---
UID: NC.sercx.PFN_SERCX2SAVERECEIVEFIFOOND0EXIT
title: PFN_SERCX2SAVERECEIVEFIFOOND0EXIT
author: windows-driver-content
description: 
ms.assetid: 0f7e6fb5-096f-44fe-a510-cc0995654a79
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: sercx.h
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

# PFN_SERCX2SAVERECEIVEFIFOOND0EXIT callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PFN_SERCX2SAVERECEIVEFIFOOND0EXIT PfnSercx2savereceivefifoond0exit; 

// Definition

WDFAPI PfnSercx2savereceivefifoond0exit 
(
	PSERCX_DRIVER_GLOBALS DriverGlobals
	SERCX2PIORECEIVE PioReceive
	ULONG FifoSize
)
{...}

PFN_SERCX2SAVERECEIVEFIFOOND0EXIT 


```

## -parameters

### -param DriverGlobals: 
### -param PioReceive: 
### -param FifoSize: 



## -returns

Returns WDFAPI that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also