---
UID: NC.ntagp.PAGP_FLUSH_CHIPSET_CACHES
title: PAGP_FLUSH_CHIPSET_CACHES
author: windows-driver-content
description: 
ms.assetid: d326360b-29ce-441a-a5dd-2b9a4180d69d
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: ntagp.h
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

# PAGP_FLUSH_CHIPSET_CACHES callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PAGP_FLUSH_CHIPSET_CACHES PagpFlushChipsetCaches; 

// Definition

NTSTATUS PagpFlushChipsetCaches 
(
	IN PVOID AgpContext
)
{...}

PAGP_FLUSH_CHIPSET_CACHES 


```

## -parameters

### -param AgpContext: 



## -returns

Returns NTSTATUS that ...
Return STATUS_SUCCESS if the operation succeeds. Otherwise, return an appropriate NTSTATUS Values error code. For more information, see [XREF-LINK:NTSTATUS Values].

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also