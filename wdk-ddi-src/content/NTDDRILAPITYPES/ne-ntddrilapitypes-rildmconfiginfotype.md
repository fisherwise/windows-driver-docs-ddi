---
UID: NE.ntddrilapitypes.RILDMCONFIGINFOTYPE
title: RILDMCONFIGINFOTYPE
author: windows-driver-content
description: This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.
old-location: netvista\rildmconfiginfotype.htm
ms.assetid: c6dc14a5-59de-42dd-9e45-99f632bf6a57
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: netvista
req.header: ntddrilapitypes.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RILDMCONFIGINFOTYPE
req.alt-loc: ntddrilapitypes.h
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
ms.keywords: TUPLE_REQUEST, TUPLE_REQUEST, *PTUPLE_REQUEST
req.iface: 
---

# RILDMCONFIGINFOTYPE enumeration



## -description
<p>This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.</p>


## -syntax

````
typedef enum _RILDMCONFIGINFOTYPE { 
  RIL_DMCV_TYPE_BOOLEAN,
  RIL_DMCV_TYPE_DWORD,
  RIL_DMCV_TYPE_STRING,
  RIL_DMCV_TYPE_MAX
} RILDMCONFIGINFOTYPE;
````


## -enum-fields
<dl>

### -field <a id="RIL_DMCV_TYPE_BOOLEAN"></a><a id="ril_dmcv_type_boolean"></a><b>RIL_DMCV_TYPE_BOOLEAN</b>

<dd></dd>

### -field <a id="RIL_DMCV_TYPE_DWORD"></a><a id="ril_dmcv_type_dword"></a><b>RIL_DMCV_TYPE_DWORD</b>

<dd></dd>

### -field <a id="RIL_DMCV_TYPE_STRING"></a><a id="ril_dmcv_type_string"></a><b>RIL_DMCV_TYPE_STRING</b>

<dd></dd>

### -field <a id="RIL_DMCV_TYPE_MAX"></a><a id="ril_dmcv_type_max"></a><b>RIL_DMCV_TYPE_MAX</b>

<dd></dd>
</dl>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntddrilapitypes.h</dt>
</dl>
</td>
</tr>
</table>