---
UID: NS.d3dkmddi._DXGK_QAITARGETIN
title: DXGK_QAITARGETIN
author: windows-driver-content
description: Used to integrate a target.
old-location: display\dxgk_qaitargetin.htm
ms.assetid: C6751CB1-1460-4C1A-9E5F-99448C4F9162
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmddi.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DXGK_QAITARGETIN
req.alt-loc: d3dkmddi.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: DXGK_QAITARGETIN, DXGK_QAITARGETIN
req.iface: 
---

# DXGK_QAITARGETIN structure



## -description
<p>Used to integrate a target.</p>


## -syntax

````
typedef struct _DXGK_QAITARGETIN {
  D3DDDI_VIDEO_PRESENT_TARGET_ID TargetId;
} DXGK_QAITARGETIN;
````


## -struct-fields
<dl>

### -field <b>TargetId</b>

<dd>
<p>The ID of the target.</p>
</dd>
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
<dt>D3dkmddi.h</dt>
</dl>
</td>
</tr>
</table>