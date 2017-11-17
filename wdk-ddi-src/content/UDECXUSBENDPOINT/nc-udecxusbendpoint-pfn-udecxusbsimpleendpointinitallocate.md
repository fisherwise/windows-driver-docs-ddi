---
UID: NC.udecxusbendpoint.PFN_UDECXUSBSIMPLEENDPOINTINITALLOCATE
title: *PFN_UDECXUSBSIMPLEENDPOINTINITALLOCATE
author: windows-driver-content
description: 
ms.assetid: aec71330-78ff-48cf-952d-000ce0ab50ba
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: udecxusbendpoint.h
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

# *PFN_UDECXUSBSIMPLEENDPOINTINITALLOCATE callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

*PFN_UDECXUSBSIMPLEENDPOINTINITALLOCATE *PfnUdecxusbsimpleendpointinitallocate; 

// Definition

PUDECXUSBENDPOINT_INIT *PfnUdecxusbsimpleendpointinitallocate 
(
	PUDECX_DRIVER_GLOBALS DriverGlobals
	UDECXUSBDEVICE UdecxUsbDevice
)
{...}

*PFN_UDECXUSBSIMPLEENDPOINTINITALLOCATE 


```

## -parameters

### -param DriverGlobals: 
### -param UdecxUsbDevice: 



## -returns

Returns PUDECXUSBENDPOINT_INIT that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also