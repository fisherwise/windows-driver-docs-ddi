---
UID: NS.d3dukmdt._DXGKVGPU_ESCAPE_WRITE_PCI_CONFIG
title: DXGKVGPU_ESCAPE_WRITE_PCI_CONFIG
author: windows-driver-content
description: Used to write to the PCI config space.
old-location: display\dxgkvgpu_escape_write_pci_config.htm
ms.assetid: 2B0902DB-B59C-4DC5-A944-02ACE9DA16DC
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3dukmdt.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DXGKVGPU_ESCAPE_WRITE_PCI_CONFIG
req.alt-loc: d3dukmdt.h
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
ms.keywords: DXGKVGPU_ESCAPE_WRITE_PCI_CONFIG, DXGKVGPU_ESCAPE_WRITE_PCI_CONFIG
req.iface: 
---

# DXGKVGPU_ESCAPE_WRITE_PCI_CONFIG structure



## -description
<p>Used to write to the PCI config space.</p>


## -syntax

````
typedef struct _DXGKVGPU_ESCAPE_WRITE_PCI_CONFIG {
  UINT Offset;
  UINT Size;
} DXGKVGPU_ESCAPE_WRITE_PCI_CONFIG;
````


## -struct-fields
<dl>

### -field <b>Offset</b>

<dd>
<p>Offset, in bytes, in the PCI config space.</p>
</dd>

### -field <b>Size</b>

<dd>
<p>Size, in bytes, to write</p>
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
<dt>D3dukmdt.h</dt>
</dl>
</td>
</tr>
</table>