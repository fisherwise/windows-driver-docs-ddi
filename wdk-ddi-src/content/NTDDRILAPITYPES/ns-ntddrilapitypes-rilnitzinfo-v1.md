---
UID: NS.ntddrilapitypes.RILNITZINFO_V1
title: RILNITZINFO_V1
author: windows-driver-content
description: This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.
old-location: netvista\rilnitzinfo_v1.htm
ms.assetid: 88664809-b5ce-466a-894b-529443cb1b0e
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: netvista
req.header: ntddrilapitypes.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RILNITZINFO_V1
req.alt-loc: ntddrilapitypes.h
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
ms.keywords: RILNITZINFO_V1, RILNITZINFO_V1, *LPRILNITZINFO_V1
req.iface: 
---

# RILNITZINFO_V1 structure



## -description
<p>This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.</p>


## -syntax

````
typedef struct _RILNITZINFO_V1 {
  DWORD          cbSize;
  DWORD          dwParams;
  DWORD          dwExecutor;
  int            TimeZoneOffsetMinutes;
  int            DaylightSavingOffsetMinutes;
  RILSYSTEMTIME  SysTime;
} RILNITZINFO_V1, RILNITZINFO_V1;
````


## -struct-fields
<dl>

### -field <b>cbSize</b>

<dd></dd>

### -field <b>dwParams</b>

<dd></dd>

### -field <b>dwExecutor</b>

<dd></dd>

### -field <b>TimeZoneOffsetMinutes</b>

<dd></dd>

### -field <b>DaylightSavingOffsetMinutes</b>

<dd></dd>

### -field <b>SysTime</b>

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
<dt>Ntddrilapitypes.h</dt>
</dl>
</td>
</tr>
</table>