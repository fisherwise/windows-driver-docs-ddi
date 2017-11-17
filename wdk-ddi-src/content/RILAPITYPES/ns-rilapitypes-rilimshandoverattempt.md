---
UID: NS.rilapitypes.RILIMSHANDOVERATTEMPT
title: RILIMSHANDOVERATTEMPT
author: windows-driver-content
description: This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.
old-location: netvista\rilimshandoverattempt_2.htm
ms.assetid: de56a241-10a3-4f9c-970c-433ab997612d
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
req.alt-api: RILIMSHANDOVERATTEMPT
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
ms.keywords: RILIMSHANDOVERATTEMPT, RILIMSHANDOVERATTEMPT
req.iface: 
req.product: Windows 10 or later.
---

# RILIMSHANDOVERATTEMPT structure



## -description
<p>This topic supports the Windows driver infrastructure and is not intended to be used directly from your code. </p>


## -syntax

````
typedef struct _RILIMSHANDOVERATTEMPT {
  DWORD             cbSize;
  RILIMSSYSTEMTYPE  dwOldSystemType;
  RILIMSSYSTEMTYPE  dwDestSystemType;
  HRESULT           hrHandOverResult;
} RILIMSHANDOVERATTEMPT, RILIMSHANDOVERATTEMPT;
````


## -struct-fields
<dl>

### -field <b>cbSize</b>

<dd></dd>

### -field <b>dwOldSystemType</b>

<dd></dd>

### -field <b>dwDestSystemType</b>

<dd></dd>

### -field <b>hrHandOverResult</b>

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