---
UID: NE.d3d12umddi.D3D12DDI_VIDEO_PROCESS_FILTER_0020
title: D3D12DDI_VIDEO_PROCESS_FILTER_0020
author: windows-driver-content
description: Contains video process filters.
old-location: display\d3d12ddi_video_process_filter_0020.htm
ms.assetid: A69E2A06-EA08-465C-A1E9-2D7FAB4E2F81
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: display
req.header: d3d12umddi.h
req.include-header: D3d12umddi.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3D12DDI_VIDEO_PROCESS_FILTER_0020
req.alt-loc: D3d12umddi.h
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
ms.keywords: D3DWDDM2_2DDI_SWIZZLE_PATTERN_DESC, D3DWDDM2_2DDI_SWIZZLE_PATTERN_DESC
req.iface: 
---

# D3D12DDI_VIDEO_PROCESS_FILTER_0020 enumeration



## -description
<p>Contains video process filters.</p>


## -syntax

````
typedef enum _D3D12DDI_VIDEO_PROCESS_FILTER_0020 { 
  D3D12DDI_VIDEO_PROCESS_FILTER_0020_BRIGHTNESS          = 0,
  D3D12DDI_VIDEO_PROCESS_FILTER_0020_CONTRAST            = 1,
  D3D12DDI_VIDEO_PROCESS_FILTER_0020_HUE                 = 2,
  D3D12DDI_VIDEO_PROCESS_FILTER_0020_SATURATION          = 3,
  D3D12DDI_VIDEO_PROCESS_FILTER_0020_NOISE_REDUCTION     = 4,
  D3D12DDI_VIDEO_PROCESS_FILTER_0020_EDGE_ENHANCEMENT    = 5,
  D3D12DDI_VIDEO_PROCESS_FILTER_0020_ANAMORPHIC_SCALING  = 6,
  D3D12DDI_VIDEO_PROCESS_FILTER_0020_STEREO_ADJUSTMENT   = 7
} D3D12DDI_VIDEO_PROCESS_FILTER_0020;
````


## -enum-fields
<dl>

### -field <a id="D3D12DDI_VIDEO_PROCESS_FILTER_0020_BRIGHTNESS"></a><a id="d3d12ddi_video_process_filter_0020_brightness"></a><b>D3D12DDI_VIDEO_PROCESS_FILTER_0020_BRIGHTNESS</b>

<dd>
<p>The video processor can adjust the brightness level. </p>
</dd>

### -field <a id="D3D12DDI_VIDEO_PROCESS_FILTER_0020_CONTRAST"></a><a id="d3d12ddi_video_process_filter_0020_contrast"></a><b>D3D12DDI_VIDEO_PROCESS_FILTER_0020_CONTRAST</b>

<dd>
<p>The video processor can adjust the contrast level. </p>
</dd>

### -field <a id="D3D12DDI_VIDEO_PROCESS_FILTER_0020_HUE"></a><a id="d3d12ddi_video_process_filter_0020_hue"></a><b>D3D12DDI_VIDEO_PROCESS_FILTER_0020_HUE</b>

<dd>
<p>The video processor can adjust hue. </p>
</dd>

### -field <a id="D3D12DDI_VIDEO_PROCESS_FILTER_0020_SATURATION"></a><a id="d3d12ddi_video_process_filter_0020_saturation"></a><b>D3D12DDI_VIDEO_PROCESS_FILTER_0020_SATURATION</b>

<dd>
<p>The video processor can adjust the saturation level.</p>
</dd>

### -field <a id="D3D12DDI_VIDEO_PROCESS_FILTER_0020_NOISE_REDUCTION"></a><a id="d3d12ddi_video_process_filter_0020_noise_reduction"></a><b>D3D12DDI_VIDEO_PROCESS_FILTER_0020_NOISE_REDUCTION</b>

<dd>
<p>The video processor can perform noise reduction. </p>
</dd>

### -field <a id="D3D12DDI_VIDEO_PROCESS_FILTER_0020_EDGE_ENHANCEMENT"></a><a id="d3d12ddi_video_process_filter_0020_edge_enhancement"></a><b>D3D12DDI_VIDEO_PROCESS_FILTER_0020_EDGE_ENHANCEMENT</b>

<dd>
<p>The video processor can perform edge enhancement. </p>
</dd>

### -field <a id="D3D12DDI_VIDEO_PROCESS_FILTER_0020_ANAMORPHIC_SCALING"></a><a id="d3d12ddi_video_process_filter_0020_anamorphic_scaling"></a><b>D3D12DDI_VIDEO_PROCESS_FILTER_0020_ANAMORPHIC_SCALING</b>

<dd>
<p>The video processor can perform anamorphic scaling. Anamorphic scaling can be used to stretch 4:3 content to a widescreen 16:9 aspect ratio. </p>
</dd>

### -field <a id="D3D12DDI_VIDEO_PROCESS_FILTER_0020_STEREO_ADJUSTMENT"></a><a id="d3d12ddi_video_process_filter_0020_stereo_adjustment"></a><b>D3D12DDI_VIDEO_PROCESS_FILTER_0020_STEREO_ADJUSTMENT</b>

<dd>
<p>For stereo 3D video, the video processor can adjust the offset between the left and right views, allowing the user to reduce potential eye strain.</p>
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
<dt>D3d12umddi.h (include D3d12umddi.h)</dt>
</dl>
</td>
</tr>
</table>