---
UID: NC.d3dkmthk.PFND3DKMT_RELEASEPROCESSVIDPNSOURCEOWNERS
title: PFND3DKMT_RELEASEPROCESSVIDPNSOURCEOWNERS
author: windows-driver-content
description: 
ms.assetid: 77029607-4210-40b9-9a27-8abeeae2fade
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: d3dkmthk.h
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

# PFND3DKMT_RELEASEPROCESSVIDPNSOURCEOWNERS callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PFND3DKMT_RELEASEPROCESSVIDPNSOURCEOWNERS Pfnd3dkmtReleaseprocessvidpnsourceowners; 

// Definition

NTSTATUS Pfnd3dkmtReleaseprocessvidpnsourceowners 
(
	 HANDLE
)
{...}

PFND3DKMT_RELEASEPROCESSVIDPNSOURCEOWNERS 


```

## -parameters

### -param HANDLE: 



## -returns

Returns NTSTATUS that ...
Return STATUS_SUCCESS if the operation succeeds. Otherwise, return an appropriate NTSTATUS Values error code. For more information, see [XREF-LINK:NTSTATUS Values].

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also