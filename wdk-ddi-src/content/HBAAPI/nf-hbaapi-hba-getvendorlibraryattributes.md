---
UID: NF.hbaapi.HBA_GetVendorLibraryAttributes
title: HBA_GetVendorLibraryAttributes
author: windows-driver-content
description: The HBA_GetVendorLibraryAttributes routine retrieves the vendor-specific attributes of the fibre channel HBA API library.
old-location: storage\hba_getvendorlibraryattributes.htm
ms.assetid: 43c55364-1f73-4413-99fb-27c85600d7a6
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: Storage
req.header: hbaapi.h
req.include-header: Hbaapi.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: HBA_GetVendorLibraryAttributes
req.alt-loc: Hbaapi.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Hbaapi.lib
req.dll: Hbaapi.dll
req.irql: 
ms.keywords: HBA_GetVendorLibraryAttributes
req.iface: 
---

# HBA_GetVendorLibraryAttributes function



## -description
<p>The <b>HBA_GetVendorLibraryAttributes</b> routine retrieves the vendor-specific attributes of the fibre channel HBA API library.</p>


## -syntax

````
HBA_UINT32 HBA_API HBA_GetVendorLibraryAttributes(
  _In_  HBA_UINT32            AdapterIndex,
  _Out_ HBA_LIBRARYATTRIBUTES *Attributes
);
````


## -parameters
<dl>

### -param <i>AdapterIndex</i> [in]

<dd>
<p>Contains an adapter index that identifies which library to query. Each library is associated with one or more HBAs. This routine uses an index to identify the HBA so that the caller does not have to open the adapter to obtain a name or handle. The HBA API library can be associated with more than one HBA, so the same library attributes might be retrieved for different HBAs. The adapter index must be within the range of values returned by <a href="https://msdn.microsoft.com/library/windows/hardware/ff556101">HBA_GetNumberOfAdapters</a>. </p>
</dd>

### -param <i>Attributes</i> [out]

<dd>
<p>Pointer, on return, to a structure of type <a href="https://msdn.microsoft.com/library/windows/hardware/ff556119">HBA_LibraryAttributes</a> that holds the attributes of the library associated with the adapter referenced by <i>AdapterIndex</i>.</p>
</dd>
</dl>

## -returns
<p>The <b>HBA_GetVendorLibraryAttributes</b> routine returns a value that indicates the version of the specification with which the library is compliant. A value of 1 indicates version 1 of the specification. A value of 2 indicates version 2 of the specification. All other values are reserved until the future versions of the specification are published.</p>

## -remarks
<p>The <b>HBA_GetVendorLibraryAttributes</b> routine, as defined by the T11 committee's <i>Fibre Channel HBA API</i> specification, retrieves information about a vendor-supplied HBA API library, and the related routine <a href="https://msdn.microsoft.com/library/windows/hardware/ff556115">HBA_GetWrapperLibraryAttributes</a> reports the characteristics of a system-supplied wrapper library that works with the vendor library to provide the fibre channel HBA API. </p>

<p>In particular, the <b>HBA_GetVendorLibraryAttributes</b> routine allows the caller to determine whether a compatible library is installed.</p>

<p>Microsoft supplies both libraries, so currently they return the same information. </p>

<p>The <b>HBA_GetVendorLibraryAttributes</b> routine, as defined by the T11 committee's <i>Fibre Channel HBA API</i> specification, retrieves information about a vendor-supplied HBA API library, and the related routine <a href="https://msdn.microsoft.com/library/windows/hardware/ff556115">HBA_GetWrapperLibraryAttributes</a> reports the characteristics of a system-supplied wrapper library that works with the vendor library to provide the fibre channel HBA API. </p>

<p>In particular, the <b>HBA_GetVendorLibraryAttributes</b> routine allows the caller to determine whether a compatible library is installed.</p>

<p>Microsoft supplies both libraries, so currently they return the same information. </p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt>Desktop</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Hbaapi.h (include Hbaapi.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Hbaapi.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>Hbaapi.dll</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff556101">HBA_GetNumberOfAdapters</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff556115">HBA_GetWrapperLibraryAttributes</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff556119">HBA_LibraryAttributes</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20HBA_GetVendorLibraryAttributes routine%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>