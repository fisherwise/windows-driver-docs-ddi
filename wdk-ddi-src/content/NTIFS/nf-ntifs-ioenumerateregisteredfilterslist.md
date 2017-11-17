---
UID: NF.ntifs.IoEnumerateRegisteredFiltersList
title: IoEnumerateRegisteredFiltersList
author: windows-driver-content
description: The IoEnumerateRegisteredFiltersList routine enumerates the file system filter drivers that have registered with the system.
old-location: ifsk\ioenumerateregisteredfilterslist.htm
ms.assetid: 7ac67110-bc92-457a-88f4-a21f2fa38174
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: ifsk
req.header: ntifs.h
req.include-header: Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: This routine is available on Update Rollup for Windows 2000 Service Pack 4 (SP4) and on Windows Server 2003 Service Pack 1 (SP1) and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IoEnumerateRegisteredFiltersList
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: <= APC_LEVEL
ms.keywords: IoEnumerateRegisteredFiltersList
req.iface: 
---

# IoEnumerateRegisteredFiltersList function



## -description
<p>The <b>IoEnumerateRegisteredFiltersList</b> routine enumerates the file system filter drivers that have registered with the system. </p>


## -syntax

````
NTSTATUS IoEnumerateRegisteredFiltersList(
  _Out_ PDRIVER_OBJECT *DriverObjectList,
  _In_  ULONG          DriverObjectListSize,
  _Out_ PULONG         ActualNumberDriverObjects
);
````


## -parameters
<dl>

### -param <i>DriverObjectList</i> [out]

<dd>
<p>A pointer to a caller-allocated array that receives the driver object pointers. This parameter is optional and can be <b>NULL</b>. (See the following Remarks section.) </p>
</dd>

### -param <i>DriverObjectListSize</i> [in]

<dd>
<p>Size, in bytes, of the <i>DriverObjectList</i> array. Can be zero. (See the following Remarks section.) </p>
</dd>

### -param <i>ActualNumberDriverObjects</i> [out]

<dd>
<p>Actual number of driver objects found. Note that if the array at <i>DriverObjectList</i> is too small, the number of driver object pointers that are copied into the array will be less than <i>ActualNumberDriverObjects</i>. </p>
</dd>
</dl>

## -returns
<p><b>IoEnumerateRegisteredFiltersList</b> can return one of the following: </p><dl>
<dt><b>STATUS_SUCCESS</b></dt>
</dl><p>The call to <b>IoEnumerateRegisteredFiltersList</b> was successful. </p><dl>
<dt><b>STATUS_BUFFER_TOO_SMALL</b></dt>
</dl><p>The array at <i>DriverObjectList</i> is too small to hold the entire driver object list. In this case, <b>IoEnumerateRegisteredFiltersList</b> copies as many driver object pointers into the array as possible. </p>

<p> </p>

## -remarks
<p>A file system filter driver calls <b>IoEnumerateRegisteredFiltersList</b> to obtain an array of pointers to the driver objects for all file system filter drivers that have called <a href="https://msdn.microsoft.com/library/windows/hardware/ff548499">IoRegisterFsRegistrationChange</a>. </p>

<p>The filter drivers are enumerated in order of decreasing distance from the base file system. The first element (index zero) in the <i>DriverObjectList</i> array represents the filter that is attached farthest from the file system. The second entry is for the next-farthest filter, and so on. The last entry in the array is for the filter that is closest to the base file system. </p>

<p><b>IoEnumerateRegisteredFiltersList</b> enumerates only file system filter drivers (also called "legacy filters"). It does not enumerate minifilters. To enumerate both minifilters and legacy filters, or only minifilters, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff542060">FltEnumerateFilterInformation</a>. </p>

<p>The filter driver typically calls <b>IoEnumerateRegisteredFiltersList</b> twice: once to get the number of driver objects in the list, and once to get the driver object list itself. In the first call, the caller should set the <i>DriverObjectList</i> parameter to <b>NULL</b> and <i>DriverObjectListSize</i> to zero. In the second call, <i>DriverObjectList</i> should contain a pointer to an appropriately-sized pointer array, and <i>DriverObjectListSize</i> should contain the size, in bytes, of that array. </p>

<p><b>IoEnumerateRegisteredFiltersList</b> increments the reference count on every driver object in the list pointed to by <i>DriverObjectList</i>. Thus every successful call to <b>IoEnumerateRegisteredFiltersList</b> must be matched by a subsequent call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff557724">ObDereferenceObject</a>for each driver object in the list. Failure to do so prevents the system from freeing or deleting these driver objects because of an outstanding reference count. </p>

<p>Minifilters should call <a href="https://msdn.microsoft.com/library/windows/hardware/ff542060">FltEnumerateFilterInformation</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff542064">FltEnumerateFilters</a> instead of <b>IoEnumerateRegisteredFiltersList</b>. </p>

<p>A file system filter driver calls <b>IoEnumerateRegisteredFiltersList</b> to obtain an array of pointers to the driver objects for all file system filter drivers that have called <a href="https://msdn.microsoft.com/library/windows/hardware/ff548499">IoRegisterFsRegistrationChange</a>. </p>

<p>The filter drivers are enumerated in order of decreasing distance from the base file system. The first element (index zero) in the <i>DriverObjectList</i> array represents the filter that is attached farthest from the file system. The second entry is for the next-farthest filter, and so on. The last entry in the array is for the filter that is closest to the base file system. </p>

<p><b>IoEnumerateRegisteredFiltersList</b> enumerates only file system filter drivers (also called "legacy filters"). It does not enumerate minifilters. To enumerate both minifilters and legacy filters, or only minifilters, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff542060">FltEnumerateFilterInformation</a>. </p>

<p>The filter driver typically calls <b>IoEnumerateRegisteredFiltersList</b> twice: once to get the number of driver objects in the list, and once to get the driver object list itself. In the first call, the caller should set the <i>DriverObjectList</i> parameter to <b>NULL</b> and <i>DriverObjectListSize</i> to zero. In the second call, <i>DriverObjectList</i> should contain a pointer to an appropriately-sized pointer array, and <i>DriverObjectListSize</i> should contain the size, in bytes, of that array. </p>

<p><b>IoEnumerateRegisteredFiltersList</b> increments the reference count on every driver object in the list pointed to by <i>DriverObjectList</i>. Thus every successful call to <b>IoEnumerateRegisteredFiltersList</b> must be matched by a subsequent call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff557724">ObDereferenceObject</a>for each driver object in the list. Failure to do so prevents the system from freeing or deleting these driver objects because of an outstanding reference count. </p>

<p>Minifilters should call <a href="https://msdn.microsoft.com/library/windows/hardware/ff542060">FltEnumerateFilterInformation</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff542064">FltEnumerateFilters</a> instead of <b>IoEnumerateRegisteredFiltersList</b>. </p>

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
<p>This routine is available on Update Rollup for Windows 2000 Service Pack 4 (SP4) and on Windows Server 2003 Service Pack 1 (SP1) and later. </p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntifs.h (include Ntifs.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>NtosKrnl.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>NtosKrnl.exe</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542060">FltEnumerateFilterInformation</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542064">FltEnumerateFilters</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548499">IoRegisterFsRegistrationChange</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff557724">ObDereferenceObject</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20IoEnumerateRegisteredFiltersList routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>