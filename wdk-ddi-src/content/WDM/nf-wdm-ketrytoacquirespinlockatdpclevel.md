---
UID: NF.wdm.KeTryToAcquireSpinLockAtDpcLevel
title: KeTryToAcquireSpinLockAtDpcLevel
author: windows-driver-content
description: The KeTryToAcquireSpinLockAtDpcLevel routine attempts to acquire a spin lock at DISPATCH_LEVEL.
old-location: kernel\ketrytoacquirespinlockatdpclevel.htm
ms.assetid: b7791969-027e-4df7-b720-1eb612597c56
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: Available in Windows Server 2003 with Service Pack 1 (SP1) and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: KeTryToAcquireSpinLockAtDpcLevel
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: SpinLock, SpinlockRelease, HwStorPortProhibitedDDIs
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: DISPATCH_LEVEL
ms.keywords: KeTryToAcquireSpinLockAtDpcLevel
req.iface: 
req.product: Windows 10 or later.
---

# KeTryToAcquireSpinLockAtDpcLevel function



## -description
<p>The <b>KeTryToAcquireSpinLockAtDpcLevel</b> routine attempts to acquire a spin lock at DISPATCH_LEVEL.</p>


## -syntax

````
BOOLEAN KeTryToAcquireSpinLockAtDpcLevel(
  _Inout_ PKSPIN_LOCK SpinLock
);
````


## -parameters
<dl>

### -param <i>SpinLock</i> [in, out]

<dd>
<p>Specifies the spin lock to acquire. The spin lock must have already been initialized by <a href="https://msdn.microsoft.com/library/windows/hardware/ff552160">KeInitializeSpinLock</a>.</p>
</dd>
</dl>

## -returns
<p><b>KeTryToAcquireSpinLockAtDpcLevel</b> returns <b>TRUE</b> if the spin lock has been acquired, and <b>FALSE</b> if the spin lock is already being held and cannot be acquired.</p>

## -remarks
<p>If the specified spin lock is not busy, the <b>KeTryToAcquireSpinLockAtDpcLevel</b> routine acquires the spin lock (see <a href="https://msdn.microsoft.com/library/windows/hardware/ff551917">KeAcquireSpinLock</a> for details) and returns <b>TRUE</b>. If the spin lock has already been acquired, the routine immediately returns <b>FALSE</b>.</p>

<p>If the spin lock is acquired, the caller can release it by using the <a href="https://msdn.microsoft.com/library/windows/hardware/ff553145">KeReleaseSpinLock</a> routine.</p>

<p>If you want the driver to block when it is unable to acquire the spin lock, use <a href="https://msdn.microsoft.com/library/windows/hardware/ff551921">KeAcquireSpinLockAtDpcLevel</a> instead.</p>

<p>For more information about spin locks, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563830">Spin Locks</a>.</p>

<p>If the specified spin lock is not busy, the <b>KeTryToAcquireSpinLockAtDpcLevel</b> routine acquires the spin lock (see <a href="https://msdn.microsoft.com/library/windows/hardware/ff551917">KeAcquireSpinLock</a> for details) and returns <b>TRUE</b>. If the spin lock has already been acquired, the routine immediately returns <b>FALSE</b>.</p>

<p>If the spin lock is acquired, the caller can release it by using the <a href="https://msdn.microsoft.com/library/windows/hardware/ff553145">KeReleaseSpinLock</a> routine.</p>

<p>If you want the driver to block when it is unable to acquire the spin lock, use <a href="https://msdn.microsoft.com/library/windows/hardware/ff551921">KeAcquireSpinLockAtDpcLevel</a> instead.</p>

<p>For more information about spin locks, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563830">Spin Locks</a>.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt><a href="http://go.microsoft.com/fwlink/p/?linkid=531356" target="_blank">Universal</a></dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Available in Windows Server 2003 with Service Pack 1 (SP1) and later versions of Windows.</p>
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
<p>DISPATCH_LEVEL</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/dn926953">SpinLock</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh454251">SpinlockRelease</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh454220">HwStorPortProhibitedDDIs</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551917">KeAcquireSpinLock</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551921">KeAcquireSpinLockAtDpcLevel</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552160">KeInitializeSpinLock</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553145">KeReleaseSpinLock</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20KeTryToAcquireSpinLockAtDpcLevel routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>