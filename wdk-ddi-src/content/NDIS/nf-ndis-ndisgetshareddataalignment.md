---
UID: NF.ndis.NdisGetSharedDataAlignment
title: NdisGetSharedDataAlignment
author: windows-driver-content
description: NdisGetSharedDataAlignment returns the preferred alignment for memory structures that can be shared by more than one processor.
old-location: netvista\ndisgetshareddataalignment.htm
ms.assetid: 561315b4-8866-4f48-8138-12b1a38f743e
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: netvista
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Universal
req.target-min-winverclnt: Supported for NDIS 6.0 and NDIS 5.1 drivers (see 
   NdisGetSharedDataAlignment
   (NDIS 5.1)) in Windows Vista. Supported for NDIS 5.1 drivers (see 
   NdisGetSharedDataAlignment
   (NDIS 5.1)) in Windows XP.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NdisGetSharedDataAlignment
req.alt-loc: ndis.lib,ndis.dll
req.ddi-compliance: Irql_Miscellaneous_Function
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ndis.lib
req.dll: 
req.irql: <= DISPATCH_LEVEL
ms.keywords: NdisGetSharedDataAlignment
req.iface: 
---

# NdisGetSharedDataAlignment function



## -description
<p><b>NdisGetSharedDataAlignment</b> returns the preferred alignment for memory structures that can be shared
  by more than one processor.</p>


## -syntax

````
ULONG NdisGetSharedDataAlignment(void);
````


## -parameters


## -returns
<p>The boundary value, in bytes, on which drivers should align structures that can be shared by more
     than one processor.</p>

<p>The boundary value, in bytes, on which drivers should align structures that can be shared by more
     than one processor.</p>

<p>The boundary value, in bytes, on which drivers should align structures that can be shared by more
     than one processor.</p>

## -remarks
<p>Use 
    <b>NdisGetSharedDataAlignment</b> to determine the best alignment for data structures that will be shared
    between processors. Using the returned value when allocating such structures minimizes cache effects that
    reduce the performance of multiprocessor systems.</p>

<p>System support for 
    <b>NdisGetSharedDataAlignment</b> is available in Windows XP and later versions.</p>

<p>Use 
    <b>NdisGetSharedDataAlignment</b> to determine the best alignment for data structures that will be shared
    between processors. Using the returned value when allocating such structures minimizes cache effects that
    reduce the performance of multiprocessor systems.</p>

<p>System support for 
    <b>NdisGetSharedDataAlignment</b> is available in Windows XP and later versions.</p>

<p>Use 
    <b>NdisGetSharedDataAlignment</b> to determine the best alignment for data structures that will be shared
    between processors. Using the returned value when allocating such structures minimizes cache effects that
    reduce the performance of multiprocessor systems.</p>

<p>System support for 
    <b>NdisGetSharedDataAlignment</b> is available in Windows XP and later versions.</p>

<p>Use 
    <b>NdisGetSharedDataAlignment</b> to determine the best alignment for data structures that will be shared
    between processors. Using the returned value when allocating such structures minimizes cache effects that
    reduce the performance of multiprocessor systems.</p>

<p>System support for 
    <b>NdisGetSharedDataAlignment</b> is available in Windows XP and later versions.</p>

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
<p>Supported for NDIS 6.0 and NDIS 5.1 drivers (see 
   <a href="https://msdn.microsoft.com/890ef7fd-bc7b-4e9d-a25d-2e9eb3a7f9cc">NdisGetSharedDataAlignment
   (NDIS 5.1)</a>) in Windows Vista. Supported for NDIS 5.1 drivers (see 
   <b>NdisGetSharedDataAlignment
   (NDIS 5.1)</b>) in Windows XP.</p>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547982">Irql_Miscellaneous_Function</a>
</td>
</tr>
</table>