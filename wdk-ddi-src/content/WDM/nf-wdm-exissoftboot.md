---
UID: NF.wdm.ExIsSoftBoot
title: ExIsSoftBoot
author: windows-driver-content
description: Determines whether the system has gone through a soft restart.
old-location: kernel\exissoftboot.htm
ms.assetid: ff67bc75-b424-4278-b979-f67d118232aa
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows 10, version 1709
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: ExIsSoftBoot
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe (kernel mode)
req.irql: <=APC_LEVEL
ms.keywords: ExIsSoftBoot
req.iface: 
req.product: Windows 10 or later.
---

# ExIsSoftBoot function



## -description
<p>Determines whether the system has gone through a soft restart.</p>


## -syntax

````
 BOOLEAN  ExIsSoftBoot(
   VOID 
);
````


## -parameters


## -returns
<p>TRUE indicates a soft restart; FALSE otherwise.</p>

<p>TRUE indicates a soft restart; FALSE otherwise.</p>

<p>TRUE indicates a soft restart; FALSE otherwise.</p>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 10, version 1709</p>
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
<dt>Wdm.h</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>NtosKrnl.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>NtosKrnl.exe (kernel mode)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&lt;=APC_LEVEL</p>
</td>
</tr>
</table>