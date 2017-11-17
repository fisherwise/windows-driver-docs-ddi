---
UID: NE.dxgiddi.DXGI_DDI_MULTIPLANE_OVERLAY_BLEND
title: DXGI_DDI_MULTIPLANE_OVERLAY_BLEND
author: windows-driver-content
description: Identifies a blend operation to be performed on an overlay plane.
old-location: display\dxgi_ddi_multiplane_overlay_blend.htm
ms.assetid: 00b263e7-8655-4219-8e06-e0feba659d04
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: display
req.header: dxgiddi.h
req.include-header: D3d10umddi.h
req.target-type: Windows
req.target-min-winverclnt: Windows 8.1
req.target-min-winversvr: Windows Server 2012 R2
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DXGI_DDI_MULTIPLANE_OVERLAY_BLEND
req.alt-loc: Dxgiddi.h
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
ms.keywords: DxApiGetVersion
req.iface: 
---

# DXGI_DDI_MULTIPLANE_OVERLAY_BLEND enumeration



## -description
<p>Identifies a blend operation to be performed on an overlay plane.</p>


## -syntax

````
typedef enum DXGI_DDI_MULTIPLANE_OVERLAY_BLEND { 
  DXGI_DDI_MULTIPLANE_OVERLAY_BLEND_OPAQUE      = 0x0,
  DXGI_DDI_MULTIPLANE_OVERLAY_BLEND_ALPHABLEND  = 0x1
} DXGI_DDI_MULTIPLANE_OVERLAY_BLEND;
````


## -enum-fields
<dl>

### -field <a id="DXGI_DDI_MULTIPLANE_OVERLAY_BLEND_OPAQUE"></a><a id="dxgi_ddi_multiplane_overlay_blend_opaque"></a><b>DXGI_DDI_MULTIPLANE_OVERLAY_BLEND_OPAQUE</b>

<dd>
<p>The overlay plane should ignore data in the alpha channel and make the blended plane entirely opaque.</p>
</dd>

### -field <a id="DXGI_DDI_MULTIPLANE_OVERLAY_BLEND_ALPHABLEND"></a><a id="dxgi_ddi_multiplane_overlay_blend_alphablend"></a><b>DXGI_DDI_MULTIPLANE_OVERLAY_BLEND_ALPHABLEND</b>

<dd>
<p>The overlay plane should use the pre-multiplied alpha channel in this plane to blend it with the plane beneath.</p>
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
<p>Windows 8.1</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>Windows Server 2012 R2</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Dxgiddi.h (include D3d10umddi.h)</dt>
</dl>
</td>
</tr>
</table>