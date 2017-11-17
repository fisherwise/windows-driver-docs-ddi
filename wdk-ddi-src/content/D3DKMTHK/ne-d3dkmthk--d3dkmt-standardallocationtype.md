---
UID: NE.d3dkmthk._D3DKMT_STANDARDALLOCATIONTYPE
title: D3DKMT_STANDARDALLOCATIONTYPE
author: windows-driver-content
description: Used to give information on the allocation type.
old-location: display\d3dkmt-standardallocationtype.htm
ms.assetid: 7ce6d148-bfe8-4040-a4c1-ccd22fd07307
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmthk.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3DKMT_STANDARDALLOCATIONTYPE
req.alt-loc: d3dkmthk.h
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
ms.keywords: DXGKMDT_OPM_STANDARD_INFORMATION, DXGKMDT_OPM_STANDARD_INFORMATION
req.iface: 
---

# D3DKMT_STANDARDALLOCATIONTYPE enumeration



## -description
<p>Used to give information on the allocation type.</p>


## -syntax

````
typedef enum _D3DKMT_STANDARDALLOCATIONTYPE { 
  D3DKMT_STANDARDALLOCATIONTYPE_EXISTINGHEAP  = 1
} D3DKMT_STANDARDALLOCATIONTYPE;
````


## -enum-fields
<dl>

### -field <a id="D3DKMT_STANDARDALLOCATIONTYPE_EXISTINGHEAP"></a><a id="d3dkmt_standardallocationtype_existingheap"></a><b>D3DKMT_STANDARDALLOCATIONTYPE_EXISTINGHEAP</b>

<dd>
<p>Indicates that the allocation type is an existing heap.</p>
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
<dt>D3dkmthk.h</dt>
</dl>
</td>
</tr>
</table>