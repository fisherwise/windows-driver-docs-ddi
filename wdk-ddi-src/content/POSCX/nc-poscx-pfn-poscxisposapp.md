---
UID: NC.poscx.PFN_POSCXISPOSAPP
title: *PFN_POSCXISPOSAPP
author: windows-driver-content
description: 
ms.assetid: 23e7ae1d-3cbe-43a3-a03f-1c2f3a6f3de1
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: poscx.h
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

# *PFN_POSCXISPOSAPP callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

*PFN_POSCXISPOSAPP *PfnPoscxisposapp; 

// Definition

BOOLEAN *PfnPoscxisposapp 
(
	PPOSCX_DRIVER_GLOBALS DriverGlobals
	WDFDEVICE device
	WDFFILEOBJECT fileObject
)
{...}

*PFN_POSCXISPOSAPP 


```

## -parameters

### -param DriverGlobals: 
### -param device: 
### -param fileObject: 



## -returns

Returns BOOLEAN that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also