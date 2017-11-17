---
UID: NF.wdm.ExInterlockedPopEntrySList
title: ExInterlockedPopEntrySList
author: windows-driver-content
description: The ExInterlockedPopEntrySList routine atomically removes the first entry from a sequenced singly linked list.
old-location: kernel\exinterlockedpopentryslist.htm
ms.assetid: dbea07e1-f987-45d8-91cb-bde45df0672b
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: Available starting with Windows 2000.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: ExInterlockedPopEntrySList
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
req.irql: Any level (see Remarks section)
ms.keywords: ExInterlockedPopEntrySList
req.iface: 
req.product: Windows 10 or later.
---

# ExInterlockedPopEntrySList function



## -description
<p>The <b>ExInterlockedPopEntrySList</b> routine atomically removes the first entry from a sequenced singly linked list.</p>


## -syntax

````
PSLIST_ENTRY ExInterlockedPopEntrySList(
  _Inout_ PSLIST_HEADER ListHead,
  _Inout_ PKSPIN_LOCK   Lock
);
````


## -parameters
<dl>

### -param <i>ListHead</i> [in, out]

<dd>
<p>A pointer to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff563810">SLIST_HEADER</a> structure that serves as the header for the sequenced singly linked list. <i>ListHead</i> must have been initialized by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff545321">ExInitializeSListHead</a>.</p>
</dd>

### -param <i>Lock</i> [in, out]

<dd>
<p>A pointer to a <b>KSPIN_LOCK</b> structure that serves as the spin lock used to synchronize access to the list. The storage for the spin lock must be resident and must have been initialized by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff552160">KeInitializeSpinLock</a>. You must use this spin lock only with the <b>ExInterlocked<i>Xxx</i>List</b> routines.</p>
</dd>
</dl>

## -returns
<p><b>ExInterlockedPopEntrySList</b> returns a pointer to the first <a href="https://msdn.microsoft.com/library/windows/hardware/ff563805">SLIST_ENTRY</a> structure on the list. If the list was empty, the routine returns <b>NULL</b>.</p>

## -remarks
<p>For more information about using this routine to implement a sequenced singly linked list, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563802">Singly and Doubly Linked Lists</a>. </p>

<p>On Windows 2000, drivers must use the <b>-D_WIN2K_COMPAT_SLIST_USAGE</b> switch to successfully link code that uses <b>ExInterlockedPopEntrySList</b>.</p>

<p><b>ExInterlockedPopEntrySList</b> can be called at any IRQL. The storage for the <i>ListHead</i> parameter must be resident at all IRQLs.</p>

<p>For more information about using this routine to implement a sequenced singly linked list, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563802">Singly and Doubly Linked Lists</a>. </p>

<p>On Windows 2000, drivers must use the <b>-D_WIN2K_COMPAT_SLIST_USAGE</b> switch to successfully link code that uses <b>ExInterlockedPopEntrySList</b>.</p>

<p><b>ExInterlockedPopEntrySList</b> can be called at any IRQL. The storage for the <i>ListHead</i> parameter must be resident at all IRQLs.</p>

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
<p>Any level (see Remarks section)</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545321">ExInitializeSListHead</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545422">ExInterlockedPushEntrySList</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545427">ExInterlockedRemoveHeadList</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545502">ExQueryDepthSList</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552160">KeInitializeSpinLock</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20ExInterlockedPopEntrySList routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>