---
UID: NC.dbghelp.PSYMBOLSERVERSTOREFILEW
title: PSYMBOLSERVERSTOREFILEW
author: windows-driver-content
description: 
ms.assetid: e2b4900f-c6db-4020-ba26-482bd5582c77
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: dbghelp.h
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

# PSYMBOLSERVERSTOREFILEW callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PSYMBOLSERVERSTOREFILEW Psymbolserverstorefilew; 

// Definition

BOOL Psymbolserverstorefilew 
(
	 PCWSTR
	 PCWSTR
	 PVOID
	 DWORD
	 DWORD
	 PWSTR
	 size_t
	 DWORD
)
{...}

PSYMBOLSERVERSTOREFILEW 


```

## -parameters

### -param PCWSTR: 
### -param PCWSTR: 
### -param PVOID: 
### -param DWORD: 
### -param DWORD: 
### -param PWSTR: 
### -param size_t: 
### -param DWORD: 



## -returns

Returns BOOL that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also