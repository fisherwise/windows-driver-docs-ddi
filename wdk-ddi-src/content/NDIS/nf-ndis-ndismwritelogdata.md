---
UID: NF.ndis.NdisMWriteLogData
title: NdisMWriteLogData
author: windows-driver-content
description: NdisMWriteLogData transfers driver-supplied information into the log file for consumption and display by a driver-dedicated Win32 application.
old-location: netvista\ndismwritelogdata.htm
ms.assetid: 38923308-0268-49b3-9f9d-0fa2b62f7533
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: netvista
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Universal
req.target-min-winverclnt: Supported for NDIS 6.0 and NDIS 5.1 drivers (see 
   NdisMWriteLogData (NDIS 5.1)) in
   Windows Vista. Supported for NDIS 5.1 drivers (see 
   NdisMWriteLogData (NDIS 5.1)) in
   Windows XP.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NdisMWriteLogData
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
ms.keywords: NdisMWriteLogData
req.iface: 
---

# NdisMWriteLogData function



## -description
<p><b>NdisMWriteLogData</b> transfers driver-supplied information into the log file for consumption and display
  by a driver-dedicated Win32 application.</p>


## -syntax

````
NDIS_STATUS NdisMWriteLogData(
  _In_ NDIS_HANDLE LogHandle,
  _In_ PVOID       LogBuffer,
  _In_ UINT        LogBufferSize
);
````


## -parameters
<dl>

### -param <i>LogHandle</i> [in]

<dd>
<p>Specifies the handle returned by 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff563572">NdisMCreateLog</a>.</p>
</dd>

### -param <i>LogBuffer</i> [in]

<dd>
<p>Pointer to a driver-allocated buffer containing the information to be written.</p>
</dd>

### -param <i>LogBufferSize</i> [in]

<dd>
<p>Specifies how many bytes of data to copy into the log file.</p>
</dd>
</dl>

## -returns
<p><b>NdisMWriteLogData</b> can return one of the following:</p><dl>
<dt><b>NDIS_STATUS_SUCCESS</b></dt>
</dl><p>The driver-supplied data at 
       <i>LogBuffer</i> has been copied into the log file.</p><dl>
<dt><b>NDIS_STATUS_BUFFER_OVERFLOW</b></dt>
</dl><p>The given 
       <i>LogBufferSize</i> is too large, that is, larger than the log file itself.</p>

<p> </p>

## -remarks
<p>If the driver-dedicated application has an outstanding request for log file data, 
    <b>NdisMWriteLogData</b> satisfies that request as soon as it has copied the driver-supplied information
    into the log file.</p>

<p>The miniport driver can supply a 
    <i>LogBuffer</i> pointer to a location on the kernel stack if it is currently running at IRQL &lt;
    DISPATCH_LEVEL. Otherwise, 
    <i>LogBuffer</i> must access a buffer that the driver allocated from nonpaged pool.</p>

<p>The driver must release any spin lock it is holding before calling 
    <b>NdisMWriteLogData</b>.</p>

<p><b>NdisMWriteLogData</b> does not recognize boundaries between log records, nor does the Win32 function, 
    <a href="base.deviceiocontrol">DeviceIoControl</a>, which applications can call with IOCTL_NDIS_GET_LOG_DATA to retrieve data written
    to an NDIS log file by an NDIS miniport driver. 
    <b>NdisMWriteLogData</b> writes all miniport driver-supplied data at 
    <i>LogBuffer</i> into the log file as a byte stream. 
    <b>DeviceIoControl</b> reads the data from such a log as a byte stream, as well.</p>

<p>Consequently, an application reading an NDIS log must collect retrieved data into records. To aid such
    an application in collecting variable-length records, any miniport driver writing to such a log can
    insert a marker at the beginning of each record. Then, the application formatting the retrieved data can
    search for these markers to determine the start of each record.</p>

<p>If the driver-dedicated application has an outstanding request for log file data, 
    <b>NdisMWriteLogData</b> satisfies that request as soon as it has copied the driver-supplied information
    into the log file.</p>

<p>The miniport driver can supply a 
    <i>LogBuffer</i> pointer to a location on the kernel stack if it is currently running at IRQL &lt;
    DISPATCH_LEVEL. Otherwise, 
    <i>LogBuffer</i> must access a buffer that the driver allocated from nonpaged pool.</p>

<p>The driver must release any spin lock it is holding before calling 
    <b>NdisMWriteLogData</b>.</p>

<p><b>NdisMWriteLogData</b> does not recognize boundaries between log records, nor does the Win32 function, 
    <a href="base.deviceiocontrol">DeviceIoControl</a>, which applications can call with IOCTL_NDIS_GET_LOG_DATA to retrieve data written
    to an NDIS log file by an NDIS miniport driver. 
    <b>NdisMWriteLogData</b> writes all miniport driver-supplied data at 
    <i>LogBuffer</i> into the log file as a byte stream. 
    <b>DeviceIoControl</b> reads the data from such a log as a byte stream, as well.</p>

<p>Consequently, an application reading an NDIS log must collect retrieved data into records. To aid such
    an application in collecting variable-length records, any miniport driver writing to such a log can
    insert a marker at the beginning of each record. Then, the application formatting the retrieved data can
    search for these markers to determine the start of each record.</p>

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
   <a href="https://msdn.microsoft.com/library/windows/hardware/ff553671">NdisMWriteLogData (NDIS 5.1)</a>) in
   Windows Vista. Supported for NDIS 5.1 drivers (see 
   <b>NdisMWriteLogData (NDIS 5.1)</b>) in
   Windows XP.</p>
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
<a href="https://msdn.microsoft.com/aac4049c-a876-4bbb-ba3b-fa36c299e1c7">
   NdisAllocateMemoryWithTagPriority</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/df690a05-359d-44f0-b063-4fc21d6c4d76">
   NdisAllocateFromNPagedLookasideList</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562790">NdisMCloseLog</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563572">NdisMCreateLog</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563584">NdisMFlushLog</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564524">NdisReleaseSpinLock</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NdisMWriteLogData function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>