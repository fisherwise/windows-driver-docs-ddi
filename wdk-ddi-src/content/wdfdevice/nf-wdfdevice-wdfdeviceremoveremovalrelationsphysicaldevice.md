---
UID: NF.wdfdevice.WdfDeviceRemoveRemovalRelationsPhysicalDevice
title: WdfDeviceRemoveRemovalRelationsPhysicalDevice
author: windows-driver-content
description: The WdfDeviceRemoveRemovalRelationsPhysicalDevice method removes a specified device from the list of devices that must be removed when another specified device is removed.
old-location: wdf\wdfdeviceremoveremovalrelationsphysicaldevice.htm
ms.assetid: f9b50dc2-1af7-47c3-87c6-d33858569eed
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
req.alt-api: WdfDeviceRemoveRemovalRelationsPhysicalDevice
req.alt-loc: Wdf01000.sys,Wdf01000.sys.dll
req.ddi-compliance: DriverCreate, KmdfIrql, KmdfIrql2
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Wdf01000.sys (see Framework Library Versioning.)
req.dll: 
req.irql: <= DISPATCH_LEVEL
ms.keywords: WdfDeviceRemoveRemovalRelationsPhysicalDevice
req.iface: 
req.product: Windows 10 or later.
---

# WdfDeviceRemoveRemovalRelationsPhysicalDevice function



## -description
<p class="CCE_Message">[Applies to KMDF only]</p>
<p>The <b>WdfDeviceRemoveRemovalRelationsPhysicalDevice</b> method removes a specified device from the list of devices that must be removed when another specified device is removed. </p>


## -syntax

````
VOID WdfDeviceRemoveRemovalRelationsPhysicalDevice(
  _In_ WDFDEVICE      Device,
  _In_ PDEVICE_OBJECT PhysicalDevice
);
````


## -parameters
<dl>

### -param <i>Device</i> [in]

<dd>
<p>A handle to a framework device object.</p>
</dd>

### -param <i>PhysicalDevice</i> [in]

<dd>
<p>A pointer to a caller-supplied <a href="https://msdn.microsoft.com/library/windows/hardware/ff543147">DEVICE_OBJECT</a> structure that represents a physical device object (PDO).</p>
</dd>
</dl>

## -returns
<p>None.</p>

<p>A bug check occurs if the driver supplies an invalid object handle.</p>

<p>The following code example removes the device that <b>pPdo</b> identifies from the list of devices that must be removed when the device that <b>device</b> specifies is removed.</p>

## -remarks


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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544957">DriverCreate</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff548167">KmdfIrql</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975091">KmdfIrql2</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545875">WdfDeviceAddRemovalRelationsPhysicalDevice</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545914">WdfDeviceClearRemovalRelationsDevices</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WdfDeviceRemoveRemovalRelationsPhysicalDevice method%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>