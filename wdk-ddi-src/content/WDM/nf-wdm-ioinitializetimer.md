---
UID: NF.wdm.IoInitializeTimer
title: IoInitializeTimer
author: windows-driver-content
description: The IoInitializeTimer routine sets up a driver-supplied IoTimer routine associated with a given device object.
old-location: kernel\ioinitializetimer.htm
ms.assetid: f2b0f74d-7417-443e-96ec-5101b1289f9d
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
req.alt-api: IoInitializeTimer
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: IrqlIoPassive5, PowerIrpDDis, HwStorPortProhibitedDDIs
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: PASSIVE_LEVEL
ms.keywords: IoInitializeTimer
req.iface: 
req.product: Windows 10 or later.
---

# IoInitializeTimer function



## -description
<p>The <b>IoInitializeTimer</b> routine sets up a driver-supplied <a href="https://msdn.microsoft.com/library/windows/hardware/ff550381">IoTimer</a> routine associated with a given device object. </p>


## -syntax

````
NTSTATUS IoInitializeTimer(
  _In_     PDEVICE_OBJECT    DeviceObject,
  _In_     PIO_TIMER_ROUTINE TimerRoutine,
  _In_opt_ PVOID             Context
);
````


## -parameters
<dl>

### -param <i>DeviceObject</i> [in]

<dd>
<p>Pointer to a device object representing a device on which I/O operations can time out.</p>
</dd>

### -param <i>TimerRoutine</i> [in]

<dd>
<p>Pointer to the driver-supplied <i>IoTimer</i> routine. </p>
</dd>

### -param <i>Context</i> [in, optional]

<dd>
<p>Pointer to the driver-determined context with which its <i>IoTimer</i> routine will be called. </p>
</dd>
</dl>

## -returns
<p><b>IoInitializeTimer</b> returns STATUS_SUCCESS if the <i>IoTimer</i> routine is set up.</p>

## -remarks
<p><b>IoInitializeTimer</b> should be called only once per device object.</p>

<p>A driver's <a href="https://msdn.microsoft.com/library/windows/hardware/ff550381">IoTimer</a> routine is called once per second after the driver enables the timer by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff550373">IoStartTimer</a>. The driver can disable the timer by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff550377">IoStopTimer</a> and can reenable it again with <b>IoStartTimer</b>.</p>

<p>The driver's <i>IoTimer</i> routine is called at IRQL = DISPATCH_LEVEL and therefore must not contain pageable code.</p>

<p>When the timer is running, the I/O manager calls the driver-supplied <i>IoTimer</i> routine once per second. Drivers whose time-out routines should be called at variable intervals or at intervals of finer granularity can set up a <a href="https://msdn.microsoft.com/library/windows/hardware/ff542983">CustomTimerDpc</a> routine and use the <b>Ke<i>Xxx</i>Timer</b> routines.</p>

<p><b>IoInitializeTimer</b> should be called only once per device object.</p>

<p>A driver's <a href="https://msdn.microsoft.com/library/windows/hardware/ff550381">IoTimer</a> routine is called once per second after the driver enables the timer by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff550373">IoStartTimer</a>. The driver can disable the timer by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff550377">IoStopTimer</a> and can reenable it again with <b>IoStartTimer</b>.</p>

<p>The driver's <i>IoTimer</i> routine is called at IRQL = DISPATCH_LEVEL and therefore must not contain pageable code.</p>

<p>When the timer is running, the I/O manager calls the driver-supplied <i>IoTimer</i> routine once per second. Drivers whose time-out routines should be called at variable intervals or at intervals of finer granularity can set up a <a href="https://msdn.microsoft.com/library/windows/hardware/ff542983">CustomTimerDpc</a> routine and use the <b>Ke<i>Xxx</i>Timer</b> routines.</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547796">IrqlIoPassive5</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975204">PowerIrpDDis</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh454220">HwStorPortProhibitedDDIs</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550381">IoTimer</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550373">IoStartTimer</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550377">IoStopTimer</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552168">KeInitializeTimer</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553286">KeSetTimer</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20IoInitializeTimer routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>