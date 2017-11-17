---
UID: NS.d3d12umddi.D3D12DDIARG_CREATE_VIDEO_DECODER_0032
title: D3D12DDIARG_CREATE_VIDEO_DECODER_0032
author: windows-driver-content
description: Creates a video decoder.
old-location: display\d3d12ddiarg-create-video-decoder-0032.htm
ms.assetid: d4d42334-ae09-4900-828b-86da81b446c1
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
req.alt-api: D3D12DDIARG_CREATE_VIDEO_DECODER_0032
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
ms.keywords: D3D12DDIARG_CREATE_VIDEO_DECODER_0032, D3D12DDIARG_CREATE_VIDEO_DECODER_0032
req.iface: 
---

# D3D12DDIARG_CREATE_VIDEO_DECODER_0032 structure



## -description
<p>Creates a video decoder.</p>


## -syntax

````
typedef struct _D3D12DDIARG_CREATE_VIDEO_DECODER_0032 {
  UINT                                      NodeMask;
  D3D12DDI_VIDEO_DECODE_CONFIGURATION_0020  Configuration;
} D3D12DDIARG_CREATE_VIDEO_DECODER_0032, D3D12DDIARG_CREATE_VIDEO_DECODER_0032;
````


## -struct-fields
<dl>

### -field <b>NodeMask</b>

<dd>
<p>Represents the set of nodes.</p>
</dd>

### -field <b>Configuration</b>

<dd>
<p>The video decode configuration.</p>
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