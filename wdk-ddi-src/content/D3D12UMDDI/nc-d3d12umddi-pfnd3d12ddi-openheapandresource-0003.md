---
UID: NC.d3d12umddi.PFND3D12DDI_OPENHEAPANDRESOURCE_0003
title: PFND3D12DDI_OPENHEAPANDRESOURCE_0003
author: windows-driver-content
description: 
ms.assetid: 7893292b-4489-4ae1-8860-79ee28b146d1
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: d3d12umddi.h
req.include-header:
req.target-type:
req.target-min-winverclnt:
req.target-min-winversvr:
req.kmdf-ver:
req.umdf-ver:
req.lib:
req.dll:
req.irql: 
req.ddi-compliance:
req.alt-api:
req.alt-loc:
req.unicode-ansi:
req.idl:
req.max-support:
req.namespace:
req.assembly:
req.type-library:
---

# PFND3D12DDI_OPENHEAPANDRESOURCE_0003 callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PFND3D12DDI_OPENHEAPANDRESOURCE_0003 Pfnd3d12ddiOpenheapandresource0003; 

// Definition

HRESULT Pfnd3d12ddiOpenheapandresource0003 
(
	 D3D12DDI_HDEVICE
	CONST D3D12DDIARG_OPENHEAP_0003 *
	 D3D12DDI_HHEAP
	 D3D12DDI_HRTRESOURCE
	 D3D12DDI_HRESOURCE
)
{...}

PFND3D12DDI_OPENHEAPANDRESOURCE_0003 


```

## -parameters

### -param D3D12DDI_HDEVICE: 
### -param *: 
### -param D3D12DDI_HHEAP: 
### -param D3D12DDI_HRTRESOURCE: 
### -param D3D12DDI_HRESOURCE: 



## -returns

Returns HRESULT that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also