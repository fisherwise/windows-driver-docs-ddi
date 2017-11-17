---
UID: NF.wdm.IoSetShareAccess
title: IoSetShareAccess
author: windows-driver-content
description: The IoSetShareAccess routine sets the access rights for sharing the given file object.
old-location: kernel\iosetshareaccess.htm
ms.assetid: a686ea04-8a6b-4c4b-be06-73a75c4fc87d
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: Available starting with Windows 2000.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IoSetShareAccess
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: IrqlIoPassive5, HwStorPortProhibitedDDIs
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: PASSIVE_LEVEL
ms.keywords: IoSetShareAccess
req.iface: 
req.product: Windows 10 or later.
---

# IoSetShareAccess function



## -description
<p>The <b>IoSetShareAccess</b> routine sets the access rights for sharing the given file object.</p>


## -syntax

````
VOID IoSetShareAccess(
  _In_    ACCESS_MASK   DesiredAccess,
  _In_    ULONG         DesiredShareAccess,
  _Inout_ PFILE_OBJECT  FileObject,
  _Out_   PSHARE_ACCESS ShareAccess
);
````


## -parameters
<dl>

### -param <i>DesiredAccess</i> [in]

<dd>
<p>Specifies an <a href="https://msdn.microsoft.com/library/windows/hardware/ff540466">ACCESS_MASK</a> value that represents the type of access requested for the <i>FileObject</i>. See <a href="https://msdn.microsoft.com/library/windows/hardware/ff548418">IoCreateFile</a> for a complete list of system-defined <i>DesiredAccess </i>flags.</p>
</dd>

### -param <i>DesiredShareAccess</i> [in]

<dd>
<p>Specifies the type of share access to be set for the file object. This value can be zero, or any combination of the following:</p>
<dl>
<dd>
<p>FILE_SHARE_READ</p>
</dd>
<dd>
<p>FILE_SHARE_WRITE</p>
</dd>
<dd>
<p>FILE_SHARE_DELETE</p>
</dd>
</dl>
</dd>

### -param <i>FileObject</i> [in, out]

<dd>
<p>Pointer to the file object whose share access is being set or reset.</p>
</dd>

### -param <i>ShareAccess</i> [out]

<dd>
<p>Pointer to the SHARE_ACCESS structure associated with <i>FileObject</i>. Drivers should treat this structure as opaque. </p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>Only highest-level kernel-mode drivers should call this routine. The call must occur in the context of the first thread that attempts to open the <i>FileObject</i>.</p>

<p>This routine sets the access and share access information when the <i>FileObject</i> is first opened. It returns a pointer to the common share-access data structure associated with <i>FileObject</i>. Callers should save this pointer for later use when updating the access or closing the file.</p>

<p>Generally, file system drivers (FSDs) are most likely to call this routine. However, other highest-level drivers can call <b>IoSetShareAccess</b> to control the kind of access allowed to a driver-created device object associated with the given <i>FileObject</i>.</p>

<p><b>IoSetShareAccess</b> is not an atomic operation. Therefore, drivers calling this routine must protect the shared file object passed to <b>IoSetShareAccess </b>by means of some kind of lock, such as a mutex or a resource lock, in order to prevent corruption of the shared access counts.</p>

<p>Only highest-level kernel-mode drivers should call this routine. The call must occur in the context of the first thread that attempts to open the <i>FileObject</i>.</p>

<p>This routine sets the access and share access information when the <i>FileObject</i> is first opened. It returns a pointer to the common share-access data structure associated with <i>FileObject</i>. Callers should save this pointer for later use when updating the access or closing the file.</p>

<p>Generally, file system drivers (FSDs) are most likely to call this routine. However, other highest-level drivers can call <b>IoSetShareAccess</b> to control the kind of access allowed to a driver-created device object associated with the given <i>FileObject</i>.</p>

<p><b>IoSetShareAccess</b> is not an atomic operation. Therefore, drivers calling this routine must protect the shared file object passed to <b>IoSetShareAccess </b>by means of some kind of lock, such as a mutex or a resource lock, in order to prevent corruption of the shared access counts.</p>

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
<p>Available starting with Windows 2000.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdm.h (include Wdm.h, Ntddk.h, or Ntifs.h)</dt>
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
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547796">IrqlIoPassive5</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh454220">HwStorPortProhibitedDDIs</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff540466">ACCESS_MASK</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548418">IoCreateFile</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548283">IoCreateFileEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548341">IoCheckShareAccess</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549231">IoGetFileObjectGenericMapping</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549277">IoGetRelatedDeviceObject</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549587">IoRemoveShareAccess</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550412">IoUpdateShareAccess</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20IoSetShareAccess routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>