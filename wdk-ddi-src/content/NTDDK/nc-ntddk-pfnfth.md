---
UID: NC.ntddk.PFNFTH
title: PFNFTH
author: windows-driver-content
description: 
ms.assetid: 101da7c1-cfa6-4db9-833f-b9b2f7b3915c
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: ntddk.h
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

# PFNFTH callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PFNFTH Pfnfth; 

// Definition

NTSTATUS Pfnfth 
(
	PSYSTEM_FIRMWARE_TABLE_INFORMATION SystemFirmwareTableInfo
)
{...}

PFNFTH 


```

## -parameters

### -param SystemFirmwareTableInfo: 



## -returns

Returns NTSTATUS that ...
Return STATUS_SUCCESS if the operation succeeds. Otherwise, return an appropriate NTSTATUS Values error code. For more information, see [XREF-LINK:NTSTATUS Values].

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also