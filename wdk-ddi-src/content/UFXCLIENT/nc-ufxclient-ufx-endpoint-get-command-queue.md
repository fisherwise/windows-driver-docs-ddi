---
UID: NC.ufxclient.UFX_ENDPOINT_GET_COMMAND_QUEUE
title: UFX_ENDPOINT_GET_COMMAND_QUEUE
author: windows-driver-content
description: 
ms.assetid: 7072afe2-db00-481d-9ac9-c05b4b3cdb06
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: ufxclient.h
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

# UFX_ENDPOINT_GET_COMMAND_QUEUE callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

UFX_ENDPOINT_GET_COMMAND_QUEUE UfxEndpointGetCommandQueue; 

// Definition

WDFQUEUE UfxEndpointGetCommandQueue 
(
	PUFX_GLOBALS 
	UFXENDPOINT 
)
{...}

UFX_ENDPOINT_GET_COMMAND_QUEUE PFN_UFX_ENDPOINT_GET_COMMAND_QUEUE


```

## -parameters

### -param : 
### -param : 



## -returns

Returns WDFQUEUE that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also