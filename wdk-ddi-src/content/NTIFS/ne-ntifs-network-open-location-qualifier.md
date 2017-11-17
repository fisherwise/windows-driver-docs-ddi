---
UID: NE.ntifs.NETWORK_OPEN_LOCATION_QUALIFIER
title: NETWORK_OPEN_LOCATION_QUALIFIER
author: windows-driver-content
description: The NETWORK_OPEN_LOCATION_QUALIFIER enumeration type contains values that identify the kind of location restriction to attach to a file.
old-location: ifsk\network_open_location_qualifier.htm
ms.assetid: 7762bf83-82cc-4eef-9699-d093a8c2b986
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: ifsk
req.header: ntifs.h
req.include-header: Ntifs.h
req.target-type: Windows
req.target-min-winverclnt: This enumeration type is available starting with Windows Vista.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NETWORK_OPEN_LOCATION_QUALIFIER
req.alt-loc: ntifs.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: VOLUME_READ_PLEX_INPUT, VOLUME_READ_PLEX_INPUT, *PVOLUME_READ_PLEX_INPUT
req.iface: 
---

# NETWORK_OPEN_LOCATION_QUALIFIER enumeration



## -description
<p>The NETWORK_OPEN_LOCATION_QUALIFIER enumeration type contains values that identify the kind of location restriction to attach to a file.</p>


## -syntax

````
typedef enum  { 
  NetworkOpenLocationAny       = 0,
  NetworkOpenLocationRemote    = 1,
  NetworkOpenLocationLoopback  = 2
} NETWORK_OPEN_LOCATION_QUALIFIER;
````


## -enum-fields
<dl>

### -field <a id="NetworkOpenLocationAny"></a><a id="networkopenlocationany"></a><a id="NETWORKOPENLOCATIONANY"></a><b>NetworkOpenLocationAny</b>

<dd>
<p>Indicates that the file has no location restrictions. That is, a caller can open the file whether it resides remotely or locally. </p>
</dd>

### -field <a id="NetworkOpenLocationRemote"></a><a id="networkopenlocationremote"></a><a id="NETWORKOPENLOCATIONREMOTE"></a><b>NetworkOpenLocationRemote</b>

<dd>
<p>Indicates that the file is restricted to only opening remotely. That is, a caller can only open the file if it resides on a different computer from the computer that the caller resides on. </p>
</dd>

### -field <a id="NetworkOpenLocationLoopback"></a><a id="networkopenlocationloopback"></a><a id="NETWORKOPENLOCATIONLOOPBACK"></a><b>NetworkOpenLocationLoopback</b>

<dd>
<p>Indicates that the file is restricted to only opening locally. That is, a caller can only open the file if it resides on the same computer as the caller. </p>
</dd>
</dl>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>This enumeration type is available starting with Windows Vista. </p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntifs.h (include Ntifs.h)</dt>
</dl>
</td>
</tr>
</table>