---
UID: NC.wdfusb.PFN_WDFUSBTARGETDEVICEFORMATREQUESTFORURB
title: PFN_WDFUSBTARGETDEVICEFORMATREQUESTFORURB
author: windows-driver-content
description: 
ms.assetid: 359dcea1-56de-4f04-88b9-9d6a204dfb85
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

# PFN_WDFUSBTARGETDEVICEFORMATREQUESTFORURB callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PFN_WDFUSBTARGETDEVICEFORMATREQUESTFORURB PfnWdfusbtargetdeviceformatrequestforurb; 

// Definition

WDFAPI PfnWdfusbtargetdeviceformatrequestforurb 
(
	PWDF_DRIVER_GLOBALS DriverGlobals
	WDFUSBDEVICE UsbDevice
	WDFREQUEST Request
	WDFMEMORY UrbMemory
	PWDFMEMORY_OFFSET UrbMemoryOffset
)
{...}

PFN_WDFUSBTARGETDEVICEFORMATREQUESTFORURB 


```

## -parameters

### -param DriverGlobals: 
### -param UsbDevice: 
### -param Request: 
### -param UrbMemory: 
### -param UrbMemoryOffset: 



## -returns

Returns WDFAPI that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also