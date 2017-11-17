---
UID: NF.wdm.RemoveTailList
title: RemoveTailList
author: windows-driver-content
description: The RemoveTailList routine removes an entry from the end of a doubly linked list of LIST_ENTRY structures.
old-location: kernel\removetaillist.htm
ms.assetid: 67942bf7-28f6-4b2d-a880-9439afaf0bb2
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
req.alt-api: RemoveTailList
req.alt-loc: Wdm.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: Any level (See Remarks section)
ms.keywords: RemoveTailList
req.iface: 
req.product: Windows 10 or later.
---

# RemoveTailList function



## -description
<p>The <b>RemoveTailList</b> routine removes an entry from the end of a doubly linked list of <a href="https://msdn.microsoft.com/library/windows/hardware/ff554296">LIST_ENTRY</a> structures.</p>


## -syntax

````
PLIST_ENTRY RemoveTailList(
  _Inout_ PLIST_ENTRY ListHead
);
````


## -parameters
<dl>

### -param <i>ListHead</i> [in, out]

<dd>
<p>Pointer to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff554296">LIST_ENTRY</a> structure that serves as the list header.</p>
</dd>
</dl>

## -returns
<p><b>RemoveTailList</b> returns a pointer to the entry that was at the tail of the list. If the list is empty, <b>RemoveTailList</b> returns <i>ListHead</i>. </p>

## -remarks
<p><b>RemoveTailList</b> removes the last entry from the list by setting <i>ListHead</i>-&gt;<b>Blink</b> to point to the second-to-last entry in the list. The routine sets the <b>Flink</b> member of the new first entry to <i>ListHead</i>. In the event the list is empty, this is effectively a no-op.</p>

<p>For information about using this routine when implementing a doubly linked list, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563802">Singly and Doubly Linked Lists</a>.</p>

<p>Callers of <b>InsertHeadList</b> can be running at any IRQL. If <b>InsertHeadList</b> is called at IRQL &gt;= DISPATCH_LEVEL, the storage for <i>ListHead</i> and the list entries must be resident.</p>

<p><b>RemoveTailList</b> removes the last entry from the list by setting <i>ListHead</i>-&gt;<b>Blink</b> to point to the second-to-last entry in the list. The routine sets the <b>Flink</b> member of the new first entry to <i>ListHead</i>. In the event the list is empty, this is effectively a no-op.</p>

<p>For information about using this routine when implementing a doubly linked list, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563802">Singly and Doubly Linked Lists</a>.</p>

<p>Callers of <b>InsertHeadList</b> can be running at any IRQL. If <b>InsertHeadList</b> is called at IRQL &gt;= DISPATCH_LEVEL, the storage for <i>ListHead</i> and the list entries must be resident.</p>

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
<p>IRQL</p>
</th>
<td width="70%">
<p>Any level (See Remarks section)</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547799">InitializeListHead</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551789">IsListEmpty</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561032">RemoveHeadList</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561029">RemoveEntryList</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20RemoveTailList routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>