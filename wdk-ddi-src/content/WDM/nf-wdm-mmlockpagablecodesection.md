---
UID: NF.wdm.MmLockPagableCodeSection
title: MmLockPagableCodeSection
author: windows-driver-content
description: The MmLockPagableCodeSection routine locks a section of driver code, containing a set of driver routines marked with a special compiler directive, into system space.
old-location: kernel\mmlockpagablecodesection.htm
ms.assetid: dd2764d0-5775-4a89-8cdd-ba6806fb867d
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Desktop
req.target-min-winverclnt: Available starting with Windows 2000.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: MmLockPagableCodeSection
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: <=APC_LEVEL
ms.keywords: MmLockPagableCodeSection
req.iface: 
req.product: Windows 10 or later.
---

# MmLockPagableCodeSection function



## -description
<p>The <b>MmLockPagableCodeSection </b>routine locks a section of driver code, containing a set of driver routines marked with a special compiler directive, into system space.</p>


## -syntax

````
PVOID MmLockPagableCodeSection(
  _In_ PVOID AddressWithinSection
);
````


## -parameters
<dl>

### -param <i>AddressWithinSection</i> [in]

<dd>
<p>Specifies a symbolic address. This address is typically the name of a driver function within a section of driver code that has been marked with something like <b>#pragma alloc_text (PAGExxxx, driverfunction)</b>. All functions in the <b>PAGExxxx</b> section are then guaranteed to be locked down when this function returns. </p>
</dd>
</dl>

## -returns
<p><b>MmLockPagableCodeSection</b> returns an opaque value that the operating system uses to identify this section of the driver code. This opaque value can be passed subsequently to <a href="https://msdn.microsoft.com/library/windows/hardware/ff554610">MmLockPagableSectionByHandle</a> (if the driver unlocks and then later relocks the section) or to <a href="https://msdn.microsoft.com/library/windows/hardware/ff556377">MmUnlockPagableImageSection</a>.</p>

## -remarks
<p>The <b>MmLockPagableCodeSection</b> routine and <b>MmUnlockPagableImageSection</b> (the routine that performs the opposite action) support drivers that can do the following:</p>

<p>Defer loading a subset of driver routines into resident memory until incoming I/O requests for the driver's devices make it necessary for these routines to process IRPs.</p>

<p>Make the same subset of driver routines available for paging out when they have completed the processing of I/O requests and no additional requests for the driver's devices are currently expected. </p>

<p><b>MmLockPagableCodeSection</b>, <b>MmLockPagableSectionByHandle</b> and <b>MmUnlockPagableImageSection</b> are intended for use by device and intermediate drivers that have the following characteristics:</p>

<p>The driver has code paths that might not be needed while the system is running, but, if they are needed, the driver's code must be resident because it runs in an arbitrary thread context or at IRQL &gt;= DISPATCH_LEVEL.</p>

<p>The driver can determine exactly when the pageable routines should be loaded and when they can be paged out again. </p>

<p>For example, the system-supplied fault-tolerant disk driver supports the creation of mirror sets, stripe sets, and volume sets. Yet, a particular machine can be configured only with a mirror set, only with a stripe set, only with a volume set, or with any combination of these three possible options. In these circumstances, the system ftdisk driver reduces the size of its loaded image by marking routines that explicitly support mirror, stripe, and volume sets as belonging to pageable code sections. During driver initialization, pageable code sections are made resident only if the user has configured the disks to have mirror, stripe, or volume sets. If the user repartitions the disks dynamically, the ftdisk driver locks down any additional pageable code sections necessary to support any mirror, stripe, or volume sets that the user requests.</p>

<p>As other examples, the system-supplied serial and parallel drivers have <i>DispatchCreate</i> and <i>DispatchClose</i> routines that are called when a particular port is opened for exclusive I/O and when the handle for an opened port is released, respectively. Yet, serial and parallel I/O requests are sporadic, determined by which applications the end user is currently running and which application options the end user is currently exercising. In these circumstances, the system serial and parallel drivers reduce the sizes of their loaded images by marking many routines as belonging to a pageable code section that the <i>DispatchCreate</i> routine makes resident only when the first port is opened for I/O. </p>

<p>Note that each of the preceding system drivers satisfies both criteria for having pageable sections: the driver has code paths that might not be needed while the system is running, and the driver can determine exactly when its pageable section should be loaded and can be paged out again.</p>

