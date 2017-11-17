---
UID: NF.fltkernel.FltEnumerateFilterInformation
title: FltEnumerateFilterInformation
author: windows-driver-content
description: The FltEnumerateFilterInformation routine provides information about all the registered filter drivers (including minifilter and legacy filter drivers) in the system.
old-location: ifsk\fltenumeratefilterinformation.htm
ms.assetid: c8bfa809-3f32-487c-991e-2ec040e3bc98
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: ifsk
req.header: fltkernel.h
req.include-header: FltKernel.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FltEnumerateFilterInformation
req.alt-loc: FltMgr.lib,FltMgr.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: FltMgr.lib
req.dll: 
req.irql: <= APC_LEVEL
ms.keywords: FltEnumerateFilterInformation
req.iface: 
---

# FltEnumerateFilterInformation function



## -description
<p>The <b>FltEnumerateFilterInformation</b> routine provides information about all the registered filter drivers (including minifilter and legacy filter drivers) in the system.</p>


## -syntax

````
NTSTATUS FltEnumerateFilterInformation(
  _In_  ULONG                    Index,
  _In_  FILTER_INFORMATION_CLASS InformationClass,
  _Out_ PVOID                    Buffer,
  _In_  ULONG                    BufferSize,
  _Out_ PULONG                   BytesReturned
);
````


## -parameters
<dl>

### -param <i>Index</i> [in]

<dd>
<p>Zero-based index of the filter driver for which the information is requested. This parameter identifies the filter in the global list of registered filter drivers. If the list contains <i>n</i> filter drivers, valid <i>Index</i> values range from 0 to <i>n</i>-1. If the <i>Index</i> value exceeds this range, <b>FltEnumerateFilterInformation</b> returns STATUS_NO_MORE_ENTRIES.</p>
</dd>

### -param <i>InformationClass</i> [in]

<dd>
<p>Type of information requested. This parameter can have one of the following values. </p>
<table>
<tr>
<th>Value</th>
<th>Meaning</th>
</tr>
<tr>
<td>
<p><b>FilterFullInformation</b></p>
</td>
<td>
<p>The buffer pointed to by the <i>Buffer</i> parameter receives a <a href="https://msdn.microsoft.com/library/windows/hardware/ff541587">FILTER_FULL_INFORMATION</a> structure for the minifilter driver (legacy filter drivers are ignored).</p>
</td>
</tr>
<tr>
<td>
<p><b>FilterAggregateBasicInformation</b></p>
</td>
<td>
<p>The buffer pointed to by the <i>Buffer</i> parameter receives a <a href="https://msdn.microsoft.com/library/windows/hardware/ff541559">FILTER_AGGREGATE_BASIC_INFORMATION</a> structure for the minifilter or legacy filter driver. This <i>InformationClass</i> value is available starting with Microsoft Windows Server 2003 SP1 and Windows XP SP2 with filter manager rollup.  For more about the filter manager rollup package for Windows XP SP2, see article 914882, "<a href="http://go.microsoft.com/fwlink/p/?linkid=3100&amp;amp;ID=914882">The filter manager rollup package for Windows XP SP2</a>," in the Microsoft Knowledge Base.</p>
</td>
</tr>
<tr>
<td>
<p><b>FilterAggregateStandardInformation</b></p>
</td>
<td>
<p>The buffer pointed to by the <i>Buffer</i> parameter receives a <a href="https://msdn.microsoft.com/library/windows/hardware/ff541567">FILTER_AGGREGATE_STANDARD_INFORMATION</a> structure for the minifilter or legacy filter driver. This <i>InformationClass</i> value is available starting with Windows Vista.</p>
</td>
</tr>
</table>
<p> </p>
</dd>

### -param <i>Buffer</i> [out]

<dd>
<p>Pointer to a caller-allocated buffer that receives the requested information. The type of the information returned in the buffer is defined by the <i>InformationClass</i> parameter. </p>
</dd>

### -param <i>BufferSize</i> [in]

<dd>
<p>Size, in bytes, of the buffer that the <i>Buffer</i> parameter points to. The caller should set this parameter according to the given <i>InformationClass</i> value. </p>
</dd>

### -param <i>BytesReturned</i> [out]

<dd>
<p>Pointer to a caller-allocated variable that receives the number of bytes returned in the buffer that <i>Buffer</i> points to. If the input value of <i>BufferSize</i> is too small, <b>FltEnumerateFilterInformation</b> returns STATUS_BUFFER_TOO_SMALL and sets this variable to the number of bytes required to store the requested information. This parameter is required and cannot be <b>NULL</b>. </p>
</dd>
</dl>

