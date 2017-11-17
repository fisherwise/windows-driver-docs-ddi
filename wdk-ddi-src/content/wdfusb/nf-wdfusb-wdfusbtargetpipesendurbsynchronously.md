---
UID: NF.wdfusb.WdfUsbTargetPipeSendUrbSynchronously
title: WdfUsbTargetPipeSendUrbSynchronously
author: windows-driver-content
description: The WdfUsbTargetPipeSendUrbSynchronously method builds an USB request for a specified USB pipe, using request parameters that a specified URB describes.
old-location: wdf\wdfusbtargetpipesendurbsynchronously.htm
ms.assetid: 2ce7a843-0053-4351-ba79-161d83e245ac
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: wdf
req.header: wdfusb.h
req.include-header: Wdfusb.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 
req.alt-api: WdfUsbTargetPipeSendUrbSynchronously
req.alt-loc: Wdf01000.sys,Wdf01000.sys.dll
req.ddi-compliance: DriverCreate, IoctlReqs, KmdfIrql, KmdfIrql2, SyncReqSend, UsbKmdfIrql, UsbKmdfIrql2
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Wdf01000.sys (see Framework Library Versioning.)
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: WdfUsbTargetPipeSendUrbSynchronously
req.iface: 
req.product: Windows 10 or later.
---

# WdfUsbTargetPipeSendUrbSynchronously function



## -description
<p class="CCE_Message">[Applies to KMDF only]</p>
<p>The <b>WdfUsbTargetPipeSendUrbSynchronously</b> method builds an USB request for a specified USB pipe, using request parameters that a specified <a href="https://msdn.microsoft.com/library/windows/hardware/ff538923">URB</a> describes.</p>


## -syntax

````
NTSTATUS WdfUsbTargetPipeSendUrbSynchronously(
  _In_     WDFUSBPIPE                Pipe,
  _In_opt_ WDFREQUEST                Request,
  _In_opt_ PWDF_REQUEST_SEND_OPTIONS RequestOptions,
  _In_     PURB                      Urb
);
````


## -parameters
<dl>

### -param <i>Pipe</i> [in]

<dd>
<p>A handle to a framework pipe object that was obtained by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff550057">WdfUsbInterfaceGetConfiguredPipe</a>. </p>
</dd>

### -param <i>Request</i> [in, optional]

<dd>
<p>A handle to a framework request object. This parameter is optional and can be <b>NULL</b>. For more information, see the following Remarks section.</p>
</dd>

### -param <i>RequestOptions</i> [in, optional]

<dd>
<p>A pointer to a caller-allocated <a href="https://msdn.microsoft.com/library/windows/hardware/ff552491">WDF_REQUEST_SEND_OPTIONS</a> structure that specifies options for the request. This pointer is optional and can be <b>NULL</b>. For more information, see the following Remarks section.</p>
</dd>

### -param <i>Urb</i> [in]

<dd>
<p>A pointer to a driver-initialized <a href="https://msdn.microsoft.com/library/windows/hardware/ff538923">URB</a> structure.</p>
<p>If the driver previously called <a href="https://msdn.microsoft.com/library/windows/hardware/hh439428">WdfUsbTargetDeviceCreateWithParameters</a> to create <i>UsbDevice</i>, the driver must use <a href="https://msdn.microsoft.com/library/windows/hardware/hh439423">WdfUsbTargetDeviceCreateUrb</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/hh439420">WdfUsbTargetDeviceCreateIsochUrb</a> to create this URB.</p>
</dd>
</dl>

