---
UID: NS.d3d12umddi.D3D12DDIARG_CREATE_PROTECTED_RESOURCE_SESSION_0030
title: D3D12DDIARG_CREATE_PROTECTED_RESOURCE_SESSION_0030
author: windows-driver-content
description: Creates a protected resource session.
old-location: display\d3d12ddiarg-create-protected-resource-session-0030.htm
ms.assetid: 0b28ea12-1182-4be6-83f3-850172cc6a89
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
req.alt-api: D3D12DDIARG_CREATE_PROTECTED_RESOURCE_SESSION_0030
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
ms.keywords: D3D12DDIARG_CREATE_PROTECTED_RESOURCE_SESSION_0030, D3D12DDIARG_CREATE_PROTECTED_RESOURCE_SESSION_0030
req.iface: 
---

# D3D12DDIARG_CREATE_PROTECTED_RESOURCE_SESSION_0030 structure



## -description
<p>Creates a protected resource session.</p>


## -syntax

````
typedef struct _D3D12DDIARG_CREATE_PROTECTED_RESOURCE_SESSION_0030 {
  UINT  NodeMask;
} D3D12DDIARG_CREATE_PROTECTED_RESOURCE_SESSION_0030, D3D12DDIARG_CREATE_PROTECTED_RESOURCE_SESSION_0030;
````


## -struct-fields
<dl>

### -field <b>NodeMask</b>

<dd>
<p>Represents the set of nodes.</p>
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