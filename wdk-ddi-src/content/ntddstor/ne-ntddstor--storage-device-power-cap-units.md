---
UID: NE.ntddstor._STORAGE_DEVICE_POWER_CAP_UNITS
title: STORAGE_DEVICE_POWER_CAP_UNITS
author: windows-driver-content
description: The units of the maximum power threshold.
old-location: storage\storage_device_power_cap_units.htm
ms.assetid: 199900F4-90A7-4F2E-B85E-25BF3593D50B
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: Storage
req.header: ntddstor.h
req.include-header: Ntddstor.h
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: STORAGE_DEVICE_POWER_CAP_UNITS
req.alt-loc: ntddstor.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: 
ms.keywords: SERIALPERF_STATS, SERIALPERF_STATS, *PSERIALPERF_STATS
req.iface: 
---

# STORAGE_DEVICE_POWER_CAP_UNITS enumeration



## -description
<p>The units of the maximum power threshold.</p>


## -syntax

````
typedef enum _STORAGE_DEVICE_POWER_CAP_UNITS { 
  StorageDevicePowerCapUnitsPercent,
  StorageDevicePowerCapUnitsMilliwatts
} STORAGE_DEVICE_POWER_CAP_UNITS;
````


## -enum-fields
<dl>

### -field <a id="StorageDevicePowerCapUnitsPercent"></a><a id="storagedevicepowercapunitspercent"></a><a id="STORAGEDEVICEPOWERCAPUNITSPERCENT"></a><b>StorageDevicePowerCapUnitsPercent</b>

<dd>
<p>Units in percent.</p>
</dd>

### -field <a id="StorageDevicePowerCapUnitsMilliwatts"></a><a id="storagedevicepowercapunitsmilliwatts"></a><a id="STORAGEDEVICEPOWERCAPUNITSMILLIWATTS"></a><b>StorageDevicePowerCapUnitsMilliwatts</b>

<dd>
<p>Units in milliwatts.</p>
</dd>
</dl>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Client</p>
</th>
<td width="70%">
<p>Windows 10</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Server</p>
</th>
<td width="70%">
<p>Windows Server 2016</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntddstor.h (include Ntddstor.h)</dt>
</dl>
</td>
</tr>
</table>