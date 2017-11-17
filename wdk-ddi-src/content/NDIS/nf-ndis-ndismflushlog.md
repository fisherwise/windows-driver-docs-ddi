---
UID: NF.ndis.NdisMFlushLog
title: NdisMFlushLog
author: windows-driver-content
description: NdisMFlushLog clears the log file.
old-location: netvista\ndismflushlog.htm
ms.assetid: a681b704-80cc-406a-b60f-31ef5f953164
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: netvista
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Universal
req.target-min-winverclnt: Supported for NDIS 6.0 and NDIS 5.1 drivers (see 
   NdisMFlushLog (NDIS 5.1)) in Windows
   Vista. Supported for NDIS 5.1 drivers (see 
   NdisMFlushLog (NDIS 5.1)) in Windows
   XP.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NdisMFlushLog
req.alt-loc: ndis.lib,ndis.dll
req.ddi-compliance: Irql_Miniport_Driver_Function
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ndis.lib
req.dll: 
req.irql: <= DISPATCH_LEVEL
ms.keywords: NdisMFlushLog
req.iface: 
---

# NdisMFlushLog function



## -description
<p><b>NdisMFlushLog</b> clears the log file.</p>


## -syntax

````
VOID NdisMFlushLog(
  _In_ NDIS_HANDLE LogHandle
);
````


## -parameters
<dl>

### -param <i>LogHandle</i> [in]

<dd>
<p>Specifies the handle returned by 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff563572">NdisMCreateLog</a>.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p><b>NdisMFlushLog</b> resets the position pointers within the log file to the start of the file.</p>

<p>The driver must release any spin lock it is holding before calling 
    <b>NdisMFlushLog</b>.</p>

<p><b>NdisMFlushLog</b> resets the position pointers within the log file to the start of the file.</p>

<p>The driver must release any spin lock it is holding before calling 
    <b>NdisMFlushLog</b>.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt><a href="http://go.microsoft.com/fwlink/p/?linkid=531356" target="_blank">Universal</a></dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Supported for NDIS 6.0 and NDIS 5.1 drivers (see 
   <a href="https://msdn.microsoft.com/library/windows/hardware/ff553522">NdisMFlushLog (NDIS 5.1)</a>) in Windows
   Vista. Supported for NDIS 5.1 drivers (see 
   <b>NdisMFlushLog (NDIS 5.1)</b>) in Windows
   XP.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ndis.h (include Ndis.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Ndis.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&lt;= DISPATCH_LEVEL</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547979">Irql_Miniport_Driver_Function</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562790">NdisMCloseLog</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563572">NdisMCreateLog</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563695">NdisMWriteLogData</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564524">NdisReleaseSpinLock</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NdisMFlushLog function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>