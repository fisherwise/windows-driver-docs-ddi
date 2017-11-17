---
UID: NF.fltkernel.FltGetVolumeGuidName
title: FltGetVolumeGuidName
author: windows-driver-content
description: The FltGetVolumeGuidName routine returns the volume name for a given volume, in volume globally unique identifier (GUID) format.
old-location: ifsk\fltgetvolumeguidname.htm
ms.assetid: 911d8b07-1313-4c4b-8d16-188857943327
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: ifsk
req.header: fltkernel.h
req.include-header: Fltkernel.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FltGetVolumeGuidName
req.alt-loc: fltmgr.sys
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: FltMgr.lib
req.dll: Fltmgr.sys
req.irql: PASSIVE_LEVEL
ms.keywords: FltGetVolumeGuidName
req.iface: 
---

# FltGetVolumeGuidName function



## -description
<p>The <b>FltGetVolumeGuidName</b> routine returns the volume name for a given volume, in volume globally unique identifier (GUID) format. </p>


## -syntax

````
NTSTATUS FltGetVolumeGuidName(
  _In_      PFLT_VOLUME     Volume,
  _Out_     PUNICODE_STRING VolumeGuidName,
  _Out_opt_ PULONG          BufferSizeNeeded
);
````


## -parameters
<dl>

### -param <i>Volume</i> [in]

<dd>
<p>Opaque pointer for the volume. Must be a local file system volume. This parameter is required and cannot be <b>NULL</b>. </p>
</dd>

### -param <i>VolumeGuidName</i> [out]

<dd>
<p>Pointer to a caller-allocated <a href="https://msdn.microsoft.com/library/windows/hardware/ff564879">UNICODE_STRING</a> structure that receives the volume's GUID name. This parameter is required and cannot be <b>NULL</b>. </p>
</dd>

### -param <i>BufferSizeNeeded</i> [out, optional]

<dd>
<p>Pointer to a caller-allocated variable that receives the size, in bytes, of the requested volume GUID name. If <b>FltGetVolumeGuidName</b> returns STATUS_BUFFER_TOO_SMALL, you can use the value of the variable to determine the required size for the structure that the <i>VolumeGuidName</i> parameter points to. This parameter is optional and can be <b>NULL</b>. </p>
</dd>
</dl>

## -returns
<p><b>FltGetVolumeGuidName</b> returns STATUS_SUCCESS or an appropriate NTSTATUS value, such as one of the following: </p><dl>
<dt><b>STATUS_BUFFER_TOO_SMALL</b></dt>
</dl><p>The buffer pointed to by the <i>VolumeGuidName</i> parameter is too small to hold the volume GUID. If the caller provides a non-<b>NULL</b> value for the <i>BufferSizeNeeded</i> parameter, this parameter receives the required buffer size. This is an error code. </p><dl>
<dt><b>STATUS_INSUFFICIENT_RESOURCES</b></dt>
</dl><p><b>FltGetVolumeGuidName</b> encountered a pool allocation failure. This is an error code. </p><dl>
<dt><b>STATUS_INVALID_DEVICE_REQUEST</b></dt>
</dl><p>The <i>Volume</i> parameter is a handle for a network volume. This is an error code. </p><dl>
<dt><b>STATUS_FLT_VOLUME_NOT_FOUND</b></dt>
</dl><p>No matching volume was found. This is an error code. </p>

<p> </p>

## -remarks
<p>The returned volume GUID name is expressed in the following format: </p>

<p><b>\??\Volume{</b><i>GUID</i><b>}</b></p>

<p>where <i>GUID</i> is a globally unique identifier that identifies the volume. </p>

<p>This format, which is the same as that used by the mount manager, is described in <a href="NULL">Supporting Mount Manager Requests in a Storage Class Driver</a>. </p>

<p><b>FltGetVolumeGuidName</b> cannot safely be called from a pre-mount or post-mount callback. It cannot safely be called because even when the post-mount callback is called, the mount processing has not been completed by the I/O manager, and this causes a deadlock with the mount manager in certain cases.</p>

