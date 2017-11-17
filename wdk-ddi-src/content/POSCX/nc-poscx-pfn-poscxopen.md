---
UID: NC.poscx.PFN_POSCXOPEN
title: *PFN_POSCXOPEN
author: windows-driver-content
description: 
ms.assetid: 959a2882-3460-49db-827a-b8308956f5d2
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

# *PFN_POSCXOPEN callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

*PFN_POSCXOPEN *PfnPoscxopen; 

// Definition

NTSTATUS *PfnPoscxopen 
(
	PPOSCX_DRIVER_GLOBALS DriverGlobals
	WDFDEVICE device
	WDFFILEOBJECT fileObject
	ULONG deviceInterfaceTag
)
{...}

*PFN_POSCXOPEN 


```

## -parameters

### -param DriverGlobals: 
### -param device: 
### -param fileObject: 
### -param deviceInterfaceTag: 



## -returns

Returns NTSTATUS that ...
Return STATUS_SUCCESS if the operation succeeds. Otherwise, return an appropriate NTSTATUS Values error code. For more information, see [XREF-LINK:NTSTATUS Values].

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also