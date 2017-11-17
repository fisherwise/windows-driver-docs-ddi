---
UID: NS.rilapitypes.RILLOCATIONINFO
title: RILLOCATIONINFO
author: windows-driver-content
description: This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.
old-location: netvista\rillocationinfo_2.htm
ms.assetid: 057f8cb0-0473-470e-b993-457de90d98fd
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
req.alt-api: RILLOCATIONINFO
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
ms.keywords: RILLOCATIONINFO, RILLOCATIONINFO
req.iface: 
req.product: Windows 10 or later.
---

# RILLOCATIONINFO structure



## -description
<p>This topic supports the Windows driver infrastructure and is not intended to be used directly from your code. </p>


## -syntax

````
typedef struct _RILLOCATIONINFO {
  DWORD  cbSize;
  DWORD  dwParams;
  DWORD  dwExecutor;
  DWORD  hUiccApp;
  DWORD  dwLocationAreaCode;
  DWORD  dwTrackingAreaCode;
  DWORD  dwCellID;
} RILLOCATIONINFO, RILLOCATIONINFO;
````


## -struct-fields
<dl>

### -field <b>cbSize</b>

<dd></dd>

### -field <b>dwParams</b>

<dd></dd>

### -field <b>dwExecutor</b>

<dd></dd>

### -field <b>hUiccApp</b>

<dd></dd>

### -field <b>dwLocationAreaCode</b>

<dd></dd>

### -field <b>dwTrackingAreaCode</b>

<dd></dd>

### -field <b>dwCellID</b>

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