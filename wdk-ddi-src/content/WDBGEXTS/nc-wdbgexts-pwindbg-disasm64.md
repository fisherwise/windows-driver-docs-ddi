---
UID: NC.wdbgexts.PWINDBG_DISASM64
title: PWINDBG_DISASM64
author: windows-driver-content
description: 
ms.assetid: 8b9fc701-b502-41ad-a868-cf4bdaac63ba
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: wdbgexts.h
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

# PWINDBG_DISASM64 callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PWINDBG_DISASM64 PwindbgDisasm64; 

// Definition

ULONG PwindbgDisasm64 
(
	ULONG64 *lpOffset
	PCSTR lpBuffer
	ULONG fShowEffectiveAddress
)
{...}

PWINDBG_DISASM64 


```

## -parameters

### -param *lpOffset: 
### -param lpBuffer: 
### -param fShowEffectiveAddress: 



## -returns

Returns ULONG that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also