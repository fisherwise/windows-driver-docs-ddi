---
UID: NC.d3dkmddi.DXGKDDI_DESTROYPROCESS
title: DXGKDDI_DESTROYPROCESS
author: windows-driver-content
description: 
ms.assetid: 791e023c-1bcd-495f-a11d-413797ff0923
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: d3dkmddi.h
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

# DXGKDDI_DESTROYPROCESS callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

DXGKDDI_DESTROYPROCESS DxgkddiDestroyprocess; 

// Definition

NTSTATUS DxgkddiDestroyprocess 
(
	IN_CONST_HANDLE hAdapter
	IN_CONST_HANDLE hKmdProcess
)
{...}

DXGKDDI_DESTROYPROCESS PDXGKDDI_DESTROYPROCESS


```

## -parameters

### -param hAdapter: 
### -param hKmdProcess: 



## -returns

Returns NTSTATUS that ...
Return STATUS_SUCCESS if the operation succeeds. Otherwise, return an appropriate NTSTATUS Values error code. For more information, see [XREF-LINK:NTSTATUS Values].

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also