<p>Because it is an expensive operation to lock down a section, if a driver locks down a pageable code section in more than one place, use <b>MmLockPagableCodeSection</b> for the first request. Make subsequent lock requests by calling <b>MmLockPagableSectionByHandle</b> passing the handle returned by <b>MmLockPagableCodeSection</b>. Locking by handle significantly improves driver performance because the memory manager uses the opaque return value to quickly locate the relevant section rather than searching a loaded module list. A locked down section is unlocked by calling <b>MmUnlockPagableImageSection</b>.</p>

<p>Each driver routine within a pageable code section must be marked with the following compiler directive:</p>

<p>where <i>xxxx</i> is an optional four-character, unique identifier for the caller's pageable section and <i>DriverRoutine</i> is an entry point to be included within the pageable code section. The keyword <b>PAGE</b> and the driver-determined suffix, which can be up to four characters, are case-sensitive; that is, <b>PAGE</b> must be capitalized.</p>

<p>A single call to <b>MmLockPagableCodeSection</b> in, for example, a driver's <i>DispatchCreate</i> routine, causes the entire section, containing every driver routine marked with the same <b>PAGE</b><i>xxxx</i> identifier, to be locked in system space.</p>

<p>Certain types of driver routines cannot be made part of any driver's pageable section, including the following:</p>

<p>Never make an ISR pageable. It is possible for a device driver to receive a spurious interrupt even if its device is not in use, particularly if the interrupt vector could be shared. In general, even if a driver can explicitly disable interrupts on its device, an ISR should not be made pageable.</p>

<p>Never make a DPC routine pageable if the driver cannot control when the DPC is queued, such as any <i>DpcForIsr</i> or <i>CustomDpc</i> routine that might be queued from an ISR. In general, driver routines that run at IRQL &gt;= DISPATCH_LEVEL and that can be called in an arbitrary thread context or in response to a random external event should not be made pageable.</p>

<p>Never make the <i>DispatchRead</i> or <i>DispatchWrite</i> routine pageable in any driver that might be part of the system paging I/O path. The driver of a disk that might contain the system page file must have <i>DispatchRead</i> and <i>DispatchWrite</i> routines that are resident while the system is running, as must all drivers layered above such a disk driver.</p>

<p>Note that routines in a pageable section marked with the compiler directive <b>#pragma alloc_text(PAGExxxx, ...)</b> differ from routines marked with the compiler directive <b>#pragma alloc_text(INIT, ...)</b>. The routines in the <b>INIT</b> section are not pageable and are discarded as soon as the driver returns from its <b>DriverEntry</b> or its <i>Reinitialize</i> routine, if it has one.</p>

<p>The memory manager maintains an internal lock count on any driver's pageable section. Calls to <b>MmLockPagableCodeSection</b> increment this count and the reciprocal <b>MmUnlockPagableImageSection</b> decrements the count. A driver's pageable section is not available to be paged out unless this count is zero.</p>

<p>For more information about creating pageable code sections, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff554346">Making Drivers Pageable</a>. </p>

<p>The <b>MmLockPagableCodeSection</b> routine and <b>MmUnlockPagableImageSection</b> (the routine that performs the opposite action) support drivers that can do the following:</p>

<p>Defer loading a subset of driver routines into resident memory until incoming I/O requests for the driver's devices make it necessary for these routines to process IRPs.</p>

<p>Make the same subset of driver routines available for paging out when they have completed the processing of I/O requests and no additional requests for the driver's devices are currently expected. </p>

<p><b>MmLockPagableCodeSection</b>, <b>MmLockPagableSectionByHandle</b> and <b>MmUnlockPagableImageSection</b> are intended for use by device and intermediate drivers that have the following characteristics:</p>

<p>The driver has code paths that might not be needed while the system is running, but, if they are needed, the driver's code must be resident because it runs in an arbitrary thread context or at IRQL &gt;= DISPATCH_LEVEL.</p>

<p>The driver can determine exactly when the pageable routines should be loaded and when they can be paged out again. </p>

<p>For example, the system-supplied fault-tolerant disk driver supports the creation of mirror sets, stripe sets, and volume sets. Yet, a particular machine can be configured only with a mirror set, only with a stripe set, only with a volume set, or with any combination of these three possible options. In these circumstances, the system ftdisk driver reduces the size of its loaded image by marking routines that explicitly support mirror, stripe, and volume sets as belonging to pageable code sections. During driver initialization, pageable code sections are made resident only if the user has configured the disks to have mirror, stripe, or volume sets. If the user repartitions the disks dynamically, the ftdisk driver locks down any additional pageable code sections necessary to support any mirror, stripe, or volume sets that the user requests.</p>

