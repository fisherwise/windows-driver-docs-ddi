---
UID: NC.ucxcontroller.PFN_UCXCONTROLLERSETFAILED
title: PFN_UCXCONTROLLERSETFAILED
author: windows-driver-content
description: 
ms.assetid: 2d0e85cd-9edd-43c5-b043-cc05407e9ac3
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: ucxcontroller.h
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

# PFN_UCXCONTROLLERSETFAILED callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PFN_UCXCONTROLLERSETFAILED PfnUcxcontrollersetfailed; 

// Definition

WDFAPI PfnUcxcontrollersetfailed 
(
	PUCX_DRIVER_GLOBALS DriverGlobals
	UCXCONTROLLER Controller
)
{...}

PFN_UCXCONTROLLERSETFAILED 


```

## -parameters

### -param DriverGlobals: 
### -param Controller: 



## -returns

Returns WDFAPI that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also