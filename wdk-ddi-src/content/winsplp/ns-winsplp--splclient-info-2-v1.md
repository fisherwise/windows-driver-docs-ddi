---
UID: NS.winsplp._SPLCLIENT_INFO_2_V1
title: SPLCLIENT_INFO_2_V1
author: windows-driver-content
description: Contains the handle for the server-side printer that is used to make direct API calls from the client to the server without the overhead of the RPC.
old-location: print\splclient_info_2_w2k.htm
ms.assetid: 713246FE-355B-4C01-A8DF-535BDBA0FCB8
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: print
req.header: winsplp.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: SPLCLIENT_INFO_2_W2K
req.alt-loc: Winsplp.h
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
ms.keywords: SPLCLIENT_INFO_2_V1, SPLCLIENT_INFO_2_W2K
req.iface: 
req.product: Windows 10 or later.
---

# SPLCLIENT_INFO_2_V1 structure



## -description
<p>Contains the handle for the server-side printer that is used to make direct API calls from the client to the server without the overhead of the RPC. The performance improvement is primarily observed in calls to read/write printer made from within the spooler (Gdi32.dll during playback). This structure is used in the private spooler RPC interface (RpcSplOpenPrinter).</p>


## -syntax

````
typedef struct _SPLCLIENT_INFO_2_V1 {
  ULONG_PTR        hSplPrinter;
} SPLCLIENT_INFO_2_W2K;
````


## -struct-fields
<dl>

### -field <b>hSplPrinter</b>

<dd>
<p>Specifies the server-side handle to be used for direct calls.</p>
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
<dt>Winsplp.h</dt>
</dl>
</td>
</tr>
</table>