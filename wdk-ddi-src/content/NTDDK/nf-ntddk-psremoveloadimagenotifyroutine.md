---
UID: NF.ntddk.PsRemoveLoadImageNotifyRoutine
title: PsRemoveLoadImageNotifyRoutine
author: windows-driver-content
description: The PsRemoveLoadImageNotifyRoutine routine removes a callback routine that was registered by the PsSetLoadImageNotifyRoutine routine.
old-location: kernel\psremoveloadimagenotifyroutine.htm
ms.assetid: 5491f9fb-8f87-41ed-9629-18318554ad90
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: ntddk.h
req.include-header: Ntddk.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: PsRemoveLoadImageNotifyRoutine
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: PowerIrpDDis, HwStorPortProhibitedDDIs
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: <=APC_LEVEL
ms.keywords: PsRemoveLoadImageNotifyRoutine
req.iface: 
---

# PsRemoveLoadImageNotifyRoutine function



## -description
<p>The <b>PsRemoveLoadImageNotifyRoutine</b> routine removes a callback routine that was registered by the <a href="https://msdn.microsoft.com/library/windows/hardware/ff559957">PsSetLoadImageNotifyRoutine</a> routine. </p>


## -syntax

````
NTSTATUS PsRemoveLoadImageNotifyRoutine(
  _In_ PLOAD_IMAGE_NOTIFY_ROUTINE NotifyRoutine
);
````


## -parameters
<dl>

### -param <i>NotifyRoutine</i> [in]

<dd>
<p>Pointer to the callback routine that the driver has previously registered through <a href="https://msdn.microsoft.com/library/windows/hardware/ff559957">PsSetLoadImageNotifyRoutine</a>. </p>
</dd>
</dl>

## -returns
<p><b>PsRemoveLoadImageNotifyRoutine</b> returns STATUS_SUCCESS if it successfully removes the callback routine, or STATUS_PROCEDURE_NOT_FOUND if the value of <i>NotifyRoutine</i> does not match any registered callback routine.</p>

## -remarks
<p>If the driver's callback routine is currently running, <b>PsRemoveLoadImageNotifyRoutine</b> waits until the callback routine exits before removing it. Therefore, the callback routine itself must not call <b>PsRemoveLoadImageNotifyRoutine</b>. </p>

<p>If the driver's callback routine is currently running, <b>PsRemoveLoadImageNotifyRoutine</b> waits until the callback routine exits before removing it. Therefore, the callback routine itself must not call <b>PsRemoveLoadImageNotifyRoutine</b>. </p>

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
<dt>Ntddk.h (include Ntddk.h)</dt>
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
<p>&lt;=APC_LEVEL</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/hh975204">PowerIrpDDis</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh454220">HwStorPortProhibitedDDIs</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff559957">PsSetLoadImageNotifyRoutine</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20PsRemoveLoadImageNotifyRoutine routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>