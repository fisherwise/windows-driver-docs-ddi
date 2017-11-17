---
UID: NC.wdm.PGPE_CLEAR_STATUS
title: PGPE_CLEAR_STATUS
author: windows-driver-content
description: 
ms.assetid: 90e67507-5113-4e95-b3d6-0867fc8870eb
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

# PGPE_CLEAR_STATUS callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PGPE_CLEAR_STATUS PgpeClearStatus; 

// Definition

NTSTATUS PgpeClearStatus 
(
)
{...}

PGPE_CLEAR_STATUS 


```

## -parameters




## -returns

Returns NTSTATUS that ...
Return STATUS_SUCCESS if the operation succeeds. Otherwise, return an appropriate NTSTATUS Values error code. For more information, see [XREF-LINK:NTSTATUS Values].

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also