---
UID: NF.ntintsafe.RtlByteToInt8
title: RtlByteToInt8
author: windows-driver-content
description: Converts a value of type BYTE to a value of type INT8.
old-location: kernel\rtlbytetoint8.htm
ms.assetid: 865E62CA-0D73-4957-88AA-EEF5910AD916
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: ntintsafe.h
req.include-header: 
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RtlByteToInt8
req.alt-loc: Ntintsafe.h
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
ms.keywords: RtlByteToInt8
req.iface: 
---

# RtlByteToInt8 function



## -description
<p>Converts a value of type <b>BYTE</b> to a value of type <b>INT8</b>.</p>


## -syntax

````
NTSTATUS RtlByteToInt8(
  _In_  BYTE bOperand,
  _Out_ INT8 *pi8Result
);
````


## -parameters
<dl>

### -param <i>bOperand</i> [in]

<dd>
<p>The value to be converted.</p>
</dd>

### -param <i>pi8Result</i> [out]

<dd>
<p>A pointer to the converted value. In the case where the conversion causes a truncation of the original value, the function returns STATUS_INTEGER_OVERFLOW and this parameter is not valid.</p>
</dd>
</dl>

## -remarks
<p>This is one of a set of inline functions designed to provide type conversions and perform validity checks with minimal impact on performance.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt>Desktop</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntintsafe.h</dt>
</dl>
</td>
</tr>
</table>