---
UID: NS.ntddrilapitypes.RILMSGDCS
title: RILMSGDCS
author: windows-driver-content
description: This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.
old-location: netvista\rilmsgdcs.htm
ms.assetid: b9d37683-fd3d-42fd-9ec2-128b76325868
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
req.alt-api: RILMSGDCS
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
ms.keywords: RILMSGDCS, RILMSGDCS, *LPRILMSGDCS
req.iface: 
---

# RILMSGDCS structure



## -description
<p>This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.</p>


## -syntax

````
typedef struct _RILMSGDCS {
  DWORD                cbSize;
  DWORD                dwParams;
  RILMSGDCSTYPE        dwType;
  DWORD                dwFlags;
  RILMSGDCSMSGCLASS    dwMsgClass;
  RILMSGDCSALPHABET    dwAlphabet;
  RILMSGDCSINDICATION  dwIndication;
  DWORD                dwLanguage;
} RILMSGDCS, RILMSGDCS;
````


## -struct-fields
<dl>

### -field <b>cbSize</b>

<dd></dd>

### -field <b>dwParams</b>

<dd></dd>

### -field <b>dwType</b>

<dd></dd>

### -field <b>dwFlags</b>

<dd></dd>

### -field <b>dwMsgClass</b>

<dd></dd>

### -field <b>dwAlphabet</b>

<dd></dd>

### -field <b>dwIndication</b>

<dd></dd>

### -field <b>dwLanguage</b>

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