<p>As other examples, the system-supplied serial and parallel drivers have <i>DispatchCreate</i> and <i>DispatchClose</i> routines that are called when a particular port is opened for exclusive I/O and when the handle for an opened port is released, respectively. Yet, serial and parallel I/O requests are sporadic, determined by which applications the end user is currently running and which application options the end user is currently exercising. In these circumstances, the system serial and parallel drivers reduce the sizes of their loaded images by marking many routines as belonging to a pageable code section that the <i>DispatchCreate</i> routine makes resident only when the first port is opened for I/O. </p>

<p>Note that each of the preceding system drivers satisfies both criteria for having pageable sections: the driver has code paths that might not be needed while the system is running, and the driver can determine exactly when its pageable section should be loaded and can be paged out again.</p>

<p>Because it is an expensive operation to lock down a section, if a driver locks down a pageable code section in more than one place, use <b>MmLockPagableCodeSection</b> for the first request. Make subsequent lock requests by calling <b>MmLockPagableSectionByHandle</b> passing the handle returned by <b>MmLockPagableCodeSection</b>. Locking by handle significantly improves driver performance because the memory manager uses the opaque return value to quickly locate the relevant section rather than searching a loaded module list. A locked down section is unlocked by calling <b>MmUnlockPagableImageSection</b>.</p>

<p>Each driver routine within a pageable code section must be marked with the following compiler directive:</p>

<p>where <i>xxxx</i> is an optional four-character, unique identifier for the caller's pageable section and <i>DriverRoutine</i> is an entry point to be included within the pageable code section. The keyword <b>PAGE</b> and the driver-determined suffix, which can be up to four characters, are case-sensitive; that is, <b>PAGE</b> must be capitalized.</p>

<p>A single call to <b>MmLockPagableCodeSection</b> in, for example, a driver's <i>DispatchCreate</i> routine, causes the entire section, containing every driver routine marked with the same <b>PAGE</b><i>xxxx</i> identifier, to be locked in system space.</p>

<p>Certain types of driver routines cannot be made part of any driver's pageable section, including the following:</p>

<p>Never make an ISR pageable. It is possible for a device driver to receive a spurious interrupt even if its device is not in use, particularly if the interrupt vector could be shared. In general, even if a driver can explicitly disable interrupts on its device, an ISR should not be made pageable.</p>

<p>Never make a DPC routine pageable if the driver cannot control when the DPC is queued, such as any <i>DpcForIsr</i> or <i>CustomDpc</i> routine that might be queued from an ISR. In general, driver routines that run at IRQL &gt;= DISPATCH_LEVEL and that can be called in an arbitrary thread context or in response to a random external event should not be made pageable.</p>

<p>Never make the <i>DispatchRead</i> or <i>DispatchWrite</i> routine pageable in any driver that might be part of the system paging I/O path. The driver of a disk that might contain the system page file must have <i>DispatchRead</i> and <i>DispatchWrite</i> routines that are resident while the system is running, as must all drivers layered above such a disk driver.</p>

<p>Note that routines in a pageable section marked with the compiler directive <b>#pragma alloc_text(PAGExxxx, ...)</b> differ from routines marked with the compiler directive <b>#pragma alloc_text(INIT, ...)</b>. The routines in the <b>INIT</b> section are not pageable and are discarded as soon as the driver returns from its <b>DriverEntry</b> or its <i>Reinitialize</i> routine, if it has one.</p>

<p>The memory manager maintains an internal lock count on any driver's pageable section. Calls to <b>MmLockPagableCodeSection</b> increment this count and the reciprocal <b>MmUnlockPagableImageSection</b> decrements the count. A driver's pageable section is not available to be paged out unless this count is zero.</p>

<p>For more information about creating pageable code sections, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff554346">Making Drivers Pageable</a>. </p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt>Desktop</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Available starting with Windows 2000.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdm.h (include Wdm.h, Ntddk.h, or Ntifs.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>NtosKrnl.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>NtosKrnl.exe</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&lt;=APC_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff556377">MmUnlockPagableImageSection</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554650">MmPageEntireDriver</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554680">MmResetDriverPaging</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554607">MmLockPagableDataSection</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554610">MmLockPagableSectionByHandle</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20MmLockPagableCodeSection routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>