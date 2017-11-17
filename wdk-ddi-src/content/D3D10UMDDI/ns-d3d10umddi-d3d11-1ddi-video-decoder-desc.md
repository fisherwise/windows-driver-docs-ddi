---
UID: NS.d3d10umddi.D3D11_1DDI_VIDEO_DECODER_DESC
title: D3D11_1DDI_VIDEO_DECODER_DESC
author: windows-driver-content
description: Describes a video stream for a Microsoft Direct3D video decoder or video processor.
old-location: display\d3d11_1ddi_video_decoder_desc.htm
ms.assetid: 35fe914b-13e8-4658-9ea6-af1eb9068f6f
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3d10umddi.h
req.include-header: D3d10umddi.h
req.target-type: Windows
req.target-min-winverclnt: Windows 8
req.target-min-winversvr: Windows Server 2012
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3D11_1DDI_VIDEO_DECODER_DESC
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
ms.keywords: D3D11_1DDI_VIDEO_DECODER_DESC, D3D11_1DDI_VIDEO_DECODER_DESC
req.iface: 
---

# D3D11_1DDI_VIDEO_DECODER_DESC structure



## -description
<p>Describes a video stream for a Microsoft Direct3D video decoder or video processor.</p>


## -syntax

````
typedef struct D3D11_1DDI_VIDEO_DECODER_DESC {
  GUID        Guid;
  UINT        SampleWidth;
  UINT        SampleHeight;
  DXGI_FORMAT OutputFormat;
} D3D11_1DDI_VIDEO_DECODER_DESC;
````


## -struct-fields
<dl>

### -field <b>Guid</b>

<dd>
<p>The DXVA decoding profile. To get the list of profiles supported by the device, call the <a href="https://msdn.microsoft.com/library/windows/hardware/hh451670">GetVideoDecoderProfile</a> function.

</p>
</dd>

### -field <b>SampleWidth</b>

<dd>
<p>The width of the video frame, in pixels.</p>
</dd>

### -field <b>SampleHeight</b>

<dd>
<p>The height of the video frame, in pixels.</p>
</dd>

### -field <b>OutputFormat</b>

<dd>
<p>The output surface format, specified as a <b>DXGI_FORMAT</b> value. The <b>DXGI_FORMAT</b> enumeration is defined in Dxgiformat.h.</p>
</dd>
</dl>

## -remarks


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
<a href="https://msdn.microsoft.com/library/windows/hardware/hh451670">GetVideoDecoderProfile</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3D11_1DDI_VIDEO_DECODER_DESC structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>