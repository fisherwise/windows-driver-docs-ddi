---
UID: NE.iscsidef.PISCSI_AUTH_TYPES
title: PISCSI_AUTH_TYPES
author: windows-driver-content
description: The ISCSI_AUTH_TYPES enumeration indicates the type of authentication method that is used to establish a logon connection.
old-location: storage\iscsi_auth_types.htm
ms.assetid: b1d38829-53bc-42a5-acaf-c1ad89b8b563
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: Storage
req.header: iscsidef.h
req.include-header: Iscsidef.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: ISCSI_AUTH_TYPES
req.alt-loc: iscsidef.h
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
ms.keywords: MSiSCSI_TCPIPConfig, MSiSCSI_TCPIPConfig, *PMSiSCSI_TCPIPConfig
req.iface: 
---

# PISCSI_AUTH_TYPES enumeration



## -description
<p>The ISCSI_AUTH_TYPES enumeration indicates the type of authentication method that is used to establish a logon connection. </p>


## -syntax

````
typedef enum  { 
  ISCSI_NO_AUTH_TYPE           = 0,
  ISCSI_CHAP_AUTH_TYPE         = 1,
  ISCSI_MUTUAL_CHAP_AUTH_TYPE  = 2
} ISCSI_AUTH_TYPES, *PISCSI_AUTH_TYPES;
````


## -enum-fields
<dl>

### -field <a id="ISCSI_NO_AUTH_TYPE"></a><a id="iscsi_no_auth_type"></a><b>ISCSI_NO_AUTH_TYPE</b>

<dd>
<p>No authentication type was specified. </p>
</dd>

### -field <a id="ISCSI_CHAP_AUTH_TYPE"></a><a id="iscsi_chap_auth_type"></a><b>ISCSI_CHAP_AUTH_TYPE</b>

<dd>
<p>Challenge handshake authentication protocol (CHAP).</p>
</dd>

### -field <a id="ISCSI_MUTUAL_CHAP_AUTH_TYPE"></a><a id="iscsi_mutual_chap_auth_type"></a><b>ISCSI_MUTUAL_CHAP_AUTH_TYPE</b>

<dd>
<p>Mutual (2-way) CHAP authentication.</p>
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
<dt>Iscsidef.h (include Iscsidef.h)</dt>
</dl>
</td>
</tr>
</table>