## -returns
<p><b>FltEnumerateFilterInformation</b> returns STATUS_SUCCESS or an appropriate NTSTATUS value, such as one of the following: </p><dl>
<dt><b>STATUS_BUFFER_TOO_SMALL</b></dt>
</dl><p>The buffer that the <i>Buffer</i> parameter points to is not large enough to store the requested information. This is an error code. </p><dl>
<dt><b>STATUS_FLT_DELETING_OBJECT</b></dt>
</dl><p>A matching minifilter driver was found, but it is being torn down. This is an error code. </p><dl>
<dt><b>STATUS_INVALID_PARAMETER</b></dt>
</dl><p>An invalid value was specified for the <i>InformationClass</i> parameter. For example, if <b>FilterAggregateStandardInformation</b> is specified on operating systems prior to Windows Vista, the routine will return STATUS_INVALID_PARAMETER.  This is an error code.</p><dl>
<dt><b>STATUS_NO_MORE_ENTRIES</b></dt>
</dl><p>There are no more entries in the global list of registered filter drivers. (The value of the <i>Index</i> parameter is greater than or equal to the number of filter drivers.) This is a warning code. </p>

<p> </p>

## -remarks
<p>Starting with Microsoft Windows Server 2003 SP1 and Windows XP SP2 with filter manager rollup, <b>FltEnumerateFilterInformation</b> provides information about file system filter drivers (also called "legacy filters") as well as minifilter drivers. On earlier versions of Windows, <b>FltEnumerateFilterInformation</b> only provides information about minifilter drivers.</p>

<p>The following pseudocode enumerates filter information for all registered filter drivers.</p>

<p><b>FltEnumerateFilterInformation</b> returns information about registered filter drivers, through the <i>Buffer</i> parameter, in order of decreasing distance from the underlying file system.  For example, assume that there are <i>n</i> filter drivers attached above an underlying file system.  Information about the filter driver attached farthest from the file system is returned first (with an <i>Index</i> parameter value of 0).  Information about the next-farthest attached filter driver is returned second (with an <i>Index</i> parameter value of 1), and so on.  Finally, information about the filter driver closest to the file system is returned last (with an <i>Index</i> parameter value of <i>n</i>-1).</p>

<p>To enumerate all registered minifilter drivers, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff542064">FltEnumerateFilters</a>. </p>

<p>To enumerate all registered legacy filter drivers, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff548348">IoEnumerateRegisteredFiltersList</a>. </p>

<p>To enumerate all instances of a given minifilter driver, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff542071">FltEnumerateInstanceInformationByFilter</a>. </p>

<p>To enumerate all minifilter driver instances on a given volume, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff542082">FltEnumerateInstanceInformationByVolume</a>. </p>

<p>To list volume information for all volumes that are known to the Filter Manager, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff542091">FltEnumerateVolumeInformation</a>. </p>

<p>Starting with Microsoft Windows Server 2003 SP1 and Windows XP SP2 with filter manager rollup, <b>FltEnumerateFilterInformation</b> provides information about file system filter drivers (also called "legacy filters") as well as minifilter drivers. On earlier versions of Windows, <b>FltEnumerateFilterInformation</b> only provides information about minifilter drivers.</p>

<p>The following pseudocode enumerates filter information for all registered filter drivers.</p>

<p><b>FltEnumerateFilterInformation</b> returns information about registered filter drivers, through the <i>Buffer</i> parameter, in order of decreasing distance from the underlying file system.  For example, assume that there are <i>n</i> filter drivers attached above an underlying file system.  Information about the filter driver attached farthest from the file system is returned first (with an <i>Index</i> parameter value of 0).  Information about the next-farthest attached filter driver is returned second (with an <i>Index</i> parameter value of 1), and so on.  Finally, information about the filter driver closest to the file system is returned last (with an <i>Index</i> parameter value of <i>n</i>-1).</p>

<p>To enumerate all registered minifilter drivers, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff542064">FltEnumerateFilters</a>. </p>

<p>To enumerate all registered legacy filter drivers, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff548348">IoEnumerateRegisteredFiltersList</a>. </p>

<p>To enumerate all instances of a given minifilter driver, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff542071">FltEnumerateInstanceInformationByFilter</a>. </p>

<p>To enumerate all minifilter driver instances on a given volume, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff542082">FltEnumerateInstanceInformationByVolume</a>. </p>

<p>To list volume information for all volumes that are known to the Filter Manager, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff542091">FltEnumerateVolumeInformation</a>. </p>

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
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Fltkernel.h (include FltKernel.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>FltMgr.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&lt;= APC_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541559">FILTER_AGGREGATE_BASIC_INFORMATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541567">FILTER_AGGREGATE_STANDARD_INFORMATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541587">FILTER_FULL_INFORMATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542064">FltEnumerateFilters</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542071">FltEnumerateInstanceInformationByFilter</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542082">FltEnumerateInstanceInformationByVolume</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542091">FltEnumerateVolumeInformation</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543053">FltGetFilterInformation</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548348">IoEnumerateRegisteredFiltersList</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20FltEnumerateFilterInformation routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>