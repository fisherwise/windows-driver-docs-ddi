---
UID: NF.wdm.IoReuseIrp
title: IoReuseIrp
author: windows-driver-content
description: The IoReuseIrp routine reinitializes an IRP so that it can be reused.
old-location: kernel\ioreuseirp.htm
ms.assetid: 18ad2c76-110f-45a9-986b-67e7c81f256f
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: Ntddk.h
req.target-type: Universal
req.target-min-winverclnt: Available starting with Windows 2000.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IoReuseIrp
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: IoReuseIrp, IoReuseIrp2, HwStorPortProhibitedDDIs
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: <=DISPATCH_LEVEL
ms.keywords: IoReuseIrp
req.iface: 
req.product: Windows 10 or later.
---

# IoReuseIrp function



## -description
<p>The <b>IoReuseIrp</b> routine reinitializes an IRP so that it can be reused.</p>


## -syntax

````
VOID IoReuseIrp(
  _Inout_ PIRP     Irp,
  _In_    NTSTATUS Status
);
````


## -parameters
<dl>

### -param <i>Irp</i> [in, out]

<dd>
<p>Pointer to the IRP to be reinitialized for reuse. </p>
</dd>

### -param <i>Status</i> [in]

<dd>
<p>Specifies the NTSTATUS value to be set in the IRP after it is reinitialized.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>Drivers for Windows 2000 and later versions of Windows use <b>IoReuseIrp</b> to reuse an IRP.</p>

<p>A driver should use <b>IoReuseIrp</b> only on IRPs it previously allocated either as raw memory or with <a href="https://msdn.microsoft.com/library/windows/hardware/ff548257">IoAllocateIrp</a>. In particular, drivers should not use this routine for IRPs created with <a href="https://msdn.microsoft.com/library/windows/hardware/ff549397">IoMakeAssociatedIrp</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff548330">IoBuildSynchronousFsdRequest</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff548310">IoBuildAsynchronousFsdRequest</a>, or <a href="https://msdn.microsoft.com/library/windows/hardware/ff548318">IoBuildDeviceIoControlRequest</a>. </p>

<p>See <a href="https://msdn.microsoft.com/library/windows/hardware/ff561107">Reusing IRPs</a> for more details on how to reuse IRPs. </p>

<p>Drivers for Windows 2000 and later versions of Windows use <b>IoReuseIrp</b> to reuse an IRP.</p>

<p>A driver should use <b>IoReuseIrp</b> only on IRPs it previously allocated either as raw memory or with <a href="https://msdn.microsoft.com/library/windows/hardware/ff548257">IoAllocateIrp</a>. In particular, drivers should not use this routine for IRPs created with <a href="https://msdn.microsoft.com/library/windows/hardware/ff549397">IoMakeAssociatedIrp</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff548330">IoBuildSynchronousFsdRequest</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff548310">IoBuildAsynchronousFsdRequest</a>, or <a href="https://msdn.microsoft.com/library/windows/hardware/ff548318">IoBuildDeviceIoControlRequest</a>. </p>

<p>See <a href="https://msdn.microsoft.com/library/windows/hardware/ff561107">Reusing IRPs</a> for more details on how to reuse IRPs. </p>

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
<dt>Wdm.h (include Ntddk.h)</dt>
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
<p>&lt;=DISPATCH_LEVEL</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549661">IoReuseIrp</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975177">IoReuseIrp2</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh454220">HwStorPortProhibitedDDIs</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549315">IoInitializeIrp</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548257">IoAllocateIrp</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549397">IoMakeAssociatedIrp</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550694">IRP</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20IoReuseIrp routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>