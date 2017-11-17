---
UID: NS.d3dkmddi._DXGK_MULTIPLANE_OVERLAY_POST_COMPOSITION_WITH_SOURCE
title: DXGK_MULTIPLANE_OVERLAY_POST_COMPOSITION_WITH_SOURCE
author: windows-driver-content
description: Used in a call to the DxgkDdiCheckMultiPlaneOverlaySupport3 function to check details on hardware support for post composition transform support.
old-location: display\dxgk_multiplane_overlay_post_composition_with_source.htm
ms.assetid: F997E3DB-630D-41C8-B659-36376E05A6B7
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmddi.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DXGK_MULTIPLANE_OVERLAY_POST_COMPOSITION_WITH_SOURCE
req.alt-loc: d3dkmddi.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: DXGK_MULTIPLANE_OVERLAY_POST_COMPOSITION_WITH_SOURCE, DXGK_MULTIPLANE_OVERLAY_POST_COMPOSITION_WITH_SOURCE
req.iface: 
---

# DXGK_MULTIPLANE_OVERLAY_POST_COMPOSITION_WITH_SOURCE structure



## -description
<p>Used in a call to the <b>DxgkDdiCheckMultiPlaneOverlaySupport3 </b>function to check details on hardware support for post composition transform support.</p>


## -syntax

````
typedef struct _DXGK_MULTIPLANE_OVERLAY_POST_COMPOSITION_WITH_SOURCE {
  D3DDDI_VIDEO_PRESENT_SOURCE_ID            VidPnSourceId;
  DXGK_MULTIPLANE_OVERLAY_POST_COMPOSITION  PostComposition;
} DXGK_MULTIPLANE_OVERLAY_POST_COMPOSITION_WITH_SOURCE;
````


## -struct-fields
<dl>

### -field <b>VidPnSourceId</b>

<dd>
<p>The zero-based video present network (VidPN) source identification number of the input for which the support levels are queried.</p>
</dd>

### -field <b>PostComposition</b>

<dd>
<p>A DXGK_MULTIPLANE_OVERLAY_POST_COMPOSITION structure that specifies additional transforms that should be applied after the planes are composed.</p>
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
<dt>D3dkmddi.h</dt>
</dl>
</td>
</tr>
</table>