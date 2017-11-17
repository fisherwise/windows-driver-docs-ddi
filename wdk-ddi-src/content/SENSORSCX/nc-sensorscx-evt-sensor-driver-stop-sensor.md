---
UID: NC.sensorscx.EVT_SENSOR_DRIVER_STOP_SENSOR
title: EVT_SENSOR_DRIVER_STOP_SENSOR
author: windows-driver-content
description: 
ms.assetid: ea61dd20-ecd9-47af-ae7e-b18a946a7b29
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: sensorscx.h
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

# EVT_SENSOR_DRIVER_STOP_SENSOR callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

EVT_SENSOR_DRIVER_STOP_SENSOR EvtSensorDriverStopSensor; 

// Definition

_IRQL_requires_same_ NTSTATUS EvtSensorDriverStopSensor 
(
	SENSOROBJECT Sensor
)
{...}

EVT_SENSOR_DRIVER_STOP_SENSOR PFN_SENSOR_DRIVER_STOP_SENSOR


```

## -parameters

### -param Sensor: 



## -returns

Returns _IRQL_requires_same_ NTSTATUS that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also