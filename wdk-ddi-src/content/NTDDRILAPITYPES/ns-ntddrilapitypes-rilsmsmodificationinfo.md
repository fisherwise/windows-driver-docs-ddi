---
UID: NS.ntddrilapitypes.RILSMSMODIFICATIONINFO
title: RILSMSMODIFICATIONINFO
author: windows-driver-content
description: This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.
old-location: netvista\rilsmsmodificationinfo.htm
ms.assetid: 8fed32a2-f0a7-4462-b8bb-b01c9cccf6b7
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
req.alt-api: RILSMSMODIFICATIONINFO
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
ms.keywords: RILSMSMODIFICATIONINFO, RILSMSMODIFICATIONINFO, *LPRILSMSMODIFICATIONINFO
req.iface: 
---

# RILSMSMODIFICATIONINFO structure



## -description
<p>This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.</p>


## -syntax

````
typedef struct _RILSMSMODIFICATIONINFO {
  DWORD               cbSize;
  DWORD               dwParams;
  DWORD               dwExecutor;
  DWORD               dwModificationType;
  RILADDRESS          raAddress;
  RILALPHAIDENTIFIER  aiIdentifier;
} RILSMSMODIFICATIONINFO, RILSMSMODIFICATIONINFO;
````


## -struct-fields
<dl>

### -field <b>cbSize</b>

<dd></dd>

### -field <b>dwParams</b>

<dd></dd>

### -field <b>dwExecutor</b>

<dd></dd>

### -field <b>dwModificationType</b>

<dd></dd>

### -field <b>raAddress</b>

<dd></dd>

### -field <b>aiIdentifier</b>

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