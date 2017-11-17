---
UID: NF.hidpi.HidP_GetData
title: HidP_GetData
author: windows-driver-content
description: The HidP_GetData routine returns, for a specified report, an array of HIDP_DATA structures that identify the data indices of all HID control buttons that are currently set to ON (1), and the data indices and data associated with all HID control values.
old-location: hid\hidp_getdata.htm
ms.assetid: 37cbd329-81c3-40ef-be42-4a64c4a1ec3a
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: hid
req.header: hidpi.h
req.include-header: Hidpi.h
req.target-type: Universal
req.target-min-winverclnt: Available in Windows 2000 and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: HidP_GetData
req.alt-loc: Hidparse.lib,Hidparse.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Hidparse.lib
req.dll: 
req.irql: <= DISPATCH_LEVEL
ms.keywords: HidP_GetData
req.iface: 
---

# HidP_GetData function



## -description
<p>The <b>HidP_GetData</b> routine returns, for a specified report, an array of <a href="https://msdn.microsoft.com/library/windows/hardware/ff539699">HIDP_DATA</a> structures that identify the <a href="NULL">data indices</a> of all HID control buttons that are currently set to ON (1), and the data indices and data associated with all HID control values.</p>


## -syntax

````
NTSTATUS __stdcall HidP_GetData(
  _In_    HIDP_REPORT_TYPE     ReportType,
  _Out_   PHIDP_DATA           DataList,
  _Inout_ PULONG               DataLength,
  _In_    PHIDP_PREPARSED_DATA PreparsedData,
  _In_    PCHAR                Report,
  _In_    ULONG                ReportLength
);
````


## -parameters
<dl>

### -param <i>ReportType</i> [in]

<dd>
<p>Specifies a <a href="https://msdn.microsoft.com/library/windows/hardware/ff539774">HIDP_REPORT_TYPE</a> enumerator value that indicates the type of HID report located at <i>Report</i>.</p>
</dd>

### -param <i>DataList</i> [out]

<dd>
<p>Specifies a caller-allocated array of HIDP_DATA structures that the routine uses to return information about all the buttons that are currently set to ON and the data associated with values.</p>
</dd>

### -param <i>DataLength</i> [in, out]

<dd>
<p>Specifies, on input, the number of structures that the caller-allocated <i>DataList</i> array holds. Specifies, on output, the number of controls for which the routine can return data, which includes all buttons that are currently set to ON and all control values.</p>
</dd>

### -param <i>PreparsedData</i> [in]

<dd>
<p>Pointer to the <a href="NULL">preparsed data</a> of the top-level collection associated with the HID report located at <i>Report</i>.</p>
</dd>

### -param <i>Report</i> [in]

<dd>
<p>Pointer to a HID report.</p>
</dd>

### -param <i>ReportLength</i> [in]

<dd>
<p>Specifies the size, in bytes, of the HID report located at <i>Report</i>, which must be equal to the report length for the specified report type returned by <a href="https://msdn.microsoft.com/library/windows/hardware/ff539715">HidP_GetCaps</a> in the collection's <a href="https://msdn.microsoft.com/library/windows/hardware/ff539697">HIDP_CAPS</a> structure.</p>
</dd>
</dl>

## -returns
<p><b>HidP_GetData</b> returns one of the following status values:</p><dl>
<dt><b>HIDP_STATUS_SUCCESS</b></dt>
</dl><p>All the control data was successfully returned.</p><dl>
<dt><b>HIDP_STATUS_INVALID_REPORT_TYPE</b></dt>
</dl><p>The report type specified by <i>ReportType</i> is not valid</p><dl>
<dt><b>HIDP_STATUS_INVALID_PREPARSED_DATA</b></dt>
</dl><p>The preparsed data specified by <i>PreparsedData</i> is not valid</p><dl>
<dt><b>HIDP_STATUS_INVALID_REPORT_LENGTH</b></dt>
</dl><p>The size, in bytes, of the HID report is not equal to the length specified in the collection's <a href="https://msdn.microsoft.com/library/windows/hardware/ff539697">HIDP_CAPS</a> structure for the specified report type.</p><dl>
<dt><b>HIDP_STATUS_REPORT_DOES_NOT_EXIST</b></dt>
</dl><p>The top-level collection does not have a report of the specified type.</p><dl>
<dt><b>HIDP_STATUS_BUFFER_TOO_SMALL</b></dt>
</dl><p>The <i>DataList</i> array is too small to describe all the buttons, currently set to ON, and all the values in the HID report.</p>

<p> </p>

## -remarks
<p>User-mode applications and kernel-mode drivers call <a href="https://msdn.microsoft.com/library/windows/hardware/ff539768">HidP_MaxDataListLength</a> to determine the maximum possible number of HIDP_DATA structures that <b>HidP_GetData</b> can return.</p>

<p><b>HidP_GetData</b> does not return data for <a href="hid.value_capability_arrays#usage_value_array#usage_value_array">usage value arrays</a>.</p>

<p>For more information, see <a href="NULL">HID Collections</a>. </p>

<p>User-mode applications and kernel-mode drivers call <a href="https://msdn.microsoft.com/library/windows/hardware/ff539768">HidP_MaxDataListLength</a> to determine the maximum possible number of HIDP_DATA structures that <b>HidP_GetData</b> can return.</p>

<p><b>HidP_GetData</b> does not return data for <a href="hid.value_capability_arrays#usage_value_array#usage_value_array">usage value arrays</a>.</p>

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
<dt>Hidpi.h (include Hidpi.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Hidparse.lib</dt>
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
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543586">_HIDP_PREPARSED_DATA</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539699">HIDP_DATA</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539768">HidP_MaxDataListLength</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539783">HidP_SetData</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [hid\hid]:%20HidP_GetData routine%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>