---
UID: NC.drmk.PFNDRMGETCONTENTRIGHTS
title: PFNDRMGETCONTENTRIGHTS
author: windows-driver-content
description: This callback function is reserved for system use.
old-location: audio\pfndrmgetcontentrights.htm
ms.assetid: 1230C71C-9C1A-4F1F-8AA7-C814249675B5
ms.author: windowsdriverdev
ms.date: 10/30/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: audio
req.header: drmk.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DRMGetContentRights
req.alt-loc: Drmk.h
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
ms.keywords: WDI_TXRX_TARGET_CONFIGURATION, WDI_TXRX_TARGET_CONFIGURATION, *PWDI_TXRX_TARGET_CONFIGURATION
req.iface: 
---

# PFNDRMGETCONTENTRIGHTS callback



## -description
<p>This callback function is reserved for system use.</p>


## -prototype

````
PFNDRMGETCONTENTRIGHTS DRMGetContentRights;

NTSTATUS DRMGetContentRights(
  _In_  ULONG      ContentId,
  _Out_ PDRMRIGHTS DrmRights
)
{ ... }

typedef PFNDRMGETCONTENTRIGHTS DRMGetContentRights;
````


## -parameters
<dl>

### -param <i>ContentId</i> [in]

<dd>
<p>This parameter is reserved for system use.</p>
</dd>

### -param <i>DrmRights</i> [out]

<dd>
<p>This parameter is reserved for system use.</p>
</dd>
</dl>

## -returns
<p>This return value is reserved for system use.</p>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Drmk.h</dt>
</dl>
</td>
</tr>
</table>