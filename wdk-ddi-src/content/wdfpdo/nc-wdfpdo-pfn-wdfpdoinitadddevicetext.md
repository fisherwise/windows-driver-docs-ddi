---
UID: NC.wdfpdo.PFN_WDFPDOINITADDDEVICETEXT
title: PFN_WDFPDOINITADDDEVICETEXT
author: windows-driver-content
description: 
ms.assetid: 1b23945e-e2ec-493e-bca6-4128d312b177
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: wdfpdo.h
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

# PFN_WDFPDOINITADDDEVICETEXT callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PFN_WDFPDOINITADDDEVICETEXT PfnWdfpdoinitadddevicetext; 

// Definition

WDFAPI PfnWdfpdoinitadddevicetext 
(
	PWDF_DRIVER_GLOBALS DriverGlobals
	PWDFDEVICE_INIT DeviceInit
	PCUNICODE_STRING DeviceDescription
	PCUNICODE_STRING DeviceLocation
	LCID LocaleId
)
{...}

PFN_WDFPDOINITADDDEVICETEXT 


```

## -parameters

### -param DriverGlobals: 
### -param DeviceInit: 
### -param DeviceDescription: 
### -param DeviceLocation: 
### -param LocaleId: 



## -returns

Returns WDFAPI that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also