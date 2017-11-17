---
UID: NC.wdfusb.PFN_WDFUSBTARGETDEVICESELECTCONFIG
title: PFN_WDFUSBTARGETDEVICESELECTCONFIG
author: windows-driver-content
description: 
ms.assetid: 598cf349-37a1-4585-b6d8-37494571afdd
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: wdfusb.h
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

# PFN_WDFUSBTARGETDEVICESELECTCONFIG callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PFN_WDFUSBTARGETDEVICESELECTCONFIG PfnWdfusbtargetdeviceselectconfig; 

// Definition

WDFAPI PfnWdfusbtargetdeviceselectconfig 
(
	PWDF_DRIVER_GLOBALS DriverGlobals
	WDFUSBDEVICE UsbDevice
	PWDF_OBJECT_ATTRIBUTES PipeAttributes
	PWDF_USB_DEVICE_SELECT_CONFIG_PARAMS Params
)
{...}

PFN_WDFUSBTARGETDEVICESELECTCONFIG 


```

## -parameters

### -param DriverGlobals: 
### -param UsbDevice: 
### -param PipeAttributes: 
### -param Params: 



## -returns

Returns WDFAPI that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also