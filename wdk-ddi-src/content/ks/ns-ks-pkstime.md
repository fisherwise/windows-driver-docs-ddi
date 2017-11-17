---
UID: NS.ks.PKSTIME
title: PKSTIME
author: windows-driver-content
description: The KSTIME structure specifies a time stamp that can be used to indicate stream position.
old-location: stream\kstime.htm
ms.assetid: e026a539-7aa5-4205-970d-cf452e4471da
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: stream
req.header: ks.h
req.include-header: Ks.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: KSTIME
req.alt-loc: ks.h
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
ms.keywords: PKSTIME, KSTIME, *PKSTIME
req.iface: 
---

# PKSTIME structure



## -description
<p>The KSTIME structure specifies a time stamp that can be used to indicate stream position.</p>


## -syntax

````
typedef struct {
  LONGLONG Time;
  ULONG    Numerator;
  ULONG    Denominator;
} KSTIME, *PKSTIME;
````


## -struct-fields
<dl>

### -field <b>Time</b>

<dd>
<p>Specifies a time value. When using unscaled time, <b>Time</b> is in units of 100-nanoseconds. When using scaled time, <b>Time</b> is in units governed by the scale factor expressed in the <b>Numerator</b> and <b>Denominator</b> members. For more information about scaled and unscaled time, see <b>Remarks</b>.</p>
</dd>

### -field <b>Numerator</b>

<dd>
<p>Specifies the numerator of the scaling factor for a scaled time value. For a nonscaled value, this should be one. <b>Numerator</b> must not be zero.</p>
</dd>

### -field <b>Denominator</b>

<dd>
<p>Specifies the denominator of the scaling factor for a scaled time value. For a nonscaled value, this should be one. <b>Denominator</b> must not be zero.</p>
</dd>
</dl>

## -remarks
<p>Unscaled time stamps are in 100-nanosecond units. A data stream can use different units by specifying the numerator and denominator of a scale factor.  </p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ks.h (include Ks.h)</dt>
</dl>
</td>
</tr>
</table>