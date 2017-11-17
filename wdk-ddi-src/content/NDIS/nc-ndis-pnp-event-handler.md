---
UID: NC.ndis.PNP_EVENT_HANDLER
title: PNP_EVENT_HANDLER
author: windows-driver-content
description: 
ms.assetid: ffc43db4-968c-4c93-a4ea-c324a14f51cf
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

# PNP_EVENT_HANDLER callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PNP_EVENT_HANDLER PnpEventHandler; 

// Definition

NDIS_STATUS PnpEventHandler 
(
	NDIS_HANDLE ProtocolBindingContext
	PNET_PNP_EVENT NetPnPEvent
)
{...}

PNP_EVENT_HANDLER 


```

## -parameters

### -param ProtocolBindingContext: 
### -param NetPnPEvent: 



## -returns

Returns NDIS_STATUS that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also