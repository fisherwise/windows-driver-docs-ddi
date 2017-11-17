---
UID: NC.d3d10umddi.PFND3D11_1DDI_VIDEOPROCESSORSETSTREAMFILTER
title: PFND3D11_1DDI_VIDEOPROCESSORSETSTREAMFILTER
author: windows-driver-content
description: 
ms.assetid: 685e91f4-d962-4b36-8e18-1a0ce40aa0fc
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

# PFND3D11_1DDI_VIDEOPROCESSORSETSTREAMFILTER callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PFND3D11_1DDI_VIDEOPROCESSORSETSTREAMFILTER Pfnd3d111DdiVideoprocessorsetstreamfilter; 

// Definition

VOID Pfnd3d111DdiVideoprocessorsetstreamfilter 
(
	 D3D10DDI_HDEVICE
	 D3D11_1DDI_HVIDEOPROCESSOR
	 UINT
	 D3D11_1DDI_VIDEO_PROCESSOR_FILTER
	 BOOL
	 int
)
{...}

PFND3D11_1DDI_VIDEOPROCESSORSETSTREAMFILTER 


```

## -parameters

### -param D3D10DDI_HDEVICE: 
### -param D3D11_1DDI_HVIDEOPROCESSOR: 
### -param UINT: 
### -param D3D11_1DDI_VIDEO_PROCESSOR_FILTER: 
### -param BOOL: 
### -param int: 



## -returns

Returns VOID that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also