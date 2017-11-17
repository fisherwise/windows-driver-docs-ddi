---
UID: NS.ndis._PD_BUFFER_VIRTUAL_SUBNET_INFO
title: PD_BUFFER_VIRTUAL_SUBNET_INFO
author: windows-driver-content
description: This structure contains the virtual subnet information.
old-location: netvista\pd_buffer_virtual_subnet_info.htm
ms.assetid: 569424A2-4279-4758-A6F1-402D25F9B04F
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: netvista
req.header: ndis.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: PD_BUFFER_VIRTUAL_SUBNET_INFO
req.alt-loc: Ndis.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: See Remarks section
ms.keywords: PD_BUFFER_VIRTUAL_SUBNET_INFO, PD_BUFFER_VIRTUAL_SUBNET_INFO
req.iface: 
---

# PD_BUFFER_VIRTUAL_SUBNET_INFO structure



## -description
<p>This structure contains the virtual subnet information.</p>


## -syntax

````
typedef struct _PD_BUFFER_VIRTUAL_SUBNET_INFO {
  UINT32 VirtualSubnetId  :24;
  UINT32 Reserved  :8;
} PD_BUFFER_VIRTUAL_SUBNET_INFO, *PPD_BUFFER_VIRTUAL_SUBNET_INFO;
````


## -struct-fields
<dl>

### -field <b>VirtualSubnetId</b>

<dd>
<p>The virtual subnet ID.</p>
</dd>

### -field <b>Reserved</b>

<dd>
<p>Reserved.</p>
</dd>
</dl>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 10</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>Windows Server 2016</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ndis.h</dt>
</dl>
</td>
</tr>
</table>