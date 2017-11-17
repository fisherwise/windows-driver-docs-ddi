---
UID: NC.winsplp.ROUTER_NOTIFY_CALLBACK
title: ROUTER_NOTIFY_CALLBACK
author: windows-driver-content
description: TBD.
old-location: print\router_notify_callback.htm
ms.assetid: 97D8FEEA-B6D7-4AD7-A067-B503AF8F23FF
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: print
req.header: winsplp.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: ROUTER_NOTIFY_CALLBACK callback
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
req.irql: 
ms.keywords: GdiStartPageEMF
req.iface: 
req.product: Windows 10 or later.
---

# ROUTER_NOTIFY_CALLBACK callback



## -description
<p>TBD</p>


## -prototype

````
ROUTER_NOTIFY_CALLBACK ROUTER_NOTIFY_CALLBACK;

 ROUTER_NOTIFY_CALLBACK(
  _In_  DWORD                    dwCommand,
  _In_  PVOID                    pContext,
  _In_  DWORD                    dwColor,
  _In_  PPRINTER_NOTIFY_INFO     pNofityInfo,
  _In_  DWORD                    fdwFlags,
  _Out_ PDWORD                   pdwResult
)
{ ... }
````


## -parameters
<dl>

### -param <i>dwCommand</i> [in]

<dd>
<p>TBD</p>
</dd>

### -param <i>pContext</i> [in]

<dd>
<p>TBD</p>
</dd>

### -param <i>dwColor</i> [in]

<dd>
<p>TBD</p>
</dd>

### -param <i>pNofityInfo</i> [in]

<dd>
<p>TBD</p>
</dd>

### -param <i>fdwFlags</i> [in]

<dd>
<p>TBD</p>
</dd>

### -param <i>pdwResult</i> [out]

<dd>
<p>TBD</p>
</dd>
</dl>

## -returns
<p>TBD</p>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Winsplp.h</dt>
</dl>
</td>
</tr>
</table>