## -returns
<p><b>WdfUsbTargetPipeSendUrbSynchronously</b> returns the I/O target's completion status value if the operation succeeds. Otherwise, this method might return one of the following values:</p><dl>
<dt><b>STATUS_INFO_LENGTH_MISMATCH</b></dt>
</dl><p>The size of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff552491">WDF_REQUEST_SEND_OPTIONS</a> structure that the <i>RequestOptions</i> parameter specified was incorrect.</p><dl>
<dt><b>STATUS_INVALID_PARAMETER</b></dt>
</dl><p>An invalid parameter was detected.</p><dl>
<dt><b>STATUS_INSUFFICIENT_RESOURCES</b></dt>
</dl><p>Insufficient memory was available.</p><dl>
<dt><b>STATUS_INVALID_DEVICE_REQUEST</b></dt>
</dl><p>The caller's IRQL was not PASSIVE_LEVEL, or the specified I/O request was already queued to an I/O target.</p><dl>
<dt><b>STATUS_IO_TIMEOUT</b></dt>
</dl><p>The driver supplied a time-out value and the request did not complete within the allotted time. </p><dl>
<dt><b>STATUS_REQUEST_NOT_ACCEPTED</b></dt>
</dl><p>The I/O request packet (<a href="https://msdn.microsoft.com/library/windows/hardware/ff550694">IRP</a>) that the <i>Request</i> parameter represents does not provide enough <a href="https://msdn.microsoft.com/library/windows/hardware/ff550659">IO_STACK_LOCATION</a> structures to allow the driver to forward the request.</p>

<p> </p>

<p>This method also might return other <a href="https://msdn.microsoft.com/library/windows/hardware/ff557697">NTSTATUS values</a>.</p>

<p>A bug check occurs if the driver supplies an invalid object handle.

</p>

## -remarks
<p>Use the <b>WdfUsbTargetPipeSendUrbSynchronously</b> method to send a USB request synchronously. To send such requests asynchronously, use <a href="https://msdn.microsoft.com/library/windows/hardware/ff551139">WdfUsbTargetPipeFormatRequestForUrb</a>, followed by <a href="https://msdn.microsoft.com/library/windows/hardware/ff550027">WdfRequestSend</a>.</p>

<p>The <b>WdfUsbTargetPipeSendUrbSynchronously</b> method does not return until the request has completed, unless the driver supplies a time-out value in the <a href="https://msdn.microsoft.com/library/windows/hardware/ff552491">WDF_REQUEST_SEND_OPTIONS</a> structure that the <i>RequestOptions</i> parameter points to, or unless an error is detected.</p>

<p>The framework does not examine the USB request. If the request changes the state of the USB pipe, the framework will not be aware of the change.</p>

<p>You can forward an I/O request that your driver received in an I/O queue, or you can create and send a new request.</p>

<p>To forward an I/O request that your driver received in an I/O queue, specify the received request's handle for the <b>WdfUsbTargetPipeSendUrbSynchronously</b> method's <i>Request</i> parameter.</p>

<p>To create and send a new request, either supply a <b>NULL</b> request handle for the <i>Request</i> parameter, or create a new request object and supply its handle:</p>

<p>If you supply a <b>NULL</b> request handle, the framework uses an internal request object. This technique is simple to use, but the driver cannot cancel the request.</p>

<p>If you call <a href="https://msdn.microsoft.com/library/windows/hardware/ff549951">WdfRequestCreate</a> to create one or more request objects, you can reuse these request objects by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff550026">WdfRequestReuse</a>. This technique enables your driver's <a href="https://msdn.microsoft.com/b20db029-ee2c-4fb1-bd69-ccd2e37fdc9a">EvtDriverDeviceAdd</a> callback function to preallocate request objects for a device. Additionally, another driver thread can call <a href="https://msdn.microsoft.com/library/windows/hardware/ff549941">WdfRequestCancelSentRequest</a> to cancel the request, if necessary.</p>

<p>Your driver can specify a non-<b>NULL</b> <i>RequestOptions</i> parameter, whether the driver provides a non-<b>NULL</b> or a <b>NULL</b> <i>Request</i> parameter. You can, for example, use the <i>RequestOptions</i> parameter to specify a time-out value. </p>

