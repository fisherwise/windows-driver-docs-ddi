---
UID: NS.d3d12umddi.D3D12DDIARG_OPENADAPTER
title: D3D12DDIARG_OPENADAPTER
author: windows-driver-content
description: The D3D12DDIARG_OPENADAPTER structure describes the graphics adapter object.
old-location: display\d3d12ddiarg_openadapter.htm
ms.assetid: 1FABEEBC-358C-40EB-8F5C-F834EE57A1A8
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
req.alt-api: D3D12DDIARG_OPENADAPTER
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
ms.keywords: D3D12DDIARG_OPENADAPTER, D3D12DDIARG_OPENADAPTER
req.iface: 
---

# D3D12DDIARG_OPENADAPTER structure



## -description
<p>The D3D12DDIARG_OPENADAPTER structure describes the graphics adapter object.</p>


## -syntax

````
typedef struct _D3D12DDIARG_OPENADAPTER {
  D3D12DDI_HRTADAPTER           hRTAdapter;
  D3D12DDI_HADAPTER             hAdapter;
  const D3DDDI_ADAPTERCALLBACKS *pAdapterCallbacks;
  D3D12DDI_ADAPTERFUNCS         *pAdapterFuncs;
} D3D12DDIARG_OPENADAPTER;
````


## -struct-fields
<dl>

### -field <b>hRTAdapter</b>

<dd>
<p>[in] A runtime handle to the graphics adapter object that specifies the handle that the driver should use to query for graphics adapter capabilities when the driver calls the Microsoft Direct3D runtime-supplied <a href="https://msdn.microsoft.com/8008574f-a89e-4fed-b745-7cf5baa68e64">pfnQueryAdapterInfoCb</a> callback function. </p>
</dd>

### -field <b>hAdapter</b>

<dd>
<p>[out] A handle to the graphics adapter object that specifies the handle that the Direct3D runtime uses in subsequent driver calls to identify the graphics adapter object. The driver generates a unique handle and passes it back to the Direct3D runtime. </p>
</dd>

### -field <b>pAdapterCallbacks</b>

<dd>
<p>[in] A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff544350">D3DDDI_ADAPTERCALLBACKS</a> structure that contains the Direct3D runtime-supplied <b>pfnQueryAdapterInfoCb</b> callback function that the driver can use.</p>
</dd>

### -field <b>pAdapterFuncs</b>

<dd>
<p>[out] A pointer to a D3D12DDI_ADAPTERFUNCS structure that contains a table of user-mode display driver adapter-specific functions. The Direct3D runtime uses these functions to communicate with the user-mode display driver about operations that are specific to the graphics adapter.</p>
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