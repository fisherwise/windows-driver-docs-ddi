---
UID: NS.ntddrilapitypes.RILUICCSERVICE
title: RILUICCSERVICE
author: windows-driver-content
description: This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.
old-location: netvista\riluiccservice.htm
ms.assetid: 67c8abef-c920-4bc4-8216-8b6026a1962d
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
req.alt-api: RILUICCSERVICE
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
ms.keywords: RILUICCSERVICE, RILUICCSERVICE, *LPRILUICCSERVICE
req.iface: 
---

# RILUICCSERVICE structure



## -description
<p>This topic supports the Windows driver infrastructure and is not intended to be used directly from your code.</p>


## -syntax

````
typedef struct _RILUICCSERVICE {
  HUICCAPP               hUiccApp;
  RILUICCSERVICESERVICE  dwService;
} RILUICCSERVICE, RILUICCSERVICE;
````


## -struct-fields
<dl>

### -field <b>hUiccApp</b>

<dd></dd>

### -field <b>dwService</b>

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