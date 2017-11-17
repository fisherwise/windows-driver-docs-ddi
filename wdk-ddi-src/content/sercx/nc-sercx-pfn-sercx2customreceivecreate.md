---
UID: NC.sercx.PFN_SERCX2CUSTOMRECEIVECREATE
title: PFN_SERCX2CUSTOMRECEIVECREATE
author: windows-driver-content
description: 
ms.assetid: b392e2bb-6c71-4985-994c-cdd2537a7663
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

# PFN_SERCX2CUSTOMRECEIVECREATE callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PFN_SERCX2CUSTOMRECEIVECREATE PfnSercx2customreceivecreate; 

// Definition

WDFAPI PfnSercx2customreceivecreate 
(
	PSERCX_DRIVER_GLOBALS DriverGlobals
	WDFDEVICE Device
	PSERCX2_CUSTOM_RECEIVE_CONFIG CustomReceiveConfig
	PWDF_OBJECT_ATTRIBUTES Attributes
	SERCX2CUSTOMRECEIVE *CustomReceive
)
{...}

PFN_SERCX2CUSTOMRECEIVECREATE 


```

## -parameters

### -param DriverGlobals: 
### -param Device: 
### -param CustomReceiveConfig: 
### -param Attributes: 
### -param *CustomReceive: 



## -returns

Returns WDFAPI that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also