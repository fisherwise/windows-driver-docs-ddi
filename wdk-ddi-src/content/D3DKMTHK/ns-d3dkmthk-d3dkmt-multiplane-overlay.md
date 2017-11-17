---
UID: NS.d3dkmthk.D3DKMT_MULTIPLANE_OVERLAY
title: D3DKMT_MULTIPLANE_OVERLAY
author: windows-driver-content
description: Reserved for system use. Do not use in your driver.
old-location: display\d3dkmt_multiplane_overlay.htm
ms.assetid: 54773231-6240-4f44-9aff-706616af68b6
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmthk.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows 8
req.target-min-winversvr: Windows Server 2012
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3DKMT_MULTIPLANE_OVERLAY
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
ms.keywords: D3DKMT_MULTIPLANE_OVERLAY, D3DKMT_MULTIPLANE_OVERLAY
req.iface: 
---

# D3DKMT_MULTIPLANE_OVERLAY structure



## -description
<p>Reserved for system use. Do not use in your driver.</p>


## -syntax

````
typedef struct D3DKMT_MULTIPLANE_OVERLAY {
  UINT                                 LayerIndex;
  BOOL                                 Enabled;
  D3DKMT_HANDLE                        hAllocation;
  D3DKMT_MULTIPLANE_OVERLAY_ATTRIBUTES PlaneAttributes;
} D3DKMT_MULTIPLANE_OVERLAY;
````


## -struct-fields
<dl>

### -field <b>LayerIndex</b>

<dd></dd>

### -field <b>Enabled</b>

<dd></dd>

### -field <b>hAllocation</b>

<dd></dd>

### -field <b>PlaneAttributes</b>

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