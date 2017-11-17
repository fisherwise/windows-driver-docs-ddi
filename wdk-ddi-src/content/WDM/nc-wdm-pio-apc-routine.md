---
UID: NC.wdm.PIO_APC_ROUTINE
title: PIO_APC_ROUTINE
author: windows-driver-content
description: 
ms.assetid: 9055d3f2-e53c-4da9-b29e-b06f00e36528
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: wdm.h
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

# PIO_APC_ROUTINE callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PIO_APC_ROUTINE PioApcRoutine; 

// Definition

VOID PioApcRoutine 
(
	PVOID ApcContext
	PIO_STATUS_BLOCK IoStatusBlock
	ULONG Reserved
)
{...}

PIO_APC_ROUTINE 


```

## -parameters

### -param ApcContext: 
### -param IoStatusBlock: 
### -param Reserved: 



## -returns

Returns VOID that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also