---
UID: NF.ntintsafe.RtlInt8Sub
title: RtlInt8Sub
author: windows-driver-content
description: Subtracts one value of type INT8 from another.
old-location: kernel\rtlint8sub.htm
ms.assetid: 3648668C-65CD-45F9-80E0-490AE2FE405E
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
req.alt-api: RtlInt8Sub
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
ms.keywords: RtlInt8Sub
req.iface: 
---

# RtlInt8Sub function



## -description
<p>Subtracts one value of type <b>INT8</b> from another.</p>


## -syntax

````
NTSTATUS RtlInt8Sub(
  _In_  INT8 i8Minuend,
  _In_  INT8 i8Subtrahend,
  _Out_ INT8 *pi8Result
);
````


## -parameters
<dl>

### -param <i>i8Minuend</i> [in]

<dd>
<p>The value from which <i>i8Subtrahend</i> is subtracted.</p>
</dd>

### -param <i>i8Subtrahend</i> [in]

<dd>
<p>The value to subtract from <i>i8Minuend</i>.</p>
</dd>

### -param <i>pi8Result</i> [out]

<dd>
<p>A pointer to the result. If the operation results in a value that overflows or underflows the capacity of the type, the function returns STATUS_INTEGER_OVERFLOW and this parameter is not valid.</p>
</dd>
</dl>

## -remarks
<p>This is one of a set of inline functions designed to provide arithmetic operations and perform validity checks with minimal impact on performance.</p>

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