---
UID: NF.ntintsafe.RtlShortSub
title: RtlShortSub
author: windows-driver-content
description: Subtracts one value of type SHORT from another.
old-location: kernel\rtlshortsub.htm
ms.assetid: F94435C2-A2FC-44F4-8A21-E56CBEB8CC37
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
req.alt-api: RtlShortSub
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
ms.keywords: RtlShortSub
req.iface: 
---

# RtlShortSub function



## -description
<p>Subtracts one value of type <b>SHORT</b> from another.</p>


## -syntax

````
NTSTATUS RtlShortSub(
  _In_  SHORT sMinuend,
  _In_  SHORT sSubtrahend,
  _Out_ SHORT *psResult
);
````


## -parameters
<dl>

### -param <i>sMinuend</i> [in]

<dd>
<p>The value from which <i>sSubtrahend</i> is subtracted.</p>
</dd>

### -param <i>sSubtrahend</i> [in]

<dd>
<p>The value to subtract from <i>sMinuend</i>.</p>
</dd>

### -param <i>psResult</i> [out]

<dd>
<p>A pointer to the result. If the operation results in a value that overflows or underflows the capacity of the type, the function returns STATUS_INTEGER_OVERFLOW and this parameter is not valid.</p>
</dd>
</dl>

## -remarks
<p>This is one of a set of inline functions designed to provide arithmetic operations and perform validity checks with minimal impact on performance.</p>

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