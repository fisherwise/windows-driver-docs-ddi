---
UID: NS.bdatypes._BDA_TS_SELECTORINFO
title: BDA_TS_SELECTORINFO
author: windows-driver-content
description: TBD.
old-location: stream\bda_ts_selectorinfo.htm
ms.assetid: 34F10EDD-C196-4022-8D03-45A005F17F5F
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: stream
req.header: bdatypes.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: BDA_TS_SELECTORINFO
req.alt-loc: 
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
ms.keywords: BDA_TS_SELECTORINFO, BDA_TS_SELECTORINFO, *PBDA_TS_SELECTORINFO
req.iface: 
---

# BDA_TS_SELECTORINFO structure



## -description
<p>TBD</p>


## -syntax

````
typedef struct _BDA_TS_SELECTORINFO {
  BYTE   bTSInfolength;
  BYTE   bReserved[2];
  GUID   guidNetworkType;
  BYTE   bTSIDCount;
  USHORT usTSID[MIN_DIMENSION];
} BDA_TS_SELECTORINFO, *PBDA_TS_SELECTORINFO;
````


## -struct-fields
<dl>

### -field <b>bTSInfolength</b>

<dd>
<p>Specifies the buffer length including the extension.</p>
</dd>

### -field <b>bReserved</b>

<dd>
<p>TBD</p>
</dd>

### -field <b>guidNetworkType</b>

<dd>
<p>Specifies the current type of tuning.</p>
</dd>

### -field <b>bTSIDCount</b>

<dd>
<p>Specifies the number of usTSID.</p>
</dd>

### -field <b>usTSID</b>

<dd>
<p>TBD</p>
</dd>
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
<dt>Bdatypes.h</dt>
</dl>
</td>
</tr>
</table>