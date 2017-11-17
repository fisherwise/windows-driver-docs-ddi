---
UID: NI.hidport.IOCTL_HID_GET_STRING
title: IOCTL_HID_GET_STRING
author: windows-driver-content
description: The IOCTL_HID_GET_STRING request obtains a manufacturer ID, product ID, or serial number for a top-level collection. The retrieved string is a NULL-terminated wide character string in a human-readable format.
old-location: hid\ioctl_hid_get_string.htm
ms.assetid: 0812f27f-f38c-487d-9e92-98e16ddde21c
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: ioctl
ms.prod: windows-hardware
ms.technology: hid
req.header: hidport.h
req.include-header: Hidport.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IOCTL_HID_GET_STRING
req.alt-loc: hidport.h
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
ms.keywords: HidRegisterMinidriver
req.iface: 
---

# IOCTL_HID_GET_STRING IOCTL



## -description
<p>The IOCTL_HID_GET_STRING request obtains a manufacturer ID, product ID, or serial number for a <a href="https://msdn.microsoft.com/dcbee8e3-d03a-45c8-92e4-0897b9f55177">top-level collection</a>. The retrieved string is a NULL-terminated wide character string in a human-readable format.</p>
<p>For general information about HIDClass devices, see <a href="NULL">HID Collections</a>. </p>


## -ioctlparameters

### -input-buffer
<p>IOCTL_HID_GET_STRING makes use of two input buffers.</p>

<p><b>Parameters.DeviceIoControl.OutputBufferLength</b> in the I/O stack location of the IRP indicates the size, in bytes, of the locked-down output buffer at <b>Irp-&gt;UserBuffer</b>. If the output buffer is not large enough to hold the entire NULL-terminated embedded string, the request returns nothing in the output buffer. The maximum possible number of characters in an embedded string is device specific. For USB devices, the maximum string length is 126 wide characters (not including the terminating NULL character). </p>

<p><b>Parameters.DeviceIoControl.Type3InputBuffer</b> in the I/O stack location of the IRP contains a composite value. The two most significant bytes contain the language ID of the string to be retrieved. The two least significant bytes contain one of the following three constant values: </p>

<p>HID_STRING_ID_IMANUFACTURER</p>

<p>HID_STRING_ID_IPRODUCT</p>

<p>HID_STRING_ID_ISERIALNUMBER</p>

<p>The HID minidriver determines which of these three constants is present in the lower two bytes of the input buffer, then it must retrieve the corresponding string index from the device descriptor. Device descriptor information is stored in the device extension of a top-level collection associated with the device.</p>

<p>It is important not to confuse these three constants with the actual string indices of the IDs. These constants represent the offsets in the device descriptor where the corresponding string indices can be found.</p>

<p>For example, HID_STRING_ID_IMANUFACTURER indicates the location in the device descriptor where the index for the manufacturer ID is found. This index, in turn, serves as an offset into the string descriptor where the human-readable form of the manufacturer ID is located.</p>

### -input-buffer-length
<p>The size of the <b>OutputBufferLength</b> and the size of the <b>Type3InputBuffer</b>.</p>

<p>The size of the <b>OutputBufferLength</b> and the size of the <b>Type3InputBuffer</b>.</p>

### -output-buffer
<p>The HID minidriver fills the buffer at <b>Irp-&gt;UserBuffer</b> with the requested string (a NULL-terminated wide character string).</p>

<p>The HID minidriver fills the buffer at <b>Irp-&gt;UserBuffer</b> with the requested string (a NULL-terminated wide character string).</p>

<p>The HID minidriver fills the buffer at <b>Irp-&gt;UserBuffer</b> with the requested string (a NULL-terminated wide character string).</p>

### -output-buffer-length
<p>The size of the <b>UserBuffer</b>.</p>

<p>The size of the <b>UserBuffer</b>.</p>

<p>The size of the <b>UserBuffer</b>.</p>

<p>The size of the <b>UserBuffer</b>.</p>

### -in-out-buffer

<text></text>

### -inout-buffer-length

<text></text>

### -status-block
I/O Status block
<p>HID minidrivers that carry out the I/O to the device set the following fields of <b>Irp-&gt;IoStatus</b>:</p>

<p><b>Information</b> is set to the number of bytes transferred from the device.</p>

<p><b>Status</b> is set to STATUS_SUCCESS if the transfer completed without error. Otherwise, it is set to an appropriate NTSTATUS error code.</p>

<p>HID minidrivers that call other drivers with this IOCTL to carry out the I/O to their device, should ensure that the <b>Information</b> field of the status block is correct and not change the contents of the <b>Status</b> field.</p>

<p>HID minidrivers that carry out the I/O to the device set the following fields of <b>Irp-&gt;IoStatus</b>:</p>

<p><b>Information</b> is set to the number of bytes transferred from the device.</p>

<p><b>Status</b> is set to STATUS_SUCCESS if the transfer completed without error. Otherwise, it is set to an appropriate NTSTATUS error code.</p>

<p>HID minidrivers that call other drivers with this IOCTL to carry out the I/O to their device, should ensure that the <b>Information</b> field of the status block is correct and not change the contents of the <b>Status</b> field.</p>

<p>HID minidrivers that carry out the I/O to the device set the following fields of <b>Irp-&gt;IoStatus</b>:</p>

<p><b>Information</b> is set to the number of bytes transferred from the device.</p>

<p><b>Status</b> is set to STATUS_SUCCESS if the transfer completed without error. Otherwise, it is set to an appropriate NTSTATUS error code.</p>

<p>HID minidrivers that call other drivers with this IOCTL to carry out the I/O to their device, should ensure that the <b>Information</b> field of the status block is correct and not change the contents of the <b>Status</b> field.</p>

<p>HID minidrivers that carry out the I/O to the device set the following fields of <b>Irp-&gt;IoStatus</b>:</p>

<p><b>Information</b> is set to the number of bytes transferred from the device.</p>

<p><b>Status</b> is set to STATUS_SUCCESS if the transfer completed without error. Otherwise, it is set to an appropriate NTSTATUS error code.</p>

<p>HID minidrivers that call other drivers with this IOCTL to carry out the I/O to their device, should ensure that the <b>Information</b> field of the status block is correct and not change the contents of the <b>Status</b> field.</p>

<p>HID minidrivers that carry out the I/O to the device set the following fields of <b>Irp-&gt;IoStatus</b>:</p>

<p><b>Information</b> is set to the number of bytes transferred from the device.</p>

<p><b>Status</b> is set to STATUS_SUCCESS if the transfer completed without error. Otherwise, it is set to an appropriate NTSTATUS error code.</p>

<p>HID minidrivers that call other drivers with this IOCTL to carry out the I/O to their device, should ensure that the <b>Information</b> field of the status block is correct and not change the contents of the <b>Status</b> field.</p>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Hidport.h (include Hidport.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff538927">HidD_GetIndexedString</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff538959">HidD_GetManufacturerString</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539681">HidD_GetProductString</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539683">HidD_GetSerialNumberString</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541109">IOCTL_HID_GET_INDEXED_STRING</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541134">IOCTL_HID_GET_MANUFACTURER_STRING</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541146">IOCTL_HID_GET_PRODUCT_STRING</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541160">IOCTL_HID_GET_SERIALNUMBER_STRING</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [hid\hid]:%20IOCTL_HID_GET_STRING control code%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>