---
UID: NS.d3dkmddi._DXGK_SEGMENTFLAGS2
title: DXGK_SEGMENTFLAGS2
author: windows-driver-content
description: The DXGK_SEGMENTFLAGS2 structure is reserved for system use. Do not use it in your driver.
old-location: display\dxgk_segmentflags2.htm
ms.assetid: 9e6f96a2-d32f-4ef8-aaad-dc0cbd053222
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmddi.h
req.include-header: D3dkmddi.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows 7 and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DXGK_SEGMENTFLAGS2
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
ms.keywords: DXGK_SEGMENTFLAGS2, DXGK_SEGMENTFLAGS2
req.iface: 
---

# DXGK_SEGMENTFLAGS2 structure



## -description
<p>The DXGK_SEGMENTFLAGS2 structure is reserved for system use. Do not use it in your driver.</p>


## -syntax

````
typedef struct _DXGK_SEGMENTFLAGS2 {
  union {
    struct {
      UINT Aperture  :1;
      UINT PopulatedFromSystemMemory  :1;
      UINT SystemMemoryReservedByBios  :1;
      UINT CpuVisible  :1;
      UINT Reserved  :28;
    };
    UINT Value;
  };
} DXGK_SEGMENTFLAGS2;
````


## -struct-fields
<dl>

### -field <b>Aperture</b>

<dd>
<p>Reserved for system use.</p>
</dd>

### -field <b>PopulatedFromSystemMemory</b>

<dd>
<p>Reserved for system use.</p>
</dd>

### -field <b>SystemMemoryReservedByBios</b>

<dd>
<p>Reserved for system use.</p>
</dd>

### -field <b>CpuVisible</b>

<dd>
<p>Reserved for system use.</p>
</dd>

### -field <b>Reserved</b>

<dd>
<p>Reserved for system use.</p>
</dd>

### -field <b>Value</b>

<dd>
<p>Reserved for system use.</p>
</dd>
</dl>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Available in Windows 7 and later versions of the Windows operating systems.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>D3dkmddi.h (include D3dkmddi.h)</dt>
</dl>
</td>
</tr>
</table>