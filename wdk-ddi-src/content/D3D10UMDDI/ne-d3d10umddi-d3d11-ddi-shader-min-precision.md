---
UID: NE.d3d10umddi.D3D11_DDI_SHADER_MIN_PRECISION
title: D3D11_DDI_SHADER_MIN_PRECISION
author: windows-driver-content
description: Specifies minimum precision levels that the user-mode driver supports in shaders.
old-location: display\d3d11_ddi_shader_min_precision.htm
ms.assetid: cf77d6c7-8f42-470a-9e3a-85d95398470b
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: display
req.header: d3d10umddi.h
req.include-header: D3d10umddi.h
req.target-type: Windows
req.target-min-winverclnt: Windows 8
req.target-min-winversvr: Windows Server 2012
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3D11_DDI_SHADER_MIN_PRECISION
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

# D3D11_DDI_SHADER_MIN_PRECISION enumeration



## -description
<p>Specifies minimum precision levels that the user-mode driver supports in shaders.</p>


## -syntax

````
typedef enum D3D11_DDI_SHADER_MIN_PRECISION { 
  D3D11_DDI_SHADER_MIN_PRECISION_10_BIT  = 0x1,
  D3D11_DDI_SHADER_MIN_PRECISION_16_BIT  = 0x2
} D3D11_DDI_SHADER_MIN_PRECISION;
````


## -enum-fields
<dl>

### -field <a id="D3D11_DDI_SHADER_MIN_PRECISION_10_BIT"></a><a id="d3d11_ddi_shader_min_precision_10_bit"></a><b>D3D11_DDI_SHADER_MIN_PRECISION_10_BIT</b>

<dd>
<p>The minimum precision level is 10-bit.</p>
</dd>

### -field <a id="D3D11_DDI_SHADER_MIN_PRECISION_16_BIT"></a><a id="d3d11_ddi_shader_min_precision_16_bit"></a><b>D3D11_DDI_SHADER_MIN_PRECISION_16_BIT</b>

<dd>
<p>The minimum precision level is 16-bit.</p>
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