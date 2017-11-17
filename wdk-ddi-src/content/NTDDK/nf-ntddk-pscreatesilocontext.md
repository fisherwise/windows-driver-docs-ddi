---
UID: NF.ntddk.PsCreateSiloContext
title: PsCreateSiloContext
author: windows-driver-content
description: This routine creates an object that will be inserted in a Silo.
old-location: kernel\pscreatesilocontext.htm
ms.assetid: 54FD0308-7E40-40C7-BA3A-FF1EFFBE0DB6
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
req.alt-api: PsCreateSiloContext
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
ms.keywords: PsCreateSiloContext
req.iface: 
---

# PsCreateSiloContext function



## -description
<p>This routine  creates an object that will be inserted in a <i>Silo</i>.</p>


## -syntax

````
NTSTATUS PsCreateSiloContext(
  _In_     PESILO                                 Silo,
  _In_     ULONG                                  Size,
  _In_     POOL_TYPE                              PoolType,
  _In_opt_ SILO_CONTEXT_CLEANUP_CALLBACK          ContextCleanupCallback,
           _Outptr_result_bytebuffer_(Size) PVOID *ReturnedSiloContext
);
````


## -parameters
<dl>

### -param <i>Silo</i> [in]

<dd>
<p>A pointer to a silo.  This parameter is required and it cannot be <b>NULL</b>.</p>
</dd>

### -param <i>Size</i> [in]

<dd>
<p>The size, in bytes, of the portion of the object defined by the caller.</p>
</dd>

### -param <i>PoolType</i> [in]

<dd>
<p>The type of pool to allocate from. This parameter is required and must be one of the following: <b>NonPagedPoolNx</b> or <b>PagedPool</b>.</p>
</dd>

### -param <i>ContextCleanupCallback</i> [in, optional]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/mt735085">SILO_CONTEXT_CLEANUP_CALLBACK</a> callback function. The function will be called when the returned object has zero references to it. This parameter is optional and can be <b>NULL</b>. </p>
</dd>

### -param <i>ReturnedSiloContext</i> 

<dd>
<p>A pointer to a caller-allocated variable that receives the address of the newly created object. </p>
</dd>
</dl>

## -returns
<p>The following NT status codes are returned.</p><dl>
<dt><b>STATUS_INSUFFICIENT_RESOURCES </b></dt>
</dl><p>The routine encountered a pool allocation failure. This is an error code. </p><dl>
<dt><b>STATUS_INVALID_PARAMETER</b></dt>
</dl><p>The pool type is not valid. This is an error code.</p><dl>
<dt><b>STATUS_SUCCESS</b></dt>
</dl><p>The operation completed successfully.</p>

<p> </p>

## -remarks


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