---
UID: NE.ntddrilapitypes.RILCAPSTYPE
title: RILCAPSTYPE
author: windows-driver-content
description: This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.
old-location: netvista\rilcapstype.htm
ms.assetid: 78f372fc-75b2-47e8-ac3f-818b384c6d97
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
req.alt-api: RILCAPSTYPE
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

# RILCAPSTYPE enumeration



## -description
<p>This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.</p>


## -syntax

````
typedef enum _RILCAPSTYPE { 
  RIL_CAPSTYPE_PERSOLOCKPWDLENGTH,
  RIL_CAPSTYPE_PBMAXREAD,
  RIL_CAPSTYPE_PBSTORELOCATIONS,
  RIL_CAPSTYPE_RADIOCONFIGURATIONS,
  RIL_CAPSTYPE_SIGNALQUALITYIMPLEMENTATION,
  RIL_CAPSTYPE_NITZNOTIFICATION,
  RIL_CAPSTYPE_CALLSUPPORT,
  RIL_CAPSTYPE_SMSSUPPORT,
  RIL_CAPSTYPE_ARG_SMALLEST,
  RIL_CAPSTYPE_ARG_LARGEST,
  RIL_CAPSTYPE_MAX
} RILCAPSTYPE;
````


## -enum-fields
<dl>

### -field <a id="RIL_CAPSTYPE_PERSOLOCKPWDLENGTH"></a><a id="ril_capstype_persolockpwdlength"></a><b>RIL_CAPSTYPE_PERSOLOCKPWDLENGTH</b>

<dd></dd>

### -field <a id="RIL_CAPSTYPE_PBMAXREAD"></a><a id="ril_capstype_pbmaxread"></a><b>RIL_CAPSTYPE_PBMAXREAD</b>

<dd></dd>

### -field <a id="RIL_CAPSTYPE_PBSTORELOCATIONS"></a><a id="ril_capstype_pbstorelocations"></a><b>RIL_CAPSTYPE_PBSTORELOCATIONS</b>

<dd></dd>

### -field <a id="RIL_CAPSTYPE_RADIOCONFIGURATIONS"></a><a id="ril_capstype_radioconfigurations"></a><b>RIL_CAPSTYPE_RADIOCONFIGURATIONS</b>

<dd></dd>

### -field <a id="RIL_CAPSTYPE_SIGNALQUALITYIMPLEMENTATION"></a><a id="ril_capstype_signalqualityimplementation"></a><b>RIL_CAPSTYPE_SIGNALQUALITYIMPLEMENTATION</b>

<dd></dd>

### -field <a id="RIL_CAPSTYPE_NITZNOTIFICATION"></a><a id="ril_capstype_nitznotification"></a><b>RIL_CAPSTYPE_NITZNOTIFICATION</b>

<dd></dd>

### -field <a id="RIL_CAPSTYPE_CALLSUPPORT"></a><a id="ril_capstype_callsupport"></a><b>RIL_CAPSTYPE_CALLSUPPORT</b>

<dd></dd>

### -field <a id="RIL_CAPSTYPE_SMSSUPPORT"></a><a id="ril_capstype_smssupport"></a><b>RIL_CAPSTYPE_SMSSUPPORT</b>

<dd></dd>

### -field <a id="RIL_CAPSTYPE_ARG_SMALLEST"></a><a id="ril_capstype_arg_smallest"></a><b>RIL_CAPSTYPE_ARG_SMALLEST</b>

<dd></dd>

### -field <a id="RIL_CAPSTYPE_ARG_LARGEST"></a><a id="ril_capstype_arg_largest"></a><b>RIL_CAPSTYPE_ARG_LARGEST</b>

<dd></dd>

### -field <a id="RIL_CAPSTYPE_MAX"></a><a id="ril_capstype_max"></a><b>RIL_CAPSTYPE_MAX</b>

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