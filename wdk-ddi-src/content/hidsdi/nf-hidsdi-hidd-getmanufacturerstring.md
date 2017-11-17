---
UID: NF.hidsdi.HidD_GetManufacturerString
title: HidD_GetManufacturerString
author: windows-driver-content
description: The HidD_GetManufacturerString routine returns a top-level collection's embedded string that identifies the manufacturer.
old-location: hid\hidd_getmanufacturerstring.htm
ms.assetid: 21253ed7-d98d-4b97-8d83-01dd18b3c4f9
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: hid
req.header: hidsdi.h
req.include-header: Hidsdi.h
req.target-type: Universal
req.target-min-winverclnt: Available in Windows 2000 and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: HidD_GetManufacturerString
req.alt-loc: Hid.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Hid.lib
req.dll: Hid.dll
req.irql: 
ms.keywords: HidD_GetManufacturerString
req.iface: 
---

# HidD_GetManufacturerString function



## -description
<p>The <b>HidD_GetManufacturerString</b> routine returns a <a href="https://msdn.microsoft.com/dcbee8e3-d03a-45c8-92e4-0897b9f55177">top-level collection's</a> embedded string that identifies the manufacturer.</p>


## -syntax

````
BOOLEAN __stdcall HidD_GetManufacturerString(
  _In_  HANDLE HidDeviceObject,
  _Out_ PVOID  Buffer,
  _In_  ULONG  BufferLength
);
````


## -parameters
<dl>

### -param <i>HidDeviceObject</i> [in]

<dd>
<p>Specifies an open handle to a top-level collection.</p>
</dd>

### -param <i>Buffer</i> [out]

<dd>
<p>Pointer to a caller-allocated buffer that the routine uses to return the collection's manufacturer string. The routine returns a NULL-terminated wide character string in a human-readable format.</p>
</dd>

### -param <i>BufferLength</i> [in]

<dd>
<p>Specifies the length, in bytes, of a caller-allocated buffer provided at <i>Buffer</i>. If the buffer is not large enough to return the entire NULL-terminated embedded string, the routine returns nothing in the buffer.</p>
</dd>
</dl>

## -returns
<p>HidD_HidD_GetManufacturerString returns <b>TRUE</b> if it returns the entire NULL-terminated embedded string. Otherwise, the routine returns <b>FALSE</b>.</p>

## -remarks
<p>Only user-mode applications can call <b>HidD_GetManufacturerString</b>. Kernel-mode drivers can use an <a href="https://msdn.microsoft.com/library/windows/hardware/ff541134">IOCTL_HID_GET_MANUFACTURER_STRING</a> request.</p>

<p>The maximum possible number of characters in an embedded string is device specific. For USB devices, the maximum string length is 126 wide characters (not including the terminating NULL character).</p>

<p>For more information, see <a href="NULL">HID Collections</a>. </p>

<p>Only user-mode applications can call <b>HidD_GetManufacturerString</b>. Kernel-mode drivers can use an <a href="https://msdn.microsoft.com/library/windows/hardware/ff541134">IOCTL_HID_GET_MANUFACTURER_STRING</a> request.</p>

<p>The maximum possible number of characters in an embedded string is device specific. For USB devices, the maximum string length is 126 wide characters (not including the terminating NULL character).</p>

<p>For more information, see <a href="NULL">HID Collections</a>. </p>

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
<p>Available in Windows 2000 and later versions of Windows.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Hidsdi.h (include Hidsdi.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Hid.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>Hid.dll</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539677">HidD_GetPhysicalDescriptor</a>
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
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [hid\hid]:%20HidD_GetManufacturerString routine%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>