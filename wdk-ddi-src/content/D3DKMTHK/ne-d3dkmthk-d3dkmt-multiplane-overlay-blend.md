---
UID: NE.d3dkmthk.D3DKMT_MULTIPLANE_OVERLAY_BLEND
title: D3DKMT_MULTIPLANE_OVERLAY_BLEND
author: windows-driver-content
description: Reserved for system use. Do not use in your driver.
old-location: display\d3dkmt_multiplane_overlay_blend.htm
ms.assetid: f0d181a6-f9cc-4e21-a971-7192e245a5c7
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmthk.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows 8
req.target-min-winversvr: Windows Server 2012
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3DKMT_MULTIPLANE_OVERLAY_BLEND
req.alt-loc: D3dkmthk.h
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
ms.keywords: DXGKMDT_OPM_STANDARD_INFORMATION, DXGKMDT_OPM_STANDARD_INFORMATION
req.iface: 
---

# D3DKMT_MULTIPLANE_OVERLAY_BLEND enumeration



## -description
<p>Reserved for system use. Do not use in your driver.</p>


## -syntax

````
typedef enum D3DKMT_MULTIPLANE_OVERLAY_BLEND { 
  D3DKMT_MULTIPLANE_OVERLAY_BLEND_OPAQUE      = 0x0,
  D3DKMT_MULTIPLANE_OVERLAY_BLEND_ALPHABLEND  = 0x1
} D3DKMT_MULTIPLANE_OVERLAY_BLEND;
````


## -enum-fields
<dl>

### -field <a id="D3DKMT_MULTIPLANE_OVERLAY_BLEND_OPAQUE"></a><a id="d3dkmt_multiplane_overlay_blend_opaque"></a><b>D3DKMT_MULTIPLANE_OVERLAY_BLEND_OPAQUE</b>

<dd></dd>

### -field <a id="D3DKMT_MULTIPLANE_OVERLAY_BLEND_ALPHABLEND"></a><a id="d3dkmt_multiplane_overlay_blend_alphablend"></a><b>D3DKMT_MULTIPLANE_OVERLAY_BLEND_ALPHABLEND</b>

<dd></dd>
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
<dt>D3dkmthk.h</dt>
</dl>
</td>
</tr>
</table>