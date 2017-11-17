---
UID: NS.rilapitypes.RILUICCSLOTINFO
title: RILUICCSLOTINFO
author: windows-driver-content
description: This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.
old-location: netvista\riluiccslotinfo_2.htm
ms.assetid: 5fd25815-40b1-4fba-a7e8-fed24d731ab0
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
req.alt-api: RILUICCSLOTINFO
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
ms.keywords: RILUICCSLOTINFO, RILUICCSLOTINFO
req.iface: 
req.product: Windows 10 or later.
---

# RILUICCSLOTINFO structure



## -description
<p>This topic supports the Windows driver infrastructure and is not intended to be used directly from your code. </p>


## -syntax

````
typedef struct _RILUICCSLOTINFO {
  DWORD                cbSize;
  DWORD                dwParams;
  DWORD                dwNumOfUiccSlots;
  RILUICCSLOTSTATE [1] dwSlotState;
} RILUICCSLOTINFO, RILUICCSLOTINFO;
````


## -struct-fields
<dl>

### -field <b>cbSize</b>

<dd></dd>

### -field <b>dwParams</b>

<dd></dd>

### -field <b>dwNumOfUiccSlots</b>

<dd></dd>

### -field <b>dwSlotState</b>

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