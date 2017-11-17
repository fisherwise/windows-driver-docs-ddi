---
UID: NC.wdfdevice.PFN_WDFDEVICESETSPECIALFILESUPPORT
title: PFN_WDFDEVICESETSPECIALFILESUPPORT
author: windows-driver-content
description: 
ms.assetid: f2068664-96ce-4a05-a76e-8f2996941238
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: wdfdevice.h
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

# PFN_WDFDEVICESETSPECIALFILESUPPORT callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PFN_WDFDEVICESETSPECIALFILESUPPORT PfnWdfdevicesetspecialfilesupport; 

// Definition

WDFAPI PfnWdfdevicesetspecialfilesupport 
(
	PWDF_DRIVER_GLOBALS DriverGlobals
	WDFDEVICE Device
	WDF_SPECIAL_FILE_TYPE FileType
	BOOLEAN FileTypeIsSupported
)
{...}

PFN_WDFDEVICESETSPECIALFILESUPPORT 


```

## -parameters

### -param DriverGlobals: 
### -param Device: 
### -param FileType: 
### -param FileTypeIsSupported: 



## -returns

Returns WDFAPI that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also