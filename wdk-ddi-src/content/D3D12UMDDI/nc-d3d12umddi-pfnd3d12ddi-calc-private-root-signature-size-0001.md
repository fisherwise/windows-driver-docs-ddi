---
UID: NC.d3d12umddi.PFND3D12DDI_CALC_PRIVATE_ROOT_SIGNATURE_SIZE_0001
title: PFND3D12DDI_CALC_PRIVATE_ROOT_SIGNATURE_SIZE_0001
author: windows-driver-content
description: 
ms.assetid: 2f7455bd-6e05-4392-a186-1fa653a507eb
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

# PFND3D12DDI_CALC_PRIVATE_ROOT_SIGNATURE_SIZE_0001 callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PFND3D12DDI_CALC_PRIVATE_ROOT_SIGNATURE_SIZE_0001 Pfnd3d12ddiCalcPrivateRootSignatureSize0001; 

// Definition

SIZE_T Pfnd3d12ddiCalcPrivateRootSignatureSize0001 
(
	 D3D12DDI_HDEVICE
	CONST D3D12DDIARG_CREATE_ROOT_SIGNATURE_0001 *
)
{...}

PFND3D12DDI_CALC_PRIVATE_ROOT_SIGNATURE_SIZE_0001 


```

## -parameters

### -param D3D12DDI_HDEVICE: 
### -param *: 



## -returns

Returns SIZE_T that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also