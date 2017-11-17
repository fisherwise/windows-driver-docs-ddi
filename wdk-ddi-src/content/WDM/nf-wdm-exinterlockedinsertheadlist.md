---
UID: NF.wdm.ExInterlockedInsertHeadList
title: ExInterlockedInsertHeadList
author: windows-driver-content
description: The ExInterlockedInsertHeadList routine atomically inserts an entry at the beginning of a doubly linked list of LIST_ENTRY structures.
old-location: kernel\exinterlockedinsertheadlist.htm
ms.assetid: 91640a96-abad-424e-b9bd-301dad2b6aac
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
req.alt-api: ExInterlockedInsertHeadList
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: IoAllocateFree, IoReuseIrp, MarkingInterlockedQueuedIrps, RemoveLockCheck, RemoveLockForward, RemoveLockForward2, RemoveLockForwardDeviceControl, RemoveLockForwardDeviceControl2, RemoveLockForwardDeviceControlInternal, RemoveLockForwardDeviceControlInternal2, RemoveLockForwardRead, RemoveLockForwardRead2, RemoveLockForwardWrite, RemoveLockForwardWrite2, RemoveLockRelease2, RemoveLockReleaseCleanup, RemoveLockReleaseClose, RemoveLockReleaseCreate, RemoveLockReleaseDeviceControl, RemoveLockReleaseInternalDeviceControl, RemoveLockReleasePower, RemoveLockReleaseRead, RemoveLockReleaseShutdown, RemoveLockReleaseSystemControl, RemoveLockReleaseWrite
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: Any level (see Remarks section)
ms.keywords: ExInterlockedInsertHeadList
req.iface: 
req.product: Windows 10 or later.
---

# ExInterlockedInsertHeadList function



## -description
<p>The <b>ExInterlockedInsertHeadList</b> routine atomically inserts an entry at the beginning of a doubly linked list of <a href="https://msdn.microsoft.com/library/windows/hardware/ff554296">LIST_ENTRY</a> structures.</p>


## -syntax

````
PLIST_ENTRY ExInterlockedInsertHeadList(
  _Inout_ PLIST_ENTRY ListHead,
  _Inout_ PLIST_ENTRY ListEntry,
  _Inout_ PKSPIN_LOCK Lock
);
````


## -parameters
<dl>

### -param <i>ListHead</i> [in, out]

<dd>
<p>A pointer to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff554296">LIST_ENTRY</a> structure that serves as the list header.</p>
</dd>

### -param <i>ListEntry</i> [in, out]

<dd>
<p>A pointer to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff554296">LIST_ENTRY</a> structure that represents the entry to be inserted into the list.</p>
</dd>

### -param <i>Lock</i> [in, out]

<dd>
<p>A pointer to a <b>KSPIN_LOCK</b> structure that serves as the spin lock used to synchronize access to the list. The storage for the spin lock must be resident and must have been initialized by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff552160">KeInitializeSpinLock</a>. You must use this spin lock only with the <b>ExInterlocked<i>Xxx</i>List</b> routines.</p>
</dd>
</dl>

## -returns
<p><b>ExInterlockedInsertHeadList</b> returns a pointer to the first entry of the list <u>before</u> the new entry was inserted. If the list was empty, the routine returns <b>NULL</b>.</p>

## -remarks
<p><b>ExInterlockedInsertHeadList</b> performs the same operation as <a href="https://msdn.microsoft.com/library/windows/hardware/ff547820">InsertHeadList</a>, but atomically. Do not mix atomic and non-atomic calls on the same list.</p>

<p>For more information about using this routine to implement a doubly linked list, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563802">Singly and Doubly Linked Lists</a>.</p>

<p>The <b>ExInterlockedInsertHeadList</b> routine can be called at any IRQL. The storage for the <i>ListHead</i> parameter and the list entries must be resident at all IRQLs.</p>

<p><b>ExInterlockedInsertHeadList</b> performs the same operation as <a href="https://msdn.microsoft.com/library/windows/hardware/ff547820">InsertHeadList</a>, but atomically. Do not mix atomic and non-atomic calls on the same list.</p>

<p>For more information about using this routine to implement a doubly linked list, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563802">Singly and Doubly Linked Lists</a>.</p>

<p>The <b>ExInterlockedInsertHeadList</b> routine can be called at any IRQL. The storage for the <i>ListHead</i> parameter and the list entries must be resident at all IRQLs.</p>

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
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/hh975154">IoAllocateFree</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff549661">IoReuseIrp</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff549015">MarkingInterlockedQueuedIrps</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975207">RemoveLockCheck</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975208">RemoveLockForward</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975209">RemoveLockForward2</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975210">RemoveLockForwardDeviceControl</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975211">RemoveLockForwardDeviceControl2</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975212">RemoveLockForwardDeviceControlInternal</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975213">RemoveLockForwardDeviceControlInternal2</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975214">RemoveLockForwardRead</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975215">RemoveLockForwardRead2</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975216">RemoveLockForwardWrite</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975217">RemoveLockForwardWrite2</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975236">RemoveLockRelease2</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975237">RemoveLockReleaseCleanup</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975238">RemoveLockReleaseClose</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975239">RemoveLockReleaseCreate</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975240">RemoveLockReleaseDeviceControl</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975241">RemoveLockReleaseInternalDeviceControl</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975243">RemoveLockReleasePower</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975244">RemoveLockReleaseRead</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975245">RemoveLockReleaseShutdown</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975246">RemoveLockReleaseSystemControl</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975247">RemoveLockReleaseWrite</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545402">ExInterlockedInsertTailList</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545427">ExInterlockedRemoveHeadList</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547799">InitializeListHead</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547820">InsertHeadList</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552160">KeInitializeSpinLock</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20ExInterlockedInsertHeadList routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>