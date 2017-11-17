---
UID: NS.d3dkmddi._DXGKARG_SETTARGETGAMMA
title: DXGKARG_SETTARGETGAMMA
author: windows-driver-content
description: Used to hold the arguments for DXGKDDI_SETTARGETGAMMA.
old-location: display\dxgkarg_settargetgamma.htm
ms.assetid: 94BA40BD-3B56-44EF-BAD4-49556E68C550
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
req.alt-api: DXGKARG_SETTARGETGAMMA
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
ms.keywords: DXGKARG_SETTARGETGAMMA, DXGKARG_SETTARGETGAMMA
req.iface: 
---

# DXGKARG_SETTARGETGAMMA structure



## -description
<p>Used to hold the arguments for <a href="https://msdn.microsoft.com/658EA0AA-80FC-4A45-B2EF-DFE928917E7B">DXGKDDI_SETTARGETGAMMA</a>.</p>


## -syntax

````
typedef struct _DXGKARG_SETTARGETGAMMA {
  D3DDDI_VIDEO_PRESENT_TARGET_ID TargetId;
  D3DKMDT_GAMMA_RAMP             GammaRamp;
} DXGKARG_SETTARGETGAMMA, *PDXGKARG_SETTARGETGAMMA;
````


## -struct-fields
<dl>

### -field <b>TargetId</b>

<dd>
<p>The identifier of a display adapter's video present target.</p>
</dd>

### -field <b>GammaRamp</b>

<dd>
<p>A <a href="https://msdn.microsoft.com/library/windows/hardware/ff546014">D3DKMDT_GAMMA_RAMP</a> struct which describes the type of gamma ramp to set and the buffer containing the ramp data.</p>
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