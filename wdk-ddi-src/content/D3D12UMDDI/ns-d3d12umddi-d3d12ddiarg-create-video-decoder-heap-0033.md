---
UID: NS.d3d12umddi.D3D12DDIARG_CREATE_VIDEO_DECODER_HEAP_0033
title: D3D12DDIARG_CREATE_VIDEO_DECODER_HEAP_0033
author: windows-driver-content
description: Create a video decoder heap.
old-location: display\d3d12ddiarg-create-video-decoder-heap-0033.htm
ms.assetid: 158411ee-6cc1-466d-b772-fe380b55baef
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3d12umddi.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3D12DDIARG_CREATE_VIDEO_DECODER_HEAP_0033
req.alt-loc: d3d12umddi.h
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
ms.keywords: D3D12DDIARG_CREATE_VIDEO_DECODER_HEAP_0033, D3D12DDIARG_CREATE_VIDEO_DECODER_HEAP_0033
req.iface: 
---

# D3D12DDIARG_CREATE_VIDEO_DECODER_HEAP_0033 structure



## -description
<p class="CCE_Message">[Some information relates to pre-released product which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.]</p>
<p>Create a video decoder heap.</p>


## -syntax

````
typedef struct _D3D12DDIARG_CREATE_VIDEO_DECODER_HEAP_0033 {
  UINT                                      NodeMask;
  D3D12DDI_VIDEO_DECODE_CONFIGURATION_0020  Configuration;
  UINT                                      DecodeWidth;
  UINT                                      DecodeHeight;
  DXGI_FORMAT                               Format;
  DXGI_RATIONAL                             FrameRate;
  UINT                                      BitRate;
  UINT                                      MaxDecodePictureBufferCount;
} D3D12DDIARG_CREATE_VIDEO_DECODER_HEAP_0033, D3D12DDIARG_CREATE_VIDEO_DECODER_HEAP_0033;
````


## -struct-fields
<dl>

### -field <b>NodeMask</b>

<dd>
<p>The set of nodes.</p>
</dd>

### -field <b>Configuration</b>

<dd>
<p>The video decode configuration.</p>
</dd>

### -field <b>DecodeWidth</b>

<dd>
<p>Decode width.</p>
</dd>

### -field <b>DecodeHeight</b>

<dd>
<p>Decode height.</p>
</dd>

### -field <b>Format</b>

<dd>
<p>The resource data format.</p>
</dd>

### -field <b>FrameRate</b>

<dd>
<p>A rational number that specifies the frame rate.</p>
</dd>

### -field <b>BitRate</b>

<dd>
<p>The number of bits per second.</p>
</dd>

### -field <b>MaxDecodePictureBufferCount</b>

<dd>
<p>Maximum decode picture buffer count.</p>
</dd>
</dl>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>D3d12umddi.h</dt>
</dl>
</td>
</tr>
</table>