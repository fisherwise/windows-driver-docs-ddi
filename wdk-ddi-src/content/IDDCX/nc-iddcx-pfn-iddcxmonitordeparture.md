---
UID: NC.iddcx.PFN_IDDCXMONITORDEPARTURE
title: *PFN_IDDCXMONITORDEPARTURE
author: windows-driver-content
description: 
ms.assetid: cb8bd220-c2c2-496b-96ed-5b9fb232d545
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: iddcx.h
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

# *PFN_IDDCXMONITORDEPARTURE callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

*PFN_IDDCXMONITORDEPARTURE *PfnIddcxmonitordeparture; 

// Definition

NTSTATUS *PfnIddcxmonitordeparture 
(
	PIDD_DRIVER_GLOBALS DriverGlobals
	IDDCX_MONITOR MonitorObject
)
{...}

*PFN_IDDCXMONITORDEPARTURE 


```

## -parameters

### -param DriverGlobals: 
### -param MonitorObject: 



## -returns

Returns NTSTATUS that ...
Return STATUS_SUCCESS if the operation succeeds. Otherwise, return an appropriate NTSTATUS Values error code. For more information, see [XREF-LINK:NTSTATUS Values].

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also