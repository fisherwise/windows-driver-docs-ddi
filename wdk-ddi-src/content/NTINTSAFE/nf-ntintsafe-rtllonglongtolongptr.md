---
UID: NF.ntintsafe.RtlLongLongToLongPtr
title: RtlLongLongToLongPtr
author: windows-driver-content
description: Converts a value of type LONGLONG to a value of type LONG_PTR.
old-location: kernel\rtllonglongtolongptr.htm
ms.assetid: 1E7B693A-B363-4AE0-B9E3-45CC01FE9724
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
req.alt-api: RtlLongLongToLongPtr
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
ms.keywords: RtlLongLongToLongPtr
req.iface: 
---

# RtlLongLongToLongPtr function



## -description
<p>Converts a value of type <b>LONGLONG</b> to a value of type <b>LONG_PTR</b>.</p>


## -syntax

````
NTSTATUS RtlLongLongToLongPtr(
  _In_  LONGLONG llOperand,
  _Out_ LONG_PTR *plResult
);
````


## -parameters
<dl>

### -param <i>llOperand</i> [in]

<dd>
<p>The value to be converted.</p>
</dd>

### -param <i>plResult</i> [out]

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