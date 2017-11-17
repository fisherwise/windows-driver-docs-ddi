---
UID: NS.d3dumddi.D3DDDICAPS_SHADER_MIN_PRECISION_SUPPORT
title: D3DDDICAPS_SHADER_MIN_PRECISION_SUPPORT
author: windows-driver-content
description: Describes precision support options for shaders in the user-mode display driver.
old-location: display\d3dddicaps_shader_min_precision_support.htm
ms.assetid: c3ad65e7-8a91-464b-9a7f-e5c47ee54048
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3dumddi.h
req.include-header: D3dumddi.h
req.target-type: Windows
req.target-min-winverclnt: Windows 8
req.target-min-winversvr: Windows Server 2012
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3DDDICAPS_SHADER_MIN_PRECISION_SUPPORT
req.alt-loc: D3dumddi.h
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
ms.keywords: D3DDDICAPS_SHADER_MIN_PRECISION_SUPPORT, D3DDDICAPS_SHADER_MIN_PRECISION_SUPPORT
req.iface: 
---

# D3DDDICAPS_SHADER_MIN_PRECISION_SUPPORT structure



## -description
<p>Describes precision support options for shaders in the user-mode display driver.</p>


## -syntax

````
typedef struct D3DDDICAPS_SHADER_MIN_PRECISION_SUPPORT {
  UINT VertexShaderMinPrecision;
  UINT PixelShaderMinPrecision;
} D3DDDICAPS_SHADER_MIN_PRECISION_SUPPORT;
````


## -struct-fields
<dl>

### -field <b>VertexShaderMinPrecision</b>

<dd>
<p>A combination of values of type <a href="https://msdn.microsoft.com/library/windows/hardware/hh451152">D3DDDICAPS_SHADER_MIN_PRECISION</a> that are combined by using a bitwise OR operation. The resulting value specifies minimum precision levels that the driver supports for the vertex shader. A value of zero indicates that the driver supports only the default precision for the shader model, and not a lower precision.</p>
</dd>

### -field <b>PixelShaderMinPrecision</b>

<dd>
<p>A combination of values of type <a href="https://msdn.microsoft.com/library/windows/hardware/hh451152">D3DDDICAPS_SHADER_MIN_PRECISION</a> that are combined by using a bitwise OR operation. The resulting value specifies minimum precision levels that the driver supports for the pixel shader. A value of zero indicates that the driver supports only the default precision for the shader model, and not a lower precision.</p>
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
<dt>D3dumddi.h (include D3dumddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh451152">D3DDDICAPS_SHADER_MIN_PRECISION</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3DDDICAPS_SHADER_MIN_PRECISION_SUPPORT structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>