<p>On Windows Vista and later, a minifilter driver can safely call <b>FltGetVolumeGuidName</b> from its <i>InstanceSetupCallback</i> routine (<a href="https://msdn.microsoft.com/library/windows/hardware/ff551096">PFLT_INSTANCE_SETUP_CALLBACK</a>) because the callback is called on the first I/O operation for a new volume after all of the mount processing is completed. </p>

<p>On Windows operating systems earlier than Windows Vista, <b>FltGetVolumeGuidName</b> cannot safely be called from an <i>InstanceSetupCallback</i> routine because the mount manager might issue a file I/O operation while holding a lock, which can cause a deadlock. </p>

<p>It is important to note that the volume GUID is not the same as the volume object ID. The <i>volume GUID</i>, or <i>unique volume name</i>, is a file system-independent value; it is assigned to the underlying storage volume by the mount manager. The <i>volume object ID</i> is assigned to the file system volume by the file system. </p>

<p>To get the volume object ID for a volume, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff567070">ZwQueryVolumeInformationFile</a>, specifying <b>FileFsObjectIdInformation</b> for the <i>FsInformationClass</i> parameter. </p>

<p><b>FltGetVolumeGuidName</b> is roughly equivalent to the Win32 <b>GetVolumeNameForVolumeMountPoint</b> function. (<b>GetVolumeNameForVolumeMountPoint</b> is documented in the Microsoft Windows SDK.) </p>

<p>The returned volume GUID name is expressed in the following format: </p>

<p><b>\??\Volume{</b><i>GUID</i><b>}</b></p>

<p>where <i>GUID</i> is a globally unique identifier that identifies the volume. </p>

<p>This format, which is the same as that used by the mount manager, is described in <a href="NULL">Supporting Mount Manager Requests in a Storage Class Driver</a>. </p>

<p><b>FltGetVolumeGuidName</b> cannot safely be called from a pre-mount or post-mount callback. It cannot safely be called because even when the post-mount callback is called, the mount processing has not been completed by the I/O manager, and this causes a deadlock with the mount manager in certain cases.</p>

<p>On Windows Vista and later, a minifilter driver can safely call <b>FltGetVolumeGuidName</b> from its <i>InstanceSetupCallback</i> routine (<a href="https://msdn.microsoft.com/library/windows/hardware/ff551096">PFLT_INSTANCE_SETUP_CALLBACK</a>) because the callback is called on the first I/O operation for a new volume after all of the mount processing is completed. </p>

<p>On Windows operating systems earlier than Windows Vista, <b>FltGetVolumeGuidName</b> cannot safely be called from an <i>InstanceSetupCallback</i> routine because the mount manager might issue a file I/O operation while holding a lock, which can cause a deadlock. </p>

<p>It is important to note that the volume GUID is not the same as the volume object ID. The <i>volume GUID</i>, or <i>unique volume name</i>, is a file system-independent value; it is assigned to the underlying storage volume by the mount manager. The <i>volume object ID</i> is assigned to the file system volume by the file system. </p>

<p>To get the volume object ID for a volume, call <a href="https://msdn.microsoft.com/library/windows/hardware/ff567070">ZwQueryVolumeInformationFile</a>, specifying <b>FileFsObjectIdInformation</b> for the <i>FsInformationClass</i> parameter. </p>

<p><b>FltGetVolumeGuidName</b> is roughly equivalent to the Win32 <b>GetVolumeNameForVolumeMountPoint</b> function. (<b>GetVolumeNameForVolumeMountPoint</b> is documented in the Microsoft Windows SDK.) </p>

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
<dt>Fltkernel.h (include Fltkernel.h)</dt>
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
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>Fltmgr.sys</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff540274">FILE_FS_OBJECTID_INFORMATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551096">PFLT_INSTANCE_SETUP_CALLBACK</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564879">UNICODE_STRING</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567070">ZwQueryVolumeInformationFile</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20FltGetVolumeGuidName routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>