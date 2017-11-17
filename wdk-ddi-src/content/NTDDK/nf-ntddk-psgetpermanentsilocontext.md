---
UID: NF.ntddk.PsGetPermanentSiloContext
title: PsGetPermanentSiloContext
author: windows-driver-content
description: This routine retrieves an object that was inserted in the Silo without incrementing the reference count.
old-location: kernel\psgetpermanentsilocontext.htm
ms.assetid: C1AEFC8F-6488-4582-9835-DAD07D4ACB17
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
req.alt-api: PsGetPermanentSiloContext
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
ms.keywords: PsGetPermanentSiloContext
req.iface: 
---

# PsGetPermanentSiloContext function



## -description
<p>This routine retrieves an object that was inserted in the <i>Silo</i> without incrementing the reference count.</p>


## -syntax

````
NTSTATUS PsGetPermanentSiloContext(
  _In_ PESILO                              Silo,
  _In_ ULONG                               ContextSlot,
       _Outptr_result_nullonfailure_ PVOID *ReturnedSiloContext
);
````


## -parameters
<dl>

### -param <i>Silo</i> [in]

<dd>
<p>The silo in which the object was inserted. This parameter is required and it cannot be <b>NULL</b>.</p>
</dd>

### -param <i>ContextSlot</i> [in]

<dd>
<p>The read-only slot that was previously allocated by<a href="https://msdn.microsoft.com/library/windows/hardware/mt735056">PsAllocSiloContextSlot</a> and made read-only by <a href="https://msdn.microsoft.com/library/windows/hardware/mt735077">PsMakeSiloContextPermanent</a>.</p>
</dd>

### -param <i>ReturnedSiloContext</i> 

<dd>
<p>A pointer to a caller-allocated variable that receives the address of the existing object. This parameter is required and it cannot be <b>NULL</b>.</p>
</dd>
</dl>

## -returns
<p>The following NT status codes are returned.</p><dl>
<dt><b>STATUS_NOT_FOUND</b></dt>
</dl><p>The slot is empty. This is an error code.</p><dl>
<dt><b>STATUS_NOT_SUPPORTED </b></dt>
</dl><p>The slot is not read-only and it cannot safely retrieve the object. This is an error code.</p><dl>
<dt><b>STATUS_SUCCESS</b></dt>
</dl><p>The operation completed successfully.</p>

<p> </p>

## -remarks
<p>A successful call to <b>PsGetPermanentSiloContext</b> does not increment the reference count on the object that the <i>ReturnedSiloContext</i> parameter points to. The returned object pointer is valid as long as there is a valid reference on the silo object.</p>

<p>A successful call to <b>PsGetPermanentSiloContext</b> does not increment the reference count on the object that the <i>ReturnedSiloContext</i> parameter points to. The returned object pointer is valid as long as there is a valid reference on the silo object.</p>

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