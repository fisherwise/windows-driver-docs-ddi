---
UID: NF.ntintsafe.RtlLongPtrSub
title: RtlLongPtrSub
author: windows-driver-content
description: Subtracts one value of type LONG_PTR from another.
old-location: kernel\rtllongptrsub.htm
ms.assetid: 3F95CA04-3CE1-4298-B3B6-5D111AB4F3D3
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
req.alt-api: RtlLongPtrSub
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
ms.keywords: RtlLongPtrSub
req.iface: 
---

# RtlLongPtrSub function



## -description
<p>Subtracts one value of type <b>LONG_PTR</b> from another.</p>


## -syntax

````
NTSTATUS RtlLongPtrSub(
  _In_  LONG_PTR lMinuend,
  _In_  LONG_PTR lSubtrahend,
  _Out_ LONG_PTR *plResult
);
````


## -parameters
<dl>

### -param <i>lMinuend</i> [in]

<dd>
<p>The value from which <i>lSubtrahend</i> is subtracted.</p>
</dd>

### -param <i>lSubtrahend</i> [in]

<dd>
<p>The value to subtract from <i>lMinuend</i>.</p>
</dd>

### -param <i>plResult</i> [out]

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