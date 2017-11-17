---
UID: NC.usbcamdi.PCAM_NEW_FRAME_ROUTINE
title: PCAM_NEW_FRAME_ROUTINE
author: windows-driver-content
description: 
ms.assetid: 9d6a38e6-1b2f-4bdd-969a-a4a4b4fe5236
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: usbcamdi.h
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

# PCAM_NEW_FRAME_ROUTINE callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PCAM_NEW_FRAME_ROUTINE PcamNewFrameRoutine; 

// Definition

VOID PcamNewFrameRoutine 
(
	PVOID DeviceContext
	PVOID FrameContext
)
{...}

PCAM_NEW_FRAME_ROUTINE 


```

## -parameters

### -param DeviceContext: 
### -param FrameContext: 



## -returns

Returns VOID that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also