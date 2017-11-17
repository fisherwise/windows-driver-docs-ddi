---
UID: NS.nfcsedev._SECURE_ELEMENT_NFCC_CAPABILITIES
title: SECURE_ELEMENT_NFCC_CAPABILITIES
author: windows-driver-content
description: SECURE_ELEMENT_NFCC_CAPABILITIES contains NFC controller capabilities.
old-location: nfpdrivers\_secure_element_nfcc_capabilities.htm
ms.assetid: D1F9588B-02D9-49B0-B45F-AF5C140D74E4
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: nfpdrivers
req.header: nfcsedev.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: SECURE_ELEMENT_NFCC_CAPABILITIES
req.alt-loc: nfcsedev.h
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
ms.keywords: SECURE_ELEMENT_NFCC_CAPABILITIES, SECURE_ELEMENT_NFCC_CAPABILITIES, *PSECURE_ELEMENT_NFCC_CAPABILITIES
req.iface: 
---

# SECURE_ELEMENT_NFCC_CAPABILITIES structure



## -description
<p>SECURE_ELEMENT_NFCC_CAPABILITIES contains NFC controller capabilities. </p>


## -syntax

````
typedef struct _SECURE_ELEMENT_NFCC_CAPABILITIES {
  USHORT  cbMaxRoutingTableSize;
  BOOLEAN IsAidRoutingSupported;
  BOOLEAN IsProtocolRoutingSupported;
  BOOLEAN IsTechRoutingSupported;
} SECURE_ELEMENT_NFCC_CAPABILITIES, *P_SECURE_ELEMENT_NFCC_CAPABILITIES;
````


## -struct-fields
<dl>

### -field <b>cbMaxRoutingTableSize</b>

<dd>
<p>NFCC maximum listen mode routing table size.</p>
</dd>

### -field <b>IsAidRoutingSupported</b>

<dd>
<p>Specifies whether NFCC supports AID-based routing.
</p>
</dd>

### -field <b>IsProtocolRoutingSupported</b>

<dd>
<p>Specify whether NFCC supports protocol-based routing.</p>
</dd>

### -field <b>IsTechRoutingSupported</b>

<dd>
<p>Specify whether NFCC supports technology-based routing.</p>
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
<dt>Nfcsedev.h</dt>
</dl>
</td>
</tr>
</table>