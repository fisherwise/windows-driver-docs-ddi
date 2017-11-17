---
UID: NF.hidsdi.HidD_SetFeature
title: HidD_SetFeature
author: windows-driver-content
description: The HidD_SetFeature routine sends a feature report to a top-level collection.
old-location: hid\hidd_setfeature.htm
ms.assetid: 69b7d775-e689-4010-8c83-f9e393d692be
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
req.alt-api: HidD_SetFeature
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
ms.keywords: HidD_SetFeature
req.iface: 
---

# HidD_SetFeature function



## -description
<p>The <b>HidD_SetFeature</b> routine sends a feature report to a <a href="https://msdn.microsoft.com/dcbee8e3-d03a-45c8-92e4-0897b9f55177">top-level collection</a>.</p>


## -syntax

````
BOOLEAN __stdcall HidD_SetFeature(
  _In_ HANDLE HidDeviceObject,
  _In_ PVOID  ReportBuffer,
  _In_ ULONG  ReportBufferLength
);
````


## -parameters
<dl>

### -param <i>HidDeviceObject</i> [in]

<dd>
<p>Specifies an open handle to a top-level collection.</p>
</dd>

### -param <i>ReportBuffer</i> [in]

<dd>
<p>Pointer to a caller-allocated feature report buffer that the caller uses to specify a HID report ID.</p>
<p>For more information about this parameter, see the <b>Remarks</b> section.</p>
</dd>

### -param <i>ReportBufferLength</i> [in]

<dd>
<p>Specifies the size, in bytes, of the report buffer. The report buffer must be large enough to hold the feature report -- excluding its report ID, if report IDs are used -- plus one additional byte that specifies a nonzero report ID or zero.</p>
</dd>
</dl>

## -returns
<p>If <b>HidD_SetFeature</b> succeeds, it returns <b>TRUE</b>; otherwise, it returns <b>FALSE</b>.</p>

## -remarks
<p>Before it calls the <b>HidD_SetFeature</b> routine, the caller must do the following:</p>

<p>If the <a href="https://msdn.microsoft.com/dcbee8e3-d03a-45c8-92e4-0897b9f55177">top-level collection</a> includes report IDs, the caller must set the first byte of the <i>ReportBuffer</i> parameter to a nonzero report ID.</p>

<p>If the <a href="https://msdn.microsoft.com/dcbee8e3-d03a-45c8-92e4-0897b9f55177">top-level collection</a> does not include report IDs, the caller must set the first byte of the <i>ReportBuffer</i> parameter to zero.

</p>

<p>The feature report is referenced by the <i>ReportBuffer</i> parameter. Depending on the report ID, the caller prepares the report by calling one of the following functions:</p>

<p>For an example of how to prepare and  a HID report and send it to a <a href="https://msdn.microsoft.com/dcbee8e3-d03a-45c8-92e4-0897b9f55177">top-level collection</a>, see the <a href="http://go.microsoft.com/fwlink/p/?linkid=256119">HClient</a> sample application. This sample is located in the MSDN Code Gallery.</p>

<p>Only user-mode applications can call <b>HidD_SetFeature</b>. Kernel-mode drivers can use an <a href="https://msdn.microsoft.com/library/windows/hardware/ff541196">IOCTL_HID_SET_OUTPUT_REPORT</a> request.</p>

<p>For more information, see the following topics:</p><dl>
<dd>
<p>
<a href="NULL">Sending HID Reports</a>
</p>
</dd>
<dd>
<p>
<a href="NULL">Interpreting HID Reports</a>
</p>
</dd>
</dl><p>
<a href="NULL">Sending HID Reports</a>
</p>

<p>
<a href="NULL">Interpreting HID Reports</a>
</p>

<p>Before it calls the <b>HidD_SetFeature</b> routine, the caller must do the following:</p>

<p>If the <a href="https://msdn.microsoft.com/dcbee8e3-d03a-45c8-92e4-0897b9f55177">top-level collection</a> includes report IDs, the caller must set the first byte of the <i>ReportBuffer</i> parameter to a nonzero report ID.</p>

<p>If the <a href="https://msdn.microsoft.com/dcbee8e3-d03a-45c8-92e4-0897b9f55177">top-level collection</a> does not include report IDs, the caller must set the first byte of the <i>ReportBuffer</i> parameter to zero.

</p>

<p>The feature report is referenced by the <i>ReportBuffer</i> parameter. Depending on the report ID, the caller prepares the report by calling one of the following functions:</p>

<p>For an example of how to prepare and  a HID report and send it to a <a href="https://msdn.microsoft.com/dcbee8e3-d03a-45c8-92e4-0897b9f55177">top-level collection</a>, see the <a href="http://go.microsoft.com/fwlink/p/?linkid=256119">HClient</a> sample application. This sample is located in the MSDN Code Gallery.</p>

<p>Only user-mode applications can call <b>HidD_SetFeature</b>. Kernel-mode drivers can use an <a href="https://msdn.microsoft.com/library/windows/hardware/ff541196">IOCTL_HID_SET_OUTPUT_REPORT</a> request.</p>

<p>For more information, see the following topics:</p><dl>
<dd>
<p>
<a href="NULL">Sending HID Reports</a>
</p>
</dd>
<dd>
<p>
<a href="NULL">Interpreting HID Reports</a>
</p>
</dd>
</dl><p>
<a href="NULL">Sending HID Reports</a>
</p>

<p>
<a href="NULL">Interpreting HID Reports</a>
</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff538910">HidD_GetFeature</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff538945">HidD_GetInputReport</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539690">HidD_SetOutputReport</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541100">IOCTL_HID_GET_FEATURE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541126">IOCTL_HID_GET_INPUT_REPORT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541176">IOCTL_HID_SET_FEATURE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541196">IOCTL_HID_SET_OUTPUT_REPORT</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [hid\hid]:%20HidD_SetFeature routine%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>