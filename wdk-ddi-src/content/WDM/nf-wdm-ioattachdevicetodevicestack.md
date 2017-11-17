---
UID: NF.wdm.IoAttachDeviceToDeviceStack
title: IoAttachDeviceToDeviceStack
author: windows-driver-content
description: The IoAttachDeviceToDeviceStack routine attaches the caller's device object to the highest device object in the chain and returns a pointer to the previously highest device object.
old-location: kernel\ioattachdevicetodevicestack.htm
ms.assetid: 6377f980-dd56-4bef-91e7-7557866132d6
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
req.alt-api: IoAttachDeviceToDeviceStack
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: AddDevice, PnpSameDeviceObject, HwStorPortProhibitedDDIs
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: <= DISPATCH_LEVEL
ms.keywords: IoAttachDeviceToDeviceStack
req.iface: 
req.product: Windows 10 or later.
---

# IoAttachDeviceToDeviceStack function



## -description
<p>The <b>IoAttachDeviceToDeviceStack</b> routine attaches the caller's device object to the highest device object in the chain and returns a pointer to the previously highest device object.</p>


## -syntax

````
PDEVICE_OBJECT IoAttachDeviceToDeviceStack(
  _In_ PDEVICE_OBJECT SourceDevice,
  _In_ PDEVICE_OBJECT TargetDevice
);
````


## -parameters
<dl>

### -param <i>SourceDevice</i> [in]

<dd>
<p>Pointer to the caller-created device object.</p>
</dd>

### -param <i>TargetDevice</i> [in]

<dd>
<p>Pointer to another driver's device object, such as a pointer returned by a preceding call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff549198">IoGetDeviceObjectPointer</a>.</p>
</dd>
</dl>

## -returns
<p><b>IoAttachDeviceToDeviceStack</b> returns a pointer to the device object to which the <i>SourceDevice</i> was attached. The returned device object pointer can differ from <i>TargetDevice</i> if <i>TargetDevice</i> had additional drivers layered on top of it.</p>

<p><b>IoAttachDeviceToDeviceStack</b> returns <b>NULL</b> if it could not attach the device object because, for example, the target device was being unloaded.</p>

## -remarks
<p><b>IoAttachDeviceToDeviceStack</b> establishes layering between drivers so that the same IRPs are sent to each driver in the chain.</p>

<p>An intermediate driver can use this routine during initialization to attach its own device object to another driver's device object. Subsequent I/O requests sent to <i>TargetDevice</i> are sent first to the intermediate driver.</p>

<p>This routine sets the <b>AlignmentRequirement</b> in <i>SourceDevice</i>  to the value in the next-lower device object and sets the <b>StackSize</b> to the value in the next-lower-object plus one.</p>

<p>A driver writer must take care to call this routine <u>before</u> any drivers that must layer on top of their driver. <b>IoAttachDeviceToDeviceStack</b> attaches <i>SourceDevice</i> to the highest device object currently layered in the chain and has no way to determine whether drivers are being layered in the correct order.</p>

<p>A driver that acquired a pointer to the target device by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff549198">IoGetDeviceObjectPointer</a> should call <a href="https://msdn.microsoft.com/library/windows/hardware/ff557724">ObDereferenceObject</a> with the file object pointer that was returned by <b>IoGetDeviceObjectPointer</b> to release its reference to the file object before it detaches its own device object, for example, when such a higher-level driver is unloaded.</p>

<p><b>IoAttachDeviceToDeviceStack</b> establishes layering between drivers so that the same IRPs are sent to each driver in the chain.</p>

<p>An intermediate driver can use this routine during initialization to attach its own device object to another driver's device object. Subsequent I/O requests sent to <i>TargetDevice</i> are sent first to the intermediate driver.</p>

<p>This routine sets the <b>AlignmentRequirement</b> in <i>SourceDevice</i>  to the value in the next-lower device object and sets the <b>StackSize</b> to the value in the next-lower-object plus one.</p>

<p>A driver writer must take care to call this routine <u>before</u> any drivers that must layer on top of their driver. <b>IoAttachDeviceToDeviceStack</b> attaches <i>SourceDevice</i> to the highest device object currently layered in the chain and has no way to determine whether drivers are being layered in the correct order.</p>

<p>A driver that acquired a pointer to the target device by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff549198">IoGetDeviceObjectPointer</a> should call <a href="https://msdn.microsoft.com/library/windows/hardware/ff557724">ObDereferenceObject</a> with the file object pointer that was returned by <b>IoGetDeviceObjectPointer</b> to release its reference to the file object before it detaches its own device object, for example, when such a higher-level driver is unloaded.</p>

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
<p>&lt;= DISPATCH_LEVEL</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff540521">AddDevice</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff550411">PnpSameDeviceObject</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh454220">HwStorPortProhibitedDDIs</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548294">IoAttachDevice</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549087">IoDetachDevice</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff557724">ObDereferenceObject</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549198">IoGetDeviceObjectPointer</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20IoAttachDeviceToDeviceStack routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>