<p>For information about obtaining status information after an I/O request completes, see <a href="wdf.completing_i_o_requests#obtaining_completion_information#obtaining_completion_information">Obtaining Completion Information</a>.</p>

<p>For more information about the <b>WdfUsbTargetPipeSendUrbSynchronously</b> method and USB I/O targets, see <a href="wdf.usb_i_o_targets">USB I/O Targets</a>.</p>

<p>The following code example initializes a URB and sends the URB to a USB pipe.</p>

<p>Use the <b>WdfUsbTargetPipeSendUrbSynchronously</b> method to send a USB request synchronously. To send such requests asynchronously, use <a href="https://msdn.microsoft.com/library/windows/hardware/ff551139">WdfUsbTargetPipeFormatRequestForUrb</a>, followed by <a href="https://msdn.microsoft.com/library/windows/hardware/ff550027">WdfRequestSend</a>.</p>

<p>The <b>WdfUsbTargetPipeSendUrbSynchronously</b> method does not return until the request has completed, unless the driver supplies a time-out value in the <a href="https://msdn.microsoft.com/library/windows/hardware/ff552491">WDF_REQUEST_SEND_OPTIONS</a> structure that the <i>RequestOptions</i> parameter points to, or unless an error is detected.</p>

<p>The framework does not examine the USB request. If the request changes the state of the USB pipe, the framework will not be aware of the change.</p>

<p>You can forward an I/O request that your driver received in an I/O queue, or you can create and send a new request.</p>

<p>To forward an I/O request that your driver received in an I/O queue, specify the received request's handle for the <b>WdfUsbTargetPipeSendUrbSynchronously</b> method's <i>Request</i> parameter.</p>

<p>To create and send a new request, either supply a <b>NULL</b> request handle for the <i>Request</i> parameter, or create a new request object and supply its handle:</p>

<p>If you supply a <b>NULL</b> request handle, the framework uses an internal request object. This technique is simple to use, but the driver cannot cancel the request.</p>

<p>If you call <a href="https://msdn.microsoft.com/library/windows/hardware/ff549951">WdfRequestCreate</a> to create one or more request objects, you can reuse these request objects by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff550026">WdfRequestReuse</a>. This technique enables your driver's <a href="https://msdn.microsoft.com/b20db029-ee2c-4fb1-bd69-ccd2e37fdc9a">EvtDriverDeviceAdd</a> callback function to preallocate request objects for a device. Additionally, another driver thread can call <a href="https://msdn.microsoft.com/library/windows/hardware/ff549941">WdfRequestCancelSentRequest</a> to cancel the request, if necessary.</p>

<p>Your driver can specify a non-<b>NULL</b> <i>RequestOptions</i> parameter, whether the driver provides a non-<b>NULL</b> or a <b>NULL</b> <i>Request</i> parameter. You can, for example, use the <i>RequestOptions</i> parameter to specify a time-out value. </p>

<p>For information about obtaining status information after an I/O request completes, see <a href="wdf.completing_i_o_requests#obtaining_completion_information#obtaining_completion_information">Obtaining Completion Information</a>.</p>

<p>For more information about the <b>WdfUsbTargetPipeSendUrbSynchronously</b> method and USB I/O targets, see <a href="wdf.usb_i_o_targets">USB I/O Targets</a>.</p>

<p>The following code example initializes a URB and sends the URB to a USB pipe.</p>

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
<dt>Wdfusb.h (include Wdfusb.h)</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544957">DriverCreate</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff547288">IoctlReqs</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff548167">KmdfIrql</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975091">KmdfIrql2</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff552890">SyncReqSend</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff554042">UsbKmdfIrql</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh995019">UsbKmdfIrql2</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552491">WDF_REQUEST_SEND_OPTIONS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550057">WdfUsbInterfaceGetConfiguredPipe</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549941">WdfRequestCancelSentRequest</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WdfUsbTargetPipeSendUrbSynchronously method%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>