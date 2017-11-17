---
UID: NC.ucxusbdevice.EVT_UCX_USBDEVICE_UPDATE
title: EVT_UCX_USBDEVICE_UPDATE
author: windows-driver-content
description: 
ms.assetid: 85f68e68-9801-4214-a531-050ff16a7c96
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: ucxusbdevice.h
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

# EVT_UCX_USBDEVICE_UPDATE callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

EVT_UCX_USBDEVICE_UPDATE EvtUcxUsbdeviceUpdate; 

// Definition

VOID EvtUcxUsbdeviceUpdate 
(
	UCXCONTROLLER UcxController
	WDFREQUEST Request
)
{...}

EVT_UCX_USBDEVICE_UPDATE PFN_UCX_USBDEVICE_UPDATE


```

## -parameters

### -param UcxController: 
### -param Request: 



## -returns

Returns VOID that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also