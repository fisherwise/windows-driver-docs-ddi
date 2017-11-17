---
UID: NS.rilapitypes.RILCALLMEDIAOFFERANSWERSET
title: RILCALLMEDIAOFFERANSWERSET
author: windows-driver-content
description: This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.
old-location: netvista\rilcallmediaofferanswerset_2.htm
ms.assetid: 272e2bf5-9d84-407d-9126-41bcb4f43d91
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: netvista
req.header: rilapitypes.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RILCALLMEDIAOFFERANSWERSET
req.alt-loc: rilapitypes.h
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
ms.keywords: RILCALLMEDIAOFFERANSWERSET, RILCALLMEDIAOFFERANSWERSET
req.iface: 
req.product: Windows 10 or later.
---

# RILCALLMEDIAOFFERANSWERSET structure



## -description
<p>This topic supports the Windows driver infrastructure and is not intended to be used directly from your code. </p>


## -syntax

````
typedef struct _RILCALLMEDIAOFFERANSWERSET {
  DWORD                                       cbSize;
  RILCALLMEDIAOFFERANSWERTYPE                 dwType;
  DWORD                                       dwNumberOfItems;
  RILCALLMEDIAOFFERANSWER [MAXNUM_CALL_MEDIA] stOfferAnswer;
} RILCALLMEDIAOFFERANSWERSET, RILCALLMEDIAOFFERANSWERSET;
````


## -struct-fields
<dl>

### -field <b>cbSize</b>

<dd></dd>

### -field <b>dwType</b>

<dd></dd>

### -field <b>dwNumberOfItems</b>

<dd></dd>

### -field <b>stOfferAnswer</b>

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
<dt>Rilapitypes.h</dt>
</dl>
</td>
</tr>
</table>