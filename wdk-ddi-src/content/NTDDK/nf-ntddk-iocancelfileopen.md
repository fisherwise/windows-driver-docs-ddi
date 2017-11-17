---
UID: NF.ntddk.IoCancelFileOpen
title: IoCancelFileOpen
author: windows-driver-content
description: The IoCancelFileOpen routine can be used by a file system filter driver to close a file that has been opened by a file system driver in the filter driver's device stack.
old-location: ifsk\iocancelfileopen.htm
ms.assetid: 249a77b4-c0da-4445-a669-1c4e2ced5b57
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: ifsk
req.header: ntddk.h
req.include-header: Ntddk.h, Ntifs.h, Fltkernel.h
req.target-type: Universal
req.target-min-winverclnt: This routine is available on Microsoft Windows 2000 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IoCancelFileOpen
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
req.irql: PASSIVE_LEVEL
ms.keywords: IoCancelFileOpen
req.iface: 
---

# IoCancelFileOpen function



## -description
<p>The <b>IoCancelFileOpen</b> routine can be used by a file system filter driver to close a file that has been opened by a file system driver in the filter driver's device stack.</p>


## -syntax

````
VOID IoCancelFileOpen(
  _In_ PDEVICE_OBJECT DeviceObject,
  _In_ PFILE_OBJECT   FileObject
);
````


## -parameters
<dl>

### -param <i>DeviceObject</i> [in]

<dd>
<p>Pointer to the top of the device stack immediately below the filter driver's device object.</p>
</dd>

### -param <i>FileObject</i> [in]

<dd>
<p>Pointer to the file object for the file to be closed.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>If a file system filter driver determines that a file-open or file-create request must fail after the lower-level drivers have already completed the request with STATUS_SUCCESS, it can use <b>IoCancelFileOpen</b> to close the file opened by the lower-level drivers.</p>

<p>A successful call to <b>IoCancelFileOpen</b> has the following effect: To minifilters and legacy filters that are above the caller in the file system stack, the create request appears to have failed. To those that are below the caller, the file appears to have been opened (or created) and then closed. </p>

<p>Note that <b>IoCancelFileOpen</b> does not undo any modifications to the file. For example, <b>IoCancelFileOpen</b> does not delete a newly created file or restore a file that was overwritten or superseded to its previous state. </p>

<p>A typical example is as follows:</p>

<p>A filter driver exists between a higher-level filter driver and a lower-level file system driver.</p>

<p>The filter driver passes an IRP_MJ_CREATE request down the device stack to the file system driver, and the file system driver completes the IRP_MJ_CREATE request with status STATUS_SUCCESS.</p>

<p>Before the filter driver completes the create request, it determines that the file must be closed.</p>

<p>The filter driver uses <b>IoCancelFileOpen</b> to close the file that was opened by the file system driver. </p>

<p>After calling <b>IoCancelFileOpen</b>, the filter driver should complete the create request with an appropriate error code such as STATUS_UNSUCCESSFUL or STATUS_ACCESS_DENIED. In addition, it should set the <b>Irp-&gt;IoStatus.Information</b> field to zero. </p>

<p><b>IoCancelFileOpen</b> must be called before any handles are created for the file. Callers can check the <b>Flags</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff545834">FILE_OBJECT</a> structure that the <i>FileObject</i> parameter points to. If the FO_HANDLE_CREATED flag is set, this means that one or more handles have been created for the file, so it is not safe to call <b>IoCancelFileOpen</b>. </p>

<p><b>IoCancelFileOpen</b> sets the FO_FILE_OPEN_CANCELLED flag in the <b>Flags</b> member of the file object that <i>FileObject</i> points to. This flag indicates that the IRP_MJ_CREATE request has been canceled, and an IRP_MJ_CLOSE request will be issued for this file object. Once the create operation has been canceled, it cannot be reissued - that is, STATUS_REPARSE cannot be returned by the legacy filter driver if it has called the <b>IoCreateFileOpen</b> routine.</p>

<p>Minifilters should use <a href="https://msdn.microsoft.com/library/windows/hardware/ff541784">FltCancelFileOpen</a> instead of <b>IoCancelFileOpen</b>. </p>

<p>If a file system filter driver determines that a file-open or file-create request must fail after the lower-level drivers have already completed the request with STATUS_SUCCESS, it can use <b>IoCancelFileOpen</b> to close the file opened by the lower-level drivers.</p>

<p>A successful call to <b>IoCancelFileOpen</b> has the following effect: To minifilters and legacy filters that are above the caller in the file system stack, the create request appears to have failed. To those that are below the caller, the file appears to have been opened (or created) and then closed. </p>

<p>Note that <b>IoCancelFileOpen</b> does not undo any modifications to the file. For example, <b>IoCancelFileOpen</b> does not delete a newly created file or restore a file that was overwritten or superseded to its previous state. </p>

<p>A typical example is as follows:</p>

<p>A filter driver exists between a higher-level filter driver and a lower-level file system driver.</p>

<p>The filter driver passes an IRP_MJ_CREATE request down the device stack to the file system driver, and the file system driver completes the IRP_MJ_CREATE request with status STATUS_SUCCESS.</p>

<p>Before the filter driver completes the create request, it determines that the file must be closed.</p>

<p>The filter driver uses <b>IoCancelFileOpen</b> to close the file that was opened by the file system driver. </p>

<p>After calling <b>IoCancelFileOpen</b>, the filter driver should complete the create request with an appropriate error code such as STATUS_UNSUCCESSFUL or STATUS_ACCESS_DENIED. In addition, it should set the <b>Irp-&gt;IoStatus.Information</b> field to zero. </p>

<p><b>IoCancelFileOpen</b> must be called before any handles are created for the file. Callers can check the <b>Flags</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff545834">FILE_OBJECT</a> structure that the <i>FileObject</i> parameter points to. If the FO_HANDLE_CREATED flag is set, this means that one or more handles have been created for the file, so it is not safe to call <b>IoCancelFileOpen</b>. </p>

<p><b>IoCancelFileOpen</b> sets the FO_FILE_OPEN_CANCELLED flag in the <b>Flags</b> member of the file object that <i>FileObject</i> points to. This flag indicates that the IRP_MJ_CREATE request has been canceled, and an IRP_MJ_CLOSE request will be issued for this file object. Once the create operation has been canceled, it cannot be reissued - that is, STATUS_REPARSE cannot be returned by the legacy filter driver if it has called the <b>IoCreateFileOpen</b> routine.</p>

<p>Minifilters should use <a href="https://msdn.microsoft.com/library/windows/hardware/ff541784">FltCancelFileOpen</a> instead of <b>IoCancelFileOpen</b>. </p>

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
<p>This routine is available on Microsoft Windows 2000 and later. </p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntddk.h (include Ntddk.h, Ntifs.h, or Fltkernel.h)</dt>
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
<p>PASSIVE_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541784">FltCancelFileOpen</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544311">FltReissueSynchronousIo</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548418">IoCreateFile</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548283">IoCreateFileEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548289">IoCreateFileSpecifyDeviceObjectHint</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550720">IRP_MJ_CLOSE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548630">IRP_MJ_CREATE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff566424">ZwCreateFile</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567011">ZwOpenFile</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20IoCancelFileOpen routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>