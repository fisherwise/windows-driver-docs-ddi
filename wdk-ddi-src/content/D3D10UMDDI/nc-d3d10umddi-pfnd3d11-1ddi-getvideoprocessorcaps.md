---
UID: NC.d3d10umddi.PFND3D11_1DDI_GETVIDEOPROCESSORCAPS
title: PFND3D11_1DDI_GETVIDEOPROCESSORCAPS
author: windows-driver-content
description: 
ms.assetid: 4ea74e04-7e45-4590-a529-c91819ab53aa
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: d3d10umddi.h
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

# PFND3D11_1DDI_GETVIDEOPROCESSORCAPS callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PFND3D11_1DDI_GETVIDEOPROCESSORCAPS Pfnd3d111DdiGetvideoprocessorcaps; 

// Definition

VOID Pfnd3d111DdiGetvideoprocessorcaps 
(
	 D3D10DDI_HDEVICE
	 D3D11_1DDI_HVIDEOPROCESSORENUM
	D3D11_1DDI_VIDEO_PROCESSOR_CAPS *
)
{...}

PFND3D11_1DDI_GETVIDEOPROCESSORCAPS 


```

## -parameters

### -param D3D10DDI_HDEVICE: 
### -param D3D11_1DDI_HVIDEOPROCESSORENUM: 
### -param *: 



## -returns

Returns VOID that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also