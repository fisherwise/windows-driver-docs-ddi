---
UID: NF.ndis.NdisCloseFile
title: NdisCloseFile
author: windows-driver-content
description: The NdisCloseFile function releases a handle returned by the NdisOpenFile function and frees the memory allocated to hold the file contents when it was opened.
old-location: netvista\ndisclosefile.htm
ms.assetid: a12f7597-cfe7-466f-a5b5-aafd885d5adf
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: netvista
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Universal
req.target-min-winverclnt: Supported for NDIS 6.0 and NDIS 5.1 drivers (see 
   NdisCloseFile (NDIS 5.1)) in Windows
   Vista. Supported for NDIS 5.1 drivers (see 
   NdisCloseFile (NDIS 5.1)) in Windows
   XP.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NdisCloseFile
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
req.irql: PASSIVE_LEVEL
ms.keywords: NdisCloseFile
req.iface: 
---

# NdisCloseFile function



## -description
<p>The 
  <b>NdisCloseFile</b> function releases a handle returned by the 
  <a href="https://msdn.microsoft.com/library/windows/hardware/ff563728">NdisOpenFile</a> function and frees the memory
  allocated to hold the file contents when it was opened.</p>


## -syntax

````
VOID NdisCloseFile(
  _In_ NDIS_HANDLE FileHandle
);
````


## -parameters
<dl>

### -param <i>FileHandle</i> [in]

<dd>
<p>The handle that was returned in a preceding call to the 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff563728">NdisOpenFile</a> function.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>For miniport drivers, calls to this function are valid only during initialization. If the 
    <a href="https://msdn.microsoft.com/b146fa81-005b-4a6c-962d-4cb023ea790e">MiniportInitializeEx</a> function
    calls the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff563728">NdisOpenFile</a> function, it must call 
    <b>NdisCloseFile</b> before it returns control.</p>

<p>For miniport drivers, calls to this function are valid only during initialization. If the 
    <a href="https://msdn.microsoft.com/b146fa81-005b-4a6c-962d-4cb023ea790e">MiniportInitializeEx</a> function
    calls the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff563728">NdisOpenFile</a> function, it must call 
    <b>NdisCloseFile</b> before it returns control.</p>

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
   <a href="https://msdn.microsoft.com/library/windows/hardware/ff550912">NdisCloseFile (NDIS 5.1)</a>) in Windows
   Vista. Supported for NDIS 5.1 drivers (see 
   <b>NdisCloseFile (NDIS 5.1)</b>) in Windows
   XP.</p>
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
<p>PASSIVE_LEVEL</p>
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

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/b146fa81-005b-4a6c-962d-4cb023ea790e">MiniportInitializeEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562785">NdisMapFile</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563728">NdisOpenFile</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564641">NdisUnmapFile</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NdisCloseFile function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>