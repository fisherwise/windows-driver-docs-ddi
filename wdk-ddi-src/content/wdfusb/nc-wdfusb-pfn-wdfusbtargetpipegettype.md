---
UID: NC.wdfusb.PFN_WDFUSBTARGETPIPEGETTYPE
title: PFN_WDFUSBTARGETPIPEGETTYPE
author: windows-driver-content
description: 
ms.assetid: 6e3a2aca-012f-4527-afa2-364b668ddd11
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

# PFN_WDFUSBTARGETPIPEGETTYPE callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PFN_WDFUSBTARGETPIPEGETTYPE PfnWdfusbtargetpipegettype; 

// Definition

WDFAPI PfnWdfusbtargetpipegettype 
(
	PWDF_DRIVER_GLOBALS DriverGlobals
	WDFUSBPIPE Pipe
)
{...}

PFN_WDFUSBTARGETPIPEGETTYPE 


```

## -parameters

### -param DriverGlobals: 
### -param Pipe: 



## -returns

Returns WDFAPI that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also