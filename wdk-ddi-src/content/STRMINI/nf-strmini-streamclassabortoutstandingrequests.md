---
UID: NF.strmini.StreamClassAbortOutstandingRequests
title: StreamClassAbortOutstandingRequests
author: windows-driver-content
description: The StreamClassAbortOutstandingRequests routine aborts all outstanding requests, either to a particular stream, or to the entire driver.
old-location: stream\streamclassabortoutstandingrequests.htm
ms.assetid: d60ef96b-d145-48e5-be56-7f0bc4d1d0f3
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: stream
req.header: strmini.h
req.include-header: Strmini.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: StreamClassAbortOutstandingRequests
req.alt-loc: Stream.lib,Stream.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Stream.lib
req.dll: 
req.irql: > DISPATCH_LEVEL
ms.keywords: StreamClassAbortOutstandingRequests
req.iface: 
req.product: Windows 10 or later.
---

# StreamClassAbortOutstandingRequests function



## -description
<p>The <b>StreamClassAbortOutstandingRequests</b> routine aborts all outstanding requests, either to a particular stream, or to the entire driver.</p>


## -syntax

````
VOID StreamClassAbortOutstandingRequests(
  _In_     PVOID             HwDeviceExtension,
  _In_opt_ PHW_STREAM_OBJECT HwStreamObject,
  _In_     NTSTATUS          Status
);
````


## -parameters
<dl>

### -param <i>HwDeviceExtension</i> [in]

<dd>
<p>Pointer to the minidriver's device extension. The minidriver specifies the size of this buffer in the <a href="https://msdn.microsoft.com/library/windows/hardware/ff559682">HW_INITIALIZATION_DATA</a> structure it passes when it registers itself via <a href="https://msdn.microsoft.com/library/windows/hardware/ff568263">StreamClassRegisterMinidriver</a>. The class driver then passes pointers to the buffer in the <b>HwDeviceExtension</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff559702">HW_STREAM_REQUEST_BLOCK</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff559697">HW_STREAM_OBJECT</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff559706">HW_TIME_CONTEXT</a>, and <a href="https://msdn.microsoft.com/library/windows/hardware/ff567785">PORT_CONFIGURATION_INFORMATION</a> structures it passes to the minidriver.</p>
</dd>

### -param <i>HwStreamObject</i> [in, optional]

<dd>
<p>Pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff559697">HW_STREAM_OBJECT</a> that specifies which stream to abort requests on, or <b>NULL</b> to abort all requests to the minidriver. If this parameter is <b>NULL</b>, all device and stream requests are canceled.</p>
</dd>

### -param <i>Status</i> [in]

<dd>
<p>Specifies the status to be returned when an outstanding request is aborted. </p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>This call also signals the class driver that the minidriver is ready to receive new requests of the type canceled.</p>

<p>This call also signals the class driver that the minidriver is ready to receive new requests of the type canceled.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt>Desktop</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Strmini.h (include Strmini.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Stream.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&gt; DISPATCH_LEVEL</p>
</td>
</tr>
</table>