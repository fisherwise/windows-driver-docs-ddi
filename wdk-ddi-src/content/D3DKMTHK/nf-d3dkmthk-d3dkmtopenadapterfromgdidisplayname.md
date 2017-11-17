---
UID: NF.d3dkmthk.D3DKMTOpenAdapterFromGdiDisplayName
title: D3DKMTOpenAdapterFromGdiDisplayName
author: windows-driver-content
description: The D3DKMTOpenAdapterFromGdiDisplayName function maps a GDI device name to a graphics adapter handle and, if the adapter contains multiple monitor outputs, to one of those outputs.
old-location: display\d3dkmtopenadapterfromgdidisplayname.htm
ms.assetid: 56656fc2-785c-4021-9864-e4c152551973
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmthk.h
req.include-header: D3dkmthk.h
req.target-type: Universal
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3DKMTOpenAdapterFromGdiDisplayName
req.alt-loc: Gdi32.dll,API-MS-Win-DX-D3DKmt-l1-1-0.dll,API-MS-Win-DX-D3DKmt-l1-1-1.dll,API-MS-Win-DX-D3DKMT-L1-1-2.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Gdi32.lib
req.dll: Gdi32.dll
req.irql: 
ms.keywords: D3DKMTOpenAdapterFromGdiDisplayName
req.iface: 
---

# D3DKMTOpenAdapterFromGdiDisplayName function



## -description
<p>The <b>D3DKMTOpenAdapterFromGdiDisplayName</b> function maps a GDI device name to a graphics adapter handle and, if the adapter contains multiple monitor outputs, to one of those outputs.</p>


## -syntax

````
NTSTATUS D3DKMTOpenAdapterFromGdiDisplayName(
  _Inout_ D3DKMT_OPENADAPTERFROMGDIDISPLAYNAME *pData
);
````


## -parameters
<dl>

### -param <i>pData</i> [in, out]

<dd>
<p> A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff548113">D3DKMT_OPENADAPTERFROMGDIDISPLAYNAME</a> structure that describes the parameters that are required to perform the mapping.</p>
</dd>
</dl>

## -returns
<p><b>D3DKMTOpenAdapterFromGdiDisplayName</b>
       returns one of the following values:</p><dl>
<dt><b>STATUS_SUCCESS</b></dt>
</dl><p>The mapping was performed successfully.</p><dl>
<dt><b>STATUS_INVALID_PARAMETER</b></dt>
</dl><p>Parameters were validated and determined to be incorrect or the Windows Vista display driver model was not used.</p>

<p> </p>

<p>This function might also return other <a href="https://msdn.microsoft.com/library/windows/hardware/ff557697">NTSTATUS values</a>.</p>

## -remarks
<p>A graphics adapter corresponds to a video card. A monitor output corresponds to a head on a video card. A system with a single video card contains only one adapter. However, if the video card supports multiple heads, it supports outputting to multiple monitors.</p>

<p>A graphics adapter corresponds to a video card. A monitor output corresponds to a head on a video card. A system with a single video card contains only one adapter. However, if the video card supports multiple heads, it supports outputting to multiple monitors.</p>

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
<p>Available in Windows Vista and later versions of the Windows operating systems.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>D3dkmthk.h (include D3dkmthk.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Gdi32.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>Gdi32.dll</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548113">D3DKMT_OPENADAPTERFROMGDIDISPLAYNAME</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3DKMTOpenAdapterFromGdiDisplayName function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>