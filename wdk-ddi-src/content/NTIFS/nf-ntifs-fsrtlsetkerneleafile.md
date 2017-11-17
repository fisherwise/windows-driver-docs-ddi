---
UID: NF.ntifs.FsRtlSetKernelEaFile
title: FsRtlSetKernelEaFile
author: windows-driver-content
description: The routine FsRtlQueryKernelEaFile is used to set, modify and/or delete extended attribute (EA) values for a file and synchronously wait for it to complete, returning a result.
old-location: ifsk\fsrtlsetkerneleafile.htm
ms.assetid: E5EA2E40-2CC3-4C7B-8BCC-4793F76ECBAD
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: ifsk
req.header: ntifs.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows 8
req.target-min-winversvr: Windows Server 2012
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FsRtlSetKernelEaFile
req.alt-loc: ntifs.h
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
ms.keywords: FsRtlSetKernelEaFile
req.iface: 
---

# FsRtlSetKernelEaFile function



## -description
<p>The routine <b>FsRtlQueryKernelEaFile</b> is used to set, modify and/or delete extended attribute (EA) values for a file and synchronously wait
    for it to complete, returning a result.  It sets the <b>IRP_MN_KERNEL</b> minor
    code which allows this API to set SecureEAs.  This allows the caller to do
    this by FileObject instead of a handle.</p>


## -syntax

````
NTSTATUS FsRtlSetKernelEaFile(
  _In_ PFILE_OBJECT         FileObject,
  _In_ bcount(Length) PVOID EaBuffer,
  _In_ ULONG                Length
);
````


## -parameters
<dl>

### -param <i>FileObject</i> [in]

<dd>
<p>A pointer to a <b>FileObject</b> to send the QueryEA request to.</p>
</dd>

### -param <i>EaBuffer</i> [in]

<dd>
<p>A pointer to a caller-supplied, <a href="https://msdn.microsoft.com/library/windows/hardware/ff545793">FILE_FULL_EA_INFORMATION</a>-structured input buffer that contains the extended attribute values to be set</p>
</dd>

### -param <i>Length</i> [in]

<dd>
<p>Specifies the length of the EA buffer.</p>
</dd>
</dl>

## -returns
<p>The routine <b>FsRtlSetKernelEaFile</b> receives the status of the operation and returns one of the status codes:</p><dl>
<dt><b>STATUS_EA_LIST_INCONSISTENT </b></dt>
</dl><p>The <b>EaList</b> parameter is not formatted correctly.</p><dl>
<dt><b>STATUS_EAS_NOT_SUPPORTED  </b></dt>
</dl><p>The file system does not support extended attributes.</p><dl>
<dt><b>STATUS_INSUFFICIENT_RESOURCES</b></dt>
</dl><p>The  I/O request packet (IRP) could not be allocated for this request.</p><dl>
<dt><b>STATUS_INTERMIXED_KERNEL_EA_OPERATION</b></dt>
</dl><p>The request cannot intermix normal and kernel EA’s in the same call.</p><dl>
<dt><b>STATUS_INVALID_DEVICE_REQUEST</b></dt>
</dl><p>The request failed as it was a direct device open.</p><dl>
<dt><b>STATUS_SUCCESS</b></dt>
</dl><p>The request was successful. </p>

<p> </p>

## -remarks
<p> This routine assumes all passed in buffers are from kernel mode.</p>

<p>One or more Kernel EA’s may be set, modified and/or deleted in a single call to <b>FsRtlSetKernelEaFile</b>. Normal EA’s may also be set using the <b>FsRtlSetKernelEaFile</b> function.
You delete EA’s by specifying an <b>EAName</b> with an <b>EaValueLength</b> of zero.  You can intermix inserting new, modifying existing, or removing EA’s in a single call.</p>

<p> This routine assumes all passed in buffers are from kernel mode.</p>

<p>One or more Kernel EA’s may be set, modified and/or deleted in a single call to <b>FsRtlSetKernelEaFile</b>. Normal EA’s may also be set using the <b>FsRtlSetKernelEaFile</b> function.
You delete EA’s by specifying an <b>EAName</b> with an <b>EaValueLength</b> of zero.  You can intermix inserting new, modifying existing, or removing EA’s in a single call.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 8</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>Windows Server 2012</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntifs.h</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/B57BC3A4-6116-48EA-905A-CFA7AC0A5E8F">FsRtlQueryKernelEaFile</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff961907">ZwQueryEaFile</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff961908">ZwSetEaFile</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20FsRtlSetKernelEaFile routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>