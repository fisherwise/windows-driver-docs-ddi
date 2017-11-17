---
UID: NF.wdm.IoCancelIrp
title: IoCancelIrp
author: windows-driver-content
description: The IoCancelIrp routine sets the cancel bit in a given IRP and calls the cancel routine for the IRP if there is one.
old-location: kernel\iocancelirp.htm
ms.assetid: 8d991192-2df8-4b4d-a4c5-df5091492e67
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
req.alt-api: IoCancelIrp
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: HwStorPortProhibitedDDIs
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: <= DISPATCH_LEVEL
ms.keywords: IoCancelIrp
req.iface: 
req.product: Windows 10 or later.
---

# IoCancelIrp function



## -description
<p>The <b>IoCancelIrp</b> routine sets the cancel bit in a given IRP and calls the cancel routine for the IRP if there is one.</p>


## -syntax

````
BOOLEAN IoCancelIrp(
  _In_ PIRP Irp
);
````


## -parameters
<dl>

### -param <i>Irp</i> [in]

<dd>
<p>A pointer to the IRP to be canceled.</p>
</dd>
</dl>

## -returns
<p><b>IoCancelIrp</b> returns <b>TRUE</b> if the IRP had a cancel routine and this routine was called. Otherwise, it returns <b>FALSE</b>. In either case, the IRP's cancel bit is set to <b>TRUE</b>. For more information, see Remarks.</p>

## -remarks
<p>If the IRP has a cancel routine, <b>IoCancelIrp</b> sets the cancel bit and calls the cancel routine.</p>

<p>If <i>Irp</i>-&gt;<b>CancelRoutine</b> is <b>NULL</b>, and therefore the IRP is not cancelable, <b>IoCancelIrp</b> sets the IRP's cancel bit and returns <b>FALSE</b>. The IRP should be canceled at a later time when it becomes cancelable.</p>

<p>If a driver that does not own the IRP calls <b>IoCancelIrp</b>, the results are unpredictable. The IRP might be completed with a successful status even though its cancel bit was set.</p>

<p>An intermediate driver should not arbitrarily call <b>IoCancelIrp</b> unless that driver created the IRP passed in the call. Otherwise, the intermediate driver might cancel an IRP that some higher-level driver is tracking for purposes of its own.</p>

<p>If the IRP has a cancel routine, <b>IoCancelIrp</b> sets the cancel bit and calls the cancel routine.</p>

<p>If <i>Irp</i>-&gt;<b>CancelRoutine</b> is <b>NULL</b>, and therefore the IRP is not cancelable, <b>IoCancelIrp</b> sets the IRP's cancel bit and returns <b>FALSE</b>. The IRP should be canceled at a later time when it becomes cancelable.</p>

<p>If a driver that does not own the IRP calls <b>IoCancelIrp</b>, the results are unpredictable. The IRP might be completed with a successful status even though its cancel bit was set.</p>

<p>An intermediate driver should not arbitrarily call <b>IoCancelIrp</b> unless that driver created the IRP passed in the call. Otherwise, the intermediate driver might cancel an IRP that some higher-level driver is tracking for purposes of its own.</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/hh454220">HwStorPortProhibitedDDIs</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549674">IoSetCancelRoutine</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20IoCancelIrp routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>