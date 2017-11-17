---
UID: NF.ntintsafe.RtlUIntPtrToULong
title: RtlUIntPtrToULong
author: windows-driver-content
description: Converts a value of type UINT_PTR to a value of type LONG.
old-location: kernel\rtluintptrtoulong.htm
ms.assetid: A558FB1F-3887-4BB1-9C66-AC35D1587B50
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
req.alt-api: RtlUIntPtrToULong
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
ms.keywords: RtlUIntPtrToULong
req.iface: 
---

# RtlUIntPtrToULong function



## -description
<p>Converts a value of type <b>UINT_PTR</b> to a value of type <b>LONG</b>.</p>


## -syntax

````
NTSTATUS RtlUIntPtrToULong(
  _In_  UINT_PTR uOperand,
  _Out_ LONG     *pulResult
);
````


## -parameters
<dl>

### -param <i>uOperand</i> [in]

<dd>
<p>The value to be converted.</p>
</dd>

### -param <i>pulResult</i> [out]

<dd>
<p>A pointer to the converted value. In the case where the conversion causes a truncation of the original value, the function returns STATUS_INTEGER_OVERFLOW and this parameter is not valid.</p>
</dd>
</dl>

## -remarks
<p>This is one of a set of inline functions designed to provide type conversions and perform validity checks with minimal impact on performance.</p>

<p>This function uses the following alternate name:</p>

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