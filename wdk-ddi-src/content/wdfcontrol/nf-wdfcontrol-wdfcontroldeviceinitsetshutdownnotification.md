---
UID: NF.wdfcontrol.WdfControlDeviceInitSetShutdownNotification
title: WdfControlDeviceInitSetShutdownNotification
author: windows-driver-content
description: The WdfControlDeviceInitSetShutdownNotification method sets shutdown notification information for a control device object.
old-location: wdf\wdfcontroldeviceinitsetshutdownnotification.htm
ms.assetid: 43a5a017-f5de-4906-acbb-96419b4a3f1c
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: wdf
req.header: wdfcontrol.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 
req.alt-api: WdfControlDeviceInitSetShutdownNotification
req.alt-loc: Wdf01000.sys,Wdf01000.sys.dll
req.ddi-compliance: ControlDeviceInitAPI, DriverCreate, KmdfIrql, KmdfIrql2
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Wdf01000.sys (see Framework Library Versioning.)
req.dll: 
req.irql: <= DISPATCH_LEVEL
ms.keywords: WdfControlDeviceInitSetShutdownNotification
req.iface: 
req.product: Windows 10 or later.
---

# WdfControlDeviceInitSetShutdownNotification function



## -description
<p class="CCE_Message">[Applies to KMDF only]</p>
<p>The <b>WdfControlDeviceInitSetShutdownNotification</b> method sets shutdown notification information for a control device object.</p>


## -syntax

````
VOID WdfControlDeviceInitSetShutdownNotification(
  _In_ PWDFDEVICE_INIT                      DeviceInit,
  _In_ PFN_WDF_DEVICE_SHUTDOWN_NOTIFICATION Notification,
  _In_ UCHAR                                Flags
);
````


## -parameters
<dl>

### -param <i>DeviceInit</i> [in]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff546951">WDFDEVICE_INIT</a> structure that the driver obtained by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff545841">WdfControlDeviceInitAllocate</a>.</p>
</dd>

### -param <i>Notification</i> [in]

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/365e669b-b4a1-432a-ab0c-9292a910256e">EvtDeviceShutdownNotification</a> event callback function.</p>
</dd>

### -param <i>Flags</i> [in]

<dd>
<p>One or more <a href="https://msdn.microsoft.com/library/windows/hardware/ff551282">WDF_DEVICE_SHUTDOWN_FLAGS</a>-typed flags that indicate when the <a href="https://msdn.microsoft.com/365e669b-b4a1-432a-ab0c-9292a910256e">EvtDeviceShutdownNotification</a> callback function will be called.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>The driver must call <b>WdfControlDeviceInitSetShutdownNotification</b> before calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff545926">WdfDeviceCreate</a>. For more information about calling <b>WdfControlDeviceInitSetShutdownNotification</b>, see <a href="wdf.using_control_device_objects">Using Control Device Objects</a>.</p>

<p>For a code example that uses <b>WdfControlDeviceInitSetShutdownNotification</b>, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff545841">WdfControlDeviceInitAllocate</a>.</p>

<p>The driver must call <b>WdfControlDeviceInitSetShutdownNotification</b> before calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff545926">WdfDeviceCreate</a>. For more information about calling <b>WdfControlDeviceInitSetShutdownNotification</b>, see <a href="wdf.using_control_device_objects">Using Control Device Objects</a>.</p>

<p>For a code example that uses <b>WdfControlDeviceInitSetShutdownNotification</b>, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff545841">WdfControlDeviceInitAllocate</a>.</p>

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
<p>Minimum KMDF version</p>
</th>
<td width="70%">
<p>1.0</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdfcontrol.h (include Wdf.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Wdf01000.sys (see <a href="wdf.framework_library_versioning">Framework Library Versioning</a>.)</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543531">ControlDeviceInitAPI</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff544957">DriverCreate</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff548167">KmdfIrql</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975091">KmdfIrql2</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/365e669b-b4a1-432a-ab0c-9292a910256e">EvtDeviceShutdownNotification</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551282">WDF_DEVICE_SHUTDOWN_FLAGS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546951">WDFDEVICE_INIT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545926">WdfDeviceCreate</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WdfControlDeviceInitSetShutdownNotification method%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>