---
UID: NS.winsplp.PBranchOfficeJobDataRendered
title: PBranchOfficeJobDataRendered
author: windows-driver-content
description: Contains the necessary data for logging a branch office job Pipeline Rendering Event on a remote server. This is based on job-related data available to the spooler.
old-location: print\branchofficejobdatarendered.htm
ms.assetid: 67A296B3-5D59-475E-9026-EDAB90C8E3DD
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
req.alt-api: BranchOfficeJobDataRendered
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
ms.keywords: PBranchOfficeJobDataRendered, BranchOfficeJobDataRendered, *PBranchOfficeJobDataRendered
req.iface: 
req.product: Windows 10 or later.
---

# PBranchOfficeJobDataRendered structure



## -description
<p>Contains the necessary data for logging a branch office job Pipeline Rendering Event on a remote server. This is based on job-related data available to the spooler.</p>


## -syntax

````
typedef struct {
  LONGLONG Size;
  DWORD    ICMMethod;
  short    Color;
  short    PrintQuality;
  short    YResolution;
  short    Copies;
  short    TTOption;
} BranchOfficeJobDataRendered, *PBranchOfficeJobDataRendered;
````


## -struct-fields
<dl>

### -field <b>Size</b>

<dd>
<p>Specifies the 64-bit size of the job.</p>
</dd>

### -field <b>ICMMethod</b>

<dd>
<p>Describes the <b>DWORD</b> type member <b>ICMMethod</b>.</p>
</dd>

### -field <b>Color</b>

<dd>
<p>Describes the <b>short</b> type member <b>Color</b>.</p>
</dd>

### -field <b>PrintQuality</b>

<dd>
<p>Describes the <b>short</b> type member <b>PrintQuality</b>.</p>
</dd>

### -field <b>YResolution</b>

<dd>
<p>Describes the <b>short</b> type member <b>YResolution</b>.</p>
</dd>

### -field <b>Copies</b>

<dd>
<p>Describes the <b>short</b> type member <b>Copies</b>.</p>
</dd>

### -field <b>TTOption</b>

<dd>
<p>Describes the <b>short</b> type member <b>TTOption</b>.</p>
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