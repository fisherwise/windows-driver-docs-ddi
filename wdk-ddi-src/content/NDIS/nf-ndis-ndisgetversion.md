---
UID: NF.ndis.NdisGetVersion
title: NdisGetVersion
author: windows-driver-content
description: The NdisGetVersion function returns the version number of NDIS.
old-location: netvista\ndisgetversion.htm
ms.assetid: d3e2c799-f789-499f-9948-f41d7576296e
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: netvista
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Universal
req.target-min-winverclnt: Supported for NDIS 6.0 and NDIS 5.1 drivers (see 
   NdisGetVersion (NDIS 5.1)) in
   Windows Vista. Supported for NDIS 5.1 drivers (see 
   NdisGetVersion (NDIS 5.1)) in
   Windows XP.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NdisGetVersion
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
ms.keywords: NdisGetVersion
req.iface: 
---

# NdisGetVersion function



## -description
<p>The 
  <b>NdisGetVersion</b> function returns the version number of NDIS.</p>


## -syntax

````
UINT NdisGetVersion(void);
````


## -parameters


## -returns
<p>Returns the major and minor numbers for the NDIS version in the high and low halves of the
     unsigned integer respectively.</p>

<p>Returns the major and minor numbers for the NDIS version in the high and low halves of the
     unsigned integer respectively.</p>

<p>Returns the major and minor numbers for the NDIS version in the high and low halves of the
     unsigned integer respectively.</p>

## -remarks
<p>System support for 
    <b>NdisGetVersion</b> is available in Windows XP and later versions.</p>

<p>System support for 
    <b>NdisGetVersion</b> is available in Windows XP and later versions.</p>

<p>System support for 
    <b>NdisGetVersion</b> is available in Windows XP and later versions.</p>

<p>System support for 
    <b>NdisGetVersion</b> is available in Windows XP and later versions.</p>

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
   <a href="https://msdn.microsoft.com/library/windows/hardware/ff552120">NdisGetVersion (NDIS 5.1)</a>) in
   Windows Vista. Supported for NDIS 5.1 drivers (see 
   <b>NdisGetVersion (NDIS 5.1)</b>) in
   Windows XP.</p>
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