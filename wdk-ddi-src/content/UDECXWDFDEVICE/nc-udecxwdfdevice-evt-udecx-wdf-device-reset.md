---
UID: NC.udecxwdfdevice.EVT_UDECX_WDF_DEVICE_RESET
title: EVT_UDECX_WDF_DEVICE_RESET
author: windows-driver-content
description: The UDE client driver's implementation to reset the emulated host controller or the devices attached to it.
old-location: buses\evt_udecx_wdf_device_reset.htm
ms.assetid: 394343A5-10E4-4F64-AD3C-1D2114422B39
ms.author: windowsdriverdev
ms.date: 11/3/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: usbref
req.header: udecxwdfdevice.h
req.include-header: Udecx.h
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 1.15
req.umdf-ver: 
req.alt-api: EvtUdecxWdfDeviceReset
req.alt-loc: UdecxWdfDevice.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: <=DISPATCH_LEVEL
ms.keywords: UDECX_USB_ENDPOINT_INIT_AND_METADATA, UDECX_USB_ENDPOINT_INIT_AND_METADATA, *PUDECX_USB_ENDPOINT_INIT_AND_METADATA
req.iface: 
req.product: Windows 10 or later.
---

# EVT_UDECX_WDF_DEVICE_RESET callback



## -description
<p>The UDE client driver's implementation to reset the emulated host controller or the devices attached to it.</p>


## -prototype

````
EVT_UDECX_WDF_DEVICE_RESET EvtUdecxWdfDeviceReset;

void EvtUdecxWdfDeviceReset(
  _In_ WDFDEVICE UdecxWdfDevice
)
{ ... }
````


## -parameters
<dl>

### -param <i>UdecxWdfDevice</i> [in]

<dd>
<p>A handle to a framework device object that represents the controller. The client driver initialized this object in the previous call to <a href="https://msdn.microsoft.com/library/windows/hardware/mt627990">UdecxWdfDeviceAddUsbDeviceEmulation</a>.</p>
</dd>
</dl>

## -returns
<p>This callback function does not return a value.</p>

## -remarks
<p>The USB device emulation  class extension (UdeCx) invokes this callback function to notify the client driver that it must handle a reset request including resetting all downstream devices attached to the emulated host controller.
This call is asynchronous. The client driver signals completion with status information by calling <a href="https://msdn.microsoft.com/library/windows/hardware/mt627991">UdecxWdfDeviceResetComplete</a>.
If the client specified <b>UdeWdfDeviceResetActionResetEachUsbDevice</b> in <a href="https://msdn.microsoft.com/library/windows/hardware/mt628008">UDECX_WDF_DEVICE_CONFIG</a> (during the <a href="https://msdn.microsoft.com/library/windows/hardware/mt627990">UdecxWdfDeviceAddUsbDeviceEmulation</a> call), this callback is never used. Instead, each connected attached device receives an <i>EVT_UDECX_WDF_DEVICE_RESET</i> callback.
</p>

<p>The USB device emulation  class extension (UdeCx) invokes this callback function to notify the client driver that it must handle a reset request including resetting all downstream devices attached to the emulated host controller.
This call is asynchronous. The client driver signals completion with status information by calling <a href="https://msdn.microsoft.com/library/windows/hardware/mt627991">UdecxWdfDeviceResetComplete</a>.
If the client specified <b>UdeWdfDeviceResetActionResetEachUsbDevice</b> in <a href="https://msdn.microsoft.com/library/windows/hardware/mt628008">UDECX_WDF_DEVICE_CONFIG</a> (during the <a href="https://msdn.microsoft.com/library/windows/hardware/mt627990">UdecxWdfDeviceAddUsbDeviceEmulation</a> call), this callback is never used. Instead, each connected attached device receives an <i>EVT_UDECX_WDF_DEVICE_RESET</i> callback.
</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 10</p>
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
<p>Minimum KMDF version</p>
</th>
<td width="70%">
<p>1.15</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>UdecxWdfDevice.h (include Udecx.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&lt;=DISPATCH_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/mt595932">Architecture: USB Device Emulation (UDE)</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/mt595939">Write a UDE client driver</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [usbref\buses]:%20EVT_UDECX_WDF_DEVICE_RESET callback function%20 RELEASE:%20(11/3/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>