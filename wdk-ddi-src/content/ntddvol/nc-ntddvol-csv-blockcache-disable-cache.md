---
UID: NC.ntddvol.CSV_BLOCKCACHE_DISABLE_CACHE
title: CSV_BLOCKCACHE_DISABLE_CACHE
author: windows-driver-content
description: 
ms.assetid: b9dc4fe6-e78a-4389-801b-c8b666a57a63
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: ntddvol.h
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

# CSV_BLOCKCACHE_DISABLE_CACHE callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

CSV_BLOCKCACHE_DISABLE_CACHE CsvBlockcacheDisableCache; 

// Definition

void CsvBlockcacheDisableCache 
(
	PVOID CallbackContext
)
{...}

CSV_BLOCKCACHE_DISABLE_CACHE 


```

## -parameters

### -param CallbackContext: 



## -returns

Returns void that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also