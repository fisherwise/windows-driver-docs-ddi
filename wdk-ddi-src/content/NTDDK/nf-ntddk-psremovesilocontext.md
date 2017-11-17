---
UID: NF.ntddk.PsRemoveSiloContext
title: PsRemoveSiloContext
author: windows-driver-content
description: This routine removes an object that was inserted in the Silo.
old-location: kernel\psremovesilocontext.htm
ms.assetid: 3323EF1B-9EB3-4D56-A9A5-0A8397F8A235
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: ntddk.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows 10, version 1607
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: PsRemoveSiloContext
req.alt-loc: ntddk.h
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
ms.keywords: PsRemoveSiloContext
req.iface: 
---

# PsRemoveSiloContext function



## -description
<p>This routine removes an object that was inserted in the <i>Silo</i>.</p>


## -syntax

````
NTSTATUS PsRemoveSiloContext(
  _In_ PESILO                              Silo,
  _In_ ULONG                               ContextSlot,
       _Outptr_opt_result_maybenull_ PVOID *ReturnedSiloContext
);
````


## -parameters
<dl>

### -param <i>Silo</i> [in]

<dd>
<p>The silo from which the object is to be removed. This parameter is required and it cannot be <b>NULL</b>.</p>
</dd>

### -param <i>ContextSlot</i> [in]

<dd>
<p>A slot allocated by the <a href="https://msdn.microsoft.com/library/windows/hardware/mt735056">PsAllocSiloContextSlot</a> routine.</p>
</dd>

### -param <i>ReturnedSiloContext</i> 

<dd>
<p>A pointer to a caller-allocated variable that receives the address of the removed object. This parameter is optional and can be <b>NULL</b>.</p>
</dd>
</dl>

## -returns
<p>The following NT status codes are returned.</p><dl>
<dt><b>STATUS_NOT_FOUND</b></dt>
</dl><p>The slot is empty. This is an error code.</p><dl>
<dt><b>STATUS_NOT_SUPPORTED</b></dt>
</dl><p>The slot is read-only and it cannot be modified. This is an error code. </p><dl>
<dt><b>STATUS_SUCCESS</b></dt>
</dl><p>The operation completed successfully.</p>

<p> </p>

## -remarks
<p>In a successful call to <b>PsRemoveSiloContext</b> where the <i>RemovedSiloContext</i> parameter is not <b>NULL</b> and does not point to <b>NULL</b>, the caller must decrement the object that the <i>RemovedSiloContext</i> parameter points to, by calling <a href="https://msdn.microsoft.com/library/windows/hardware/mt735059">PsDereferenceSiloContext</a> when it is no longer needed. </p>

<p>In a successful call to <b>PsRemoveSiloContext</b> where the <i>RemovedSiloContext</i> parameter is not <b>NULL</b> and does not point to <b>NULL</b>, the caller must decrement the object that the <i>RemovedSiloContext</i> parameter points to, by calling <a href="https://msdn.microsoft.com/library/windows/hardware/mt735059">PsDereferenceSiloContext</a> when it is no longer needed. </p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 10, version 1607</p>
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
<dt>Ntddk.h</dt>
</dl>
</td>
</tr>
</table>