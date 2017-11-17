---
UID: NF.wdfdevice.WdfDeviceInitSetDeviceClass
title: WdfDeviceInitSetDeviceClass
author: windows-driver-content
description: The WdfDeviceInitSetDeviceClass method specifies a GUID that identifies the device's device setup class.
old-location: wdf\wdfdeviceinitsetdeviceclass.htm
ms.assetid: c87a8368-3804-4a07-92c8-65a453d0808f
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: wdf
req.header: wdfdevice.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 
req.alt-api: WdfDeviceInitSetDeviceClass
req.alt-loc: Wdf01000.sys,Wdf01000.sys.dll
req.ddi-compliance: ChildDeviceInitAPI, ControlDeviceInitAPI, DeviceInitAPI, DriverCreate, KmdfIrql, KmdfIrql2, PdoDeviceInitAPI
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Wdf01000.sys (see Framework Library Versioning.)
req.dll: 
req.irql: <= DISPATCH_LEVEL
ms.keywords: WdfDeviceInitSetDeviceClass
req.iface: 
req.product: Windows 10 or later.
---

# WdfDeviceInitSetDeviceClass function



## -description
<p class="CCE_Message">[Applies to KMDF only]</p>
<p>The <b>WdfDeviceInitSetDeviceClass</b> method specifies a GUID that identifies the device's <a href="devinst.device_setup_classes">device setup class</a>. </p>


## -syntax

````
VOID WdfDeviceInitSetDeviceClass(
  _In_       PWDFDEVICE_INIT DeviceInit,
  _In_ const GUID            *DeviceClassGuid
);
````


## -parameters
<dl>

### -param <i>DeviceInit</i> [in]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff546951">WDFDEVICE_INIT</a> structure.</p>
</dd>

### -param <i>DeviceClassGuid</i> [in]

<dd>
<p>Pointer to a GUID that identifies a section of the registry containing possible overrides for the <i>DefaultSDDLString</i>, <i>DeviceType</i>, <i>DeviceCharacteristics</i>, and <i>Exclusive</i> parameters.</p>
<div class="alert"><b>Note</b>    You should always specify a custom class GUID. You should not specify an existing class GUID. If you specify an existing class GUID, other drivers that attempt to specify that existing class GUID might fail to install or might install with incorrect security settings.</div>
<div> </div>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>The registry can contain values that override the values that a driver specifies when it calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff546035">WdfDeviceInitAssignSDDLString</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff546090">WdfDeviceInitSetDeviceType</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff546074">WdfDeviceInitSetCharacteristics</a>, and <a href="https://msdn.microsoft.com/library/windows/hardware/ff546097">WdfDeviceInitSetExclusive</a>. The driver can call <b>WdfDeviceInitSetDeviceClass</b> to specify a GUID that identifies the section of the registry that contains the override values.</p>

<p>Typically, a driver calls <b>WdfDeviceInitSetDeviceClass</b> only if it is creating a <a href="wdf.using_control_device_objects">control device</a>. </p>

<p>For more information about using the registry, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563755">Setting Device Object Registry Properties After Installation</a>.</p>

<p>If a driver calls <b>WdfDeviceInitSetDeviceClass</b>, it must do so before it calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff545926">WdfDeviceCreate</a>.</p>

<p>For more information about calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff545926">WdfDeviceCreate</a>, see <a href="wdf.creating_a_framework_device_object">Creating a Framework Device Object</a>.</p>

<p>The following code example sets a device's setup class to the system device class.</p>

<p>The registry can contain values that override the values that a driver specifies when it calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff546035">WdfDeviceInitAssignSDDLString</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff546090">WdfDeviceInitSetDeviceType</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff546074">WdfDeviceInitSetCharacteristics</a>, and <a href="https://msdn.microsoft.com/library/windows/hardware/ff546097">WdfDeviceInitSetExclusive</a>. The driver can call <b>WdfDeviceInitSetDeviceClass</b> to specify a GUID that identifies the section of the registry that contains the override values.</p>

<p>Typically, a driver calls <b>WdfDeviceInitSetDeviceClass</b> only if it is creating a <a href="wdf.using_control_device_objects">control device</a>. </p>

<p>For more information about using the registry, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563755">Setting Device Object Registry Properties After Installation</a>.</p>

<p>If a driver calls <b>WdfDeviceInitSetDeviceClass</b>, it must do so before it calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff545926">WdfDeviceCreate</a>.</p>

<p>For more information about calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff545926">WdfDeviceCreate</a>, see <a href="wdf.creating_a_framework_device_object">Creating a Framework Device Object</a>.</p>

<p>The following code example sets a device's setup class to the system device class.</p>

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
<dt>Wdfdevice.h (include Wdf.h)</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/hh975068">ChildDeviceInitAPI</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff543531">ControlDeviceInitAPI</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff544843">DeviceInitAPI</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff544957">DriverCreate</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff548167">KmdfIrql</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975091">KmdfIrql2</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff550354">PdoDeviceInitAPI</a>
</td>
</tr>
</table>