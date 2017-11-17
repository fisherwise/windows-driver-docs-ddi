---
UID: NE.ntddscsi._MP_STORAGE_DIAGNOSTIC_LEVEL
title: MP_STORAGE_DIAGNOSTIC_LEVEL
author: windows-driver-content
description: The MP_STORAGE_DIAGNOSTIC_LEVEL enumeration allows the caller to control what kinds of data the provider should return.
old-location: storage\mp_storage_diagnostic_level.htm
ms.assetid: BB05D543-7B99-481E-8CDB-AE350CBCCA2A
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: Storage
req.header: ntddscsi.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Available starting with Windows 10, version 1709.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: MP_STORAGE_DIAGNOSTIC_LEVEL
req.alt-loc: ntddscsi.h
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
ms.keywords: RILWRITEPHONEBOOKENTRYPARAMS, RILWRITEPHONEBOOKENTRYPARAMS, *LPRILWRITEPHONEBOOKENTRYPARAMS
req.iface: 
---

# MP_STORAGE_DIAGNOSTIC_LEVEL enumeration



## -description
<p>The <b>MP_STORAGE_DIAGNOSTIC_LEVEL</b> enumeration allows the caller to control what kinds of data the provider should return.</p>


## -syntax

````
typedef enum _MP_STORAGE_DIAGNOSTIC_LEVEL { 
  StorageDiagnosticLevelDefault  = 0,
  StorageDiagnosticLevelMax
} MP_STORAGE_DIAGNOSTIC_LEVEL, *PMP_STORAGE_DIAGNOSTIC_LEVEL;
````


## -enum-fields
<dl>

### -field <a id="StorageDiagnosticLevelDefault"></a><a id="storagediagnosticleveldefault"></a><a id="STORAGEDIAGNOSTICLEVELDEFAULT"></a><b>StorageDiagnosticLevelDefault</b>

<dd>
<p>Specifies the default diagnostic level.</p>
</dd>

### -field <a id="StorageDiagnosticLevelMax"></a><a id="storagediagnosticlevelmax"></a><a id="STORAGEDIAGNOSTICLEVELMAX"></a><b>StorageDiagnosticLevelMax</b>

<dd>
<p>Specifies the max diagnostic level.</p>
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
<p>Available starting with Windows 10, version 1709.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntddscsi.h</dt>
</dl>
</td>
</tr>
</table>