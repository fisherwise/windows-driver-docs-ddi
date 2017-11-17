---
UID: NC.ndis.NDIS_WM_SEND_COMPLETE_HANDLER
title: NDIS_WM_SEND_COMPLETE_HANDLER
author: windows-driver-content
description: 
ms.assetid: e88a97f6-d8fe-41e3-b759-8d2accf62b51
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: ndis.h
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

# NDIS_WM_SEND_COMPLETE_HANDLER callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

NDIS_WM_SEND_COMPLETE_HANDLER NdisWmSendCompleteHandler; 

// Definition

VOID NdisWmSendCompleteHandler 
(
	NDIS_HANDLE MiniportAdapterHandle
	PVOID Packet
	NDIS_STATUS Status
)
{...}

NDIS_WM_SEND_COMPLETE_HANDLER 


```

## -parameters

### -param MiniportAdapterHandle: 
### -param Packet: 
### -param Status: 



## -returns

Returns VOID that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also