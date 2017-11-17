---
UID: NF.wdfdevice.WdfDeviceInitRegisterPowerPolicyStateChangeCallback
title: WdfDeviceInitRegisterPowerPolicyStateChangeCallback
author: windows-driver-content
description: The WdfDeviceInitRegisterPowerPolicyStateChangeCallback method registers a driver-supplied event callback function that the framework calls when a device's power policy state machine changes state.
old-location: wdf\wdfdeviceinitregisterpowerpolicystatechangecallback.htm
ms.assetid: 61ddfdf9-65cf-482b-80fe-bc5a71f905cd
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
req.alt-api: WdfDeviceInitRegisterPowerPolicyStateChangeCallback
req.alt-loc: Wdf01000.sys,Wdf01000.sys.dll
req.ddi-compliance: ChildDeviceInitAPI, DeviceInitAPI, DriverCreate, InitFreeDeviceCallback, InitFreeDeviceCreate, InitFreeNull, KmdfIrql, KmdfIrql2, PdoDeviceInitAPI, PdoInitFreeDeviceCallback, PdoInitFreeDeviceCreate
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Wdf01000.sys (see Framework Library Versioning.)
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: WdfDeviceInitRegisterPowerPolicyStateChangeCallback
req.iface: 
req.product: Windows 10 or later.
---

# WdfDeviceInitRegisterPowerPolicyStateChangeCallback function



## -description
<p class="CCE_Message">[Applies to KMDF only]</p>
<p>The <b>WdfDeviceInitRegisterPowerPolicyStateChangeCallback</b> method registers a driver-supplied event callback function that the framework calls when a device's power policy state machine changes state.</p>


## -syntax

````
NTSTATUS WdfDeviceInitRegisterPowerPolicyStateChangeCallback(
  _In_ PWDFDEVICE_INIT                                       DeviceInit,
  _In_ WDF_DEVICE_POWER_POLICY_STATE                         PowerPolicyState,
  _In_ PFN_WDF_DEVICE_POWER_POLICY_STATE_CHANGE_NOTIFICATION EvtDevicePowerPolicyStateChange,
  _In_ ULONG                                                 CallbackTypes
);
````


## -parameters
<dl>

### -param <i>DeviceInit</i> [in]

<dd>
<p>A caller-supplied pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff546951">WDFDEVICE_INIT</a> structure.</p>
</dd>

### -param <i>PowerPolicyState</i> [in]

<dd>
<p>A <a href="https://msdn.microsoft.com/library/windows/hardware/ff551275">WDF_DEVICE_POWER_POLICY_STATE</a> enumerator that identifies the power policy machine state for which the driver is requesting notification.</p>
</dd>

### -param <i>EvtDevicePowerPolicyStateChange</i> [in]

<dd>
<p>A caller-supplied pointer to the driver's <a href="https://msdn.microsoft.com/91432773-3255-4feb-a6f4-c24da4486703">EvtDevicePowerPolicyStateChange</a> event callback function.</p>
</dd>

### -param <i>CallbackTypes</i> [in]

<dd>
<p>An ORed combination of <a href="https://msdn.microsoft.com/library/windows/hardware/ff552513">WDF_STATE_NOTIFICATION_TYPE</a>-typed enumerators.</p>
</dd>
</dl>

## -returns
<p>If <b>WdfDeviceInitRegisterPowerPolicyStateChangeCallback</b> encounters no errors, it returns STATUS_SUCCESS. Additional return values include:</p><dl>
<dt><b>STATUS_INVALID_PARAMETER</b></dt>
</dl><p>An invalid parameter was detected.</p><dl>
<dt><b>STATUS_INSUFFICIENT_RESOURCES</b></dt>
</dl><p>There is insufficient memory to complete the operation.</p>

<p> </p>

## -remarks
<p>If your driver calls <b>WdfDeviceInitRegisterPowerPolicyStateChangeCallback</b>, it must do so before it calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff545926">WdfDeviceCreate</a>.</p>

<p>For more information about <b>WdfDeviceInitRegisterPowerPolicyStateChangeCallback</b>, see <a href="wdf.state_machines_in_the_framework">State Machines in the Framework</a>.</p>

<p>The following code example registers an event callback function that the framework will call when the device's power policy state machine changes state.</p>

<p>If your driver calls <b>WdfDeviceInitRegisterPowerPolicyStateChangeCallback</b>, it must do so before it calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff545926">WdfDeviceCreate</a>.</p>

<p>For more information about <b>WdfDeviceInitRegisterPowerPolicyStateChangeCallback</b>, see <a href="wdf.state_machines_in_the_framework">State Machines in the Framework</a>.</p>

<p>The following code example registers an event callback function that the framework will call when the device's power policy state machine changes state.</p>

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
<p>PASSIVE_LEVEL</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/hh975068">ChildDeviceInitAPI</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff544843">DeviceInitAPI</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff544957">DriverCreate</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff547101">InitFreeDeviceCallback</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff547104">InitFreeDeviceCreate</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff547122">InitFreeNull</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff548167">KmdfIrql</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975091">KmdfIrql2</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff550354">PdoDeviceInitAPI</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff550359">PdoInitFreeDeviceCallback</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff550362">PdoInitFreeDeviceCreate</a>
</td>
</tr>
</table>