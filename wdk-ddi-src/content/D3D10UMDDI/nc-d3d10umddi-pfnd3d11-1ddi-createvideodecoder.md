---
UID: NC.d3d10umddi.PFND3D11_1DDI_CREATEVIDEODECODER
title: PFND3D11_1DDI_CREATEVIDEODECODER
author: windows-driver-content
description: Creates a video decoder object.
old-location: display\createvideodecoder.htm
ms.assetid: 41254f99-1806-428c-8bf3-7e736dbeec84
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: display
req.header: d3d10umddi.h
req.include-header: D3d10umddi.h
req.target-type: Desktop
req.target-min-winverclnt: Windows 8
req.target-min-winversvr: Windows Server 2012
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: CreateVideoDecoder
req.alt-loc: D3d10umddi.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: 
ms.keywords: SETRESULT_INFO, SETRESULT_INFO, *PSETRESULT_INFO
req.iface: 
---

# PFND3D11_1DDI_CREATEVIDEODECODER callback



## -description
<p>Creates a video decoder object.</p>


## -prototype

````
PFND3D11_1DDI_CREATEVIDEODECODER CreateVideoDecoder;

HRESULT APIENTRY* CreateVideoDecoder(
  _In_       D3D10DDI_HDEVICE                 hDevice,
  _In_ const D3D11_1DDIARG_CREATEVIDEODECODER *pCreateData,
  _In_       D3D11_1DDI_HDECODE               hDecoder,
  _In_       D3D11_1DDI_HRTDECODE             hRTDecode
)
{ ... }
````


## -parameters
<dl>

### -param <i>hDevice</i> [in]

<dd>
<p>A handle to the display device (graphics context).

</p>
</dd>

### -param <i>pCreateData</i> [in]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/hh406310">D3D11_1DDIARG_CREATEVIDEODECODER</a> structure. This structure specifies the attributes of the video decoder object to be created.</p>
</dd>

### -param <i>hDecoder</i> [in]

<dd>
<p>A handle to the driver's private data for the video decoder object. For more information, see the Remarks section.</p>
</dd>

### -param <i>hRTDecode</i> [in]

<dd>
<p>A handle to the video decoder object that the driver should use when it calls back into the runtime.</p>
</dd>
</dl>

## -returns
<p><b>CreateVideoDecoder</b> returns one of the following values:</p><dl>
<dt><b>S_OK</b></dt>
</dl><p>The video decoder object was created successfully.</p><dl>
<dt><b>D3DDDIERR_DEVICEREMOVED</b></dt>
</dl><p>The graphics adapter was removed.</p><dl>
<dt><b>E_OUTOFMEMORY</b></dt>
</dl><p>
        Memory was not available to complete the operation.</p>

<p> </p>

## -remarks
<p>The Microsoft Direct3D runtime calls <i>CreateVideoDecoder</i> after it has called the driver's <a href="https://msdn.microsoft.com/library/windows/hardware/hh451610">CalcPrivateVideoDecoderSize</a> to determine the size in bytes for the private data that the driver requires for the video decoder object. The runtime allocates the memory for this private data for the driver. The driver uses this memory to store private data that is related to the video decoder object.</p>

<p>When the runtime  calls <i>CreateVideoDecoder</i>, it passes the handle to the private data memory in the <i>hDecoder</i> parameter. This handle is actually a pointer to the memory. </p>

<p>The driver must keep track of the handle to the display device that was used to create the cryptographic session. The driver should fail all subsequent calls that use this created cryptographic session, such as <a href="https://msdn.microsoft.com/library/windows/hardware/hh451697">VideoDecoderBeginFrame</a>, if the display device that is specified in those calls is different from the display device that was used to create the video decoder. 

</p>

<p>The Microsoft Direct3D runtime calls <i>CreateVideoDecoder</i> after it has called the driver's <a href="https://msdn.microsoft.com/library/windows/hardware/hh451610">CalcPrivateVideoDecoderSize</a> to determine the size in bytes for the private data that the driver requires for the video decoder object. The runtime allocates the memory for this private data for the driver. The driver uses this memory to store private data that is related to the video decoder object.</p>

<p>When the runtime  calls <i>CreateVideoDecoder</i>, it passes the handle to the private data memory in the <i>hDecoder</i> parameter. This handle is actually a pointer to the memory. </p>

<p>The driver must keep track of the handle to the display device that was used to create the cryptographic session. The driver should fail all subsequent calls that use this created cryptographic session, such as <a href="https://msdn.microsoft.com/library/windows/hardware/hh451697">VideoDecoderBeginFrame</a>, if the display device that is specified in those calls is different from the display device that was used to create the video decoder. 

</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 8</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>Windows Server 2012</p>
</td>
</tr>
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
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>D3d10umddi.h (include D3d10umddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh451610">CalcPrivateVideoDecoderSize</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/a48dcbae-3236-4523-bc14-4be694da9a7b">NegotiateCryptoSessionKeyExchange</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh406310">D3D11_1DDIARG_CREATEVIDEODECODER</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh451697">VideoDecoderBeginFrame</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20PFND3D11_1DDI_CREATEVIDEODECODER callback function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>