---
UID: NS.ks._MF_MDL_SHARED_PAYLOAD_KEY
title: MF_MDL_SHARED_PAYLOAD_KEY
author: windows-driver-content
description: This union is used internally by the operating system.
old-location: stream\mf_mdl_shared_payload_key.htm
ms.assetid: 3EA093AB-1D23-4744-997E-8C7072934628
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: stream
req.header: ks.h
req.include-header: Ks.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: MF_MDL_SHARED_PAYLOAD_KEY
req.alt-loc: ks.h
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
ms.keywords: MF_MDL_SHARED_PAYLOAD_KEY, MF_MDL_SHARED_PAYLOAD_KEY, *PMF_MDL_SHARED_PAYLOAD_KEY
req.iface: 
---

# MF_MDL_SHARED_PAYLOAD_KEY structure



## -description
<p>This union is used internally by the operating system.</p>


## -syntax

````
typedef union _MF_MDL_SHARED_PAYLOAD_KEY {
  struct {
    ULONG   pHandle;
    ULONG   fHandle;
    ULONG64 uPayload;
  } combined;
  GUID   GMDLHandle;
} MF_MDL_SHARED_PAYLOAD_KEY, PMF_MDL_SHARED_PAYLOAD_KEY;
````


## -struct-fields
<dl>

### -field <b>combined</b>

<dd>
<p>This member is used internally by the operating system.</p>
<dl>

### -field <b>pHandle</b>

<dd>
<p>This member is used internally by the operating system.</p>
</dd>

### -field <b>fHandle</b>

<dd>
<p>This member is used internally by the operating system.</p>
</dd>

### -field <b>uPayload</b>

<dd>
<p>This member is used internally by the operating system.</p>
</dd>
</dl>
</dd>

### -field <b>GMDLHandle</b>

<dd>
<p>This structure is used internally by the operating system.</p>
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
<dt>Ks.h (include Ks.h)</dt>
</dl>
</td>
</tr>
</table>