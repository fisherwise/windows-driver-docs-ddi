---
UID: NF.ndis.NdisAllocateNetBufferList
title: NdisAllocateNetBufferList
author: windows-driver-content
description: Call the NdisAllocateNetBufferList function to allocate and initialize a NET_BUFFER_LIST structure from a NET_BUFFER_LIST structure pool.
old-location: netvista\ndisallocatenetbufferlist.htm
ms.assetid: 9c821aac-9abd-4041-a15e-64306ada1c02
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: netvista
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Universal
req.target-min-winverclnt: Supported in NDIS 6.0 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NdisAllocateNetBufferList
req.alt-loc: ndis.lib,ndis.dll
req.ddi-compliance: Irql_NetBuffer_Function
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ndis.lib
req.dll: 
req.irql: <= DISPATCH_LEVEL
ms.keywords: NdisAllocateNetBufferList
req.iface: 
---

# NdisAllocateNetBufferList function



## -description
<p>Call the 
  <b>NdisAllocateNetBufferList</b> function to allocate and initialize a 
  <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> structure from a
  NET_BUFFER_LIST structure pool.</p>


## -syntax

````
PNET_BUFFER_LIST NdisAllocateNetBufferList(
  _In_ NDIS_HANDLE PoolHandle,
  _In_ USHORT      ContextSize,
  _In_ USHORT      ContextBackFill
);
````


## -parameters
<dl>

### -param <i>PoolHandle</i> [in]

<dd>
<p>A NET_BUFFER_LIST structure pool handle that was previously returned from a call to 
     <a href="https://msdn.microsoft.com/b117b472-0c26-41a9-b364-3d0cfbd26cc9">
     NdisAllocateNetBufferListPool</a>.</p>
</dd>

### -param <i>ContextSize</i> [in]

<dd>
<p>The amount of 
     <i>used data space</i> in the 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff568389">NET_BUFFER_LIST_CONTEXT</a> structure
     to reserve for the caller. The 
     <i>ContextSize</i> must be a multiple of the value defined by MEMORY_ALLOCATION_ALIGNMENT.</p>
</dd>

### -param <i>ContextBackFill</i> [in]

<dd>
<p>The amount of 
     <i>unused data space</i> (backfill space) that the caller requires. NDIS adds this value to the 
     <i>ContextSize</i> and allocates additional space. The 
     <i>ContextBackFill</i> must be a multiple of the value defined by MEMORY_ALLOCATION_ALIGNMENT.</p>
</dd>
</dl>

## -returns
<p><b>NdisAllocateNetBufferList</b> returns a pointer to the allocated NET_BUFFER_LIST structure. If the
     allocation was unsuccessful, this pointer is <b>NULL</b>.</p>

## -remarks
<p>You can call the 
    <b>NdisAllocateNetBufferList</b> or 
    <a href="https://msdn.microsoft.com/b872eff3-2d0a-4f01-874d-e00e09195801">
    NdisAllocateNetBufferAndNetBufferList</a> function to allocate a 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> structure from a pool.</p>

<p>If you call 
    <b>NdisAllocateNetBufferList</b> and the NET_BUFFER_LIST structure pool was allocated by calling the 
    <a href="https://msdn.microsoft.com/b117b472-0c26-41a9-b364-3d0cfbd26cc9">
    NdisAllocateNetBufferListPool</a> function with the 
    <b>fAllocateNetBuffer</b> member of the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/hh205394">NET_BUFFER_LIST_POOL_PARAMETERS</a> structure set to <b>TRUE</b>, NDIS allocates a
    NET_BUFFER_LIST, 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff568376">NET_BUFFER</a>, MDL, and data.</p>

<p>Call the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff562583">NdisFreeNetBufferList</a> function to
    free a NET_BUFFER_LIST structure.</p>

<p>You can call the 
    <b>NdisAllocateNetBufferList</b> or 
    <a href="https://msdn.microsoft.com/b872eff3-2d0a-4f01-874d-e00e09195801">
    NdisAllocateNetBufferAndNetBufferList</a> function to allocate a 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> structure from a pool.</p>

<p>If you call 
    <b>NdisAllocateNetBufferList</b> and the NET_BUFFER_LIST structure pool was allocated by calling the 
    <a href="https://msdn.microsoft.com/b117b472-0c26-41a9-b364-3d0cfbd26cc9">
    NdisAllocateNetBufferListPool</a> function with the 
    <b>fAllocateNetBuffer</b> member of the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/hh205394">NET_BUFFER_LIST_POOL_PARAMETERS</a> structure set to <b>TRUE</b>, NDIS allocates a
    NET_BUFFER_LIST, 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff568376">NET_BUFFER</a>, MDL, and data.</p>

<p>Call the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff562583">NdisFreeNetBufferList</a> function to
    free a NET_BUFFER_LIST structure.</p>

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
<p>Supported in NDIS 6.0 and later.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ndis.h (include Ndis.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Ndis.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&lt;= DISPATCH_LEVEL</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547985">Irql_NetBuffer_Function</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/b872eff3-2d0a-4f01-874d-e00e09195801">
   NdisAllocateNetBufferAndNetBufferList</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/b117b472-0c26-41a9-b364-3d0cfbd26cc9">
   NdisAllocateNetBufferListPool</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562583">NdisFreeNetBufferList</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh205394">NET_BUFFER_LIST_POOL_PARAMETERS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff568376">NET_BUFFER</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff568389">NET_BUFFER_LIST_CONTEXT</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NdisAllocateNetBufferList function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>