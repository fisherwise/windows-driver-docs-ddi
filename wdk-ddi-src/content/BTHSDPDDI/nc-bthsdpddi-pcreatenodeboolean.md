---
UID: NC.bthsdpddi.PCREATENODEBOOLEAN
title: PCREATENODEBOOLEAN
author: windows-driver-content
description: 
ms.assetid: cde48a4a-4efd-4e61-a79b-d0093e70d9e2
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: bthsdpddi.h
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

# PCREATENODEBOOLEAN callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PCREATENODEBOOLEAN Pcreatenodeboolean; 

// Definition

PSDP_NODE Pcreatenodeboolean 
(
	UCHAR bVal
	ULONG tag
)
{...}

PCREATENODEBOOLEAN 


```

## -parameters

### -param bVal: 
### -param tag: 



## -returns

Returns PSDP_NODE that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also