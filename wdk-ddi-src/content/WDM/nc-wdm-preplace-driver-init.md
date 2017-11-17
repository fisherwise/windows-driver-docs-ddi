---
UID: NC.wdm.PREPLACE_DRIVER_INIT
title: PREPLACE_DRIVER_INIT
author: windows-driver-content
description: 
ms.assetid: 6b106515-6fac-478a-8ad7-ad13593a019a
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

# PREPLACE_DRIVER_INIT callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PREPLACE_DRIVER_INIT PreplaceDriverInit; 

// Definition

NTSTATUS PreplaceDriverInit 
(
	PPNP_REPLACE_DRIVER_INTERFACE Interface
	PVOID Unused
)
{...}

PREPLACE_DRIVER_INIT 


```

## -parameters

### -param Interface: 
### -param Unused: 



## -returns

Returns NTSTATUS that ...
Return STATUS_SUCCESS if the operation succeeds. Otherwise, return an appropriate NTSTATUS Values error code. For more information, see [XREF-LINK:NTSTATUS Values].

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also