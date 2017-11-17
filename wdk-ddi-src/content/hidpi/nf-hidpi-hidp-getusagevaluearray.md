---
UID: NF.hidpi.HidP_GetUsageValueArray
title: HidP_GetUsageValueArray
author: windows-driver-content
description: The HidP_GetUsageValueArray routine extracts the data associated with a HID control usage value array from a HID report.
old-location: hid\hidp_getusagevaluearray.htm
ms.assetid: afc92692-c665-44a7-b268-d29adc42f5bd
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
req.alt-api: HidP_GetUsageValueArray
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
ms.keywords: HidP_GetUsageValueArray
req.iface: 
---

# HidP_GetUsageValueArray function



## -description
<p>The <b>HidP_GetUsageValueArray</b> routine extracts the data associated with a HID control <a href="hid.value_capability_arrays#usage_value_array#usage_value_array">usage value array</a> from a HID report.</p>


## -syntax

````
NTSTATUS __stdcall HidP_GetUsageValueArray(
  _In_    HIDP_REPORT_TYPE     ReportType,
  _In_    USAGE                UsagePage,
  _In_    USHORT               LinkCollection,
  _In_    USAGE                Usage,
  _Inout_ PCHAR                UsageValue,
  _In_    USHORT               UsageValueByteLength,
  _In_    PHIDP_PREPARSED_DATA PreparsedData,
  _In_    PCHAR                Report,
  _In_    ULONG                ReportLength
);
````


## -parameters
<dl>

### -param <i>ReportType</i> [in]

<dd>
<p>Specifies a <a href="https://msdn.microsoft.com/library/windows/hardware/ff539774">HIDP_REPORT_TYPE</a> enumerator value that identifies the report type.</p>
</dd>

### -param <i>UsagePage</i> [in]

<dd>
<p>Specifies the <a href="hid.hid_usages#usage_page#usage_page">usage page</a> of the usage value array.</p>
</dd>

### -param <i>LinkCollection</i> [in]

<dd>
<p>Specifies the <a href="https://msdn.microsoft.com/3f934661-c33c-4c08-82ac-ee2e0f519c8e">link collection</a> that contains the usage value array. If <i>LinkCollection</i> is nonzero, the routine only searches for a usage value array in this link collection; otherwise, if <i>LinkCollection</i> is zero, the routine searches for a usage value array in the <a href="https://msdn.microsoft.com/dcbee8e3-d03a-45c8-92e4-0897b9f55177">top-level collection</a> associated with <i>PreparsedData</i>.</p>
</dd>

### -param <i>Usage</i> [in]

<dd>
<p>Specifies the usage of the usage value array.</p>
</dd>

### -param <i>UsageValue</i> [in, out]

<dd>
<p>Pointer to a caller-allocated buffer in which the routine returns the data associated with the usage value array.</p>
</dd>

### -param <i>UsageValueByteLength</i> [in]

<dd>
<p>Specifies the length, in bytes, of the buffer at <i>UsageValue</i>.</p>
</dd>

### -param <i>PreparsedData</i> [in]

<dd>
<p>Pointer to a top-level collection's <a href="NULL">preparsed data</a>.</p>
</dd>

### -param <i>Report</i> [in]

<dd>
<p>Pointer to a report that contains values.</p>
</dd>

### -param <i>ReportLength</i> [in]

<dd>
<p>Specifies the length, in bytes, of the report located at <i>Report</i>.</p>
</dd>
</dl>

## -returns
<p><b>HidP_GetUsageValueArray </b>returns one of the following status values:</p><dl>
<dt><b>HIDP_STATUS_SUCCESS</b></dt>
</dl><p>The routine successfully returned the value's data.</p><dl>
<dt><b>HIDP_INVALID_REPORT_LENGTH</b></dt>
</dl><p>The report length is not valid.</p><dl>
<dt><b>HIDP_INVALID_REPORT_TYPE</b></dt>
</dl><p>The specified report type is not valid.</p><dl>
<dt><b>HIDP_STATUS_NOT_VALUE_ARRAY</b></dt>
</dl><p>The requested usage is not a usage value array.</p><dl>
<dt><b>HIDP_STATUS_BUFFER_TOO_SMALL</b></dt>
</dl><p>The <i>UsageValue</i> buffer is too small to hold the requested usage. </p><dl>
<dt><b>HIDP_STATUS_INCOMPATIBLE_REPORT_ID</b></dt>
</dl><p>The collection contains a usage value array on the specified usage page in a report of the specified type, but there are no such usages in the specified report.</p><dl>
<dt><b>HIDP_STATUS_INVALID_PREPARSED_DATA</b></dt>
</dl><p>The preparsed data is not valid.</p><dl>
<dt><b>HIDP_STATUS_USAGE_NOT_FOUND</b></dt>
</dl><p>The collection does not contain a usage value array on the specified usage page in any report of the specified report type.</p>

<p> </p>

## -remarks
<p>The required size, in bytes, of <i>UsageValueByteLength</i> is determined by multiplying together the <b>BitSize</b> and <b>ReportCount</b> members of the usage value array's <a href="https://msdn.microsoft.com/library/windows/hardware/ff539832">HIDP_VALUE_CAPS</a> structure, and rounding the result up to the nearest byte.</p>

<p><b>HidP_GetUsageValueArray</b> sets the <i>UsageValue</i> buffer in little-endian order, beginning with the least significant bit of the usage's data. The data is not byte-aligned, and is shifted such that the least significant bit of the data is located at the first bit of the <i>UsageValue</i> buffer.</p>

<p><b>HidP_GetUsageValueArray</b> is designed to extract all the usage values for a usage whose report count is greater than 1. To extract a usage whose report count is equal to 1, use <b>HidP_GetUsageValue</b>. </p>

<p>For more information, see <a href="NULL">HID Collections</a>. </p>

<p>The required size, in bytes, of <i>UsageValueByteLength</i> is determined by multiplying together the <b>BitSize</b> and <b>ReportCount</b> members of the usage value array's <a href="https://msdn.microsoft.com/library/windows/hardware/ff539832">HIDP_VALUE_CAPS</a> structure, and rounding the result up to the nearest byte.</p>

<p><b>HidP_GetUsageValueArray</b> sets the <i>UsageValue</i> buffer in little-endian order, beginning with the least significant bit of the usage's data. The data is not byte-aligned, and is shifted such that the least significant bit of the data is located at the first bit of the <i>UsageValue</i> buffer.</p>

<p><b>HidP_GetUsageValueArray</b> is designed to extract all the usage values for a usage whose report count is greater than 1. To extract a usage whose report count is equal to 1, use <b>HidP_GetUsageValue</b>. </p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539708">HidP_GetButtons</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539712">HidP_GetButtonsEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539715">HidP_GetCaps</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539729">HidP_GetScaledUsageValue</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539742">HidP_GetUsages</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539745">HidP_GetUsagesEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539748">HidP_GetUsageValue</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539832">HIDP_VALUE_CAPS</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [hid\hid]:%20HidP_GetUsageValueArray routine%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>