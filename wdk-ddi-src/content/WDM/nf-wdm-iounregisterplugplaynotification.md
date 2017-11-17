---
UID: NF.wdm.IoUnregisterPlugPlayNotification
title: IoUnregisterPlugPlayNotification
author: windows-driver-content
description: This routine is obsolete in Windows 7 and later versions of Windows. For more information, see the following Remarks section.The IoUnregisterPlugPlayNotification routine removes the registration of a driver's callback routine for a PnP event.
old-location: kernel\iounregisterplugplaynotification.htm
ms.assetid: 55eca513-030c-47f8-9ce9-ab36183cbaf2
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
req.alt-api: IoUnregisterPlugPlayNotification
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
req.irql: PASSIVE_LEVEL
ms.keywords: IoUnregisterPlugPlayNotification
req.iface: 
req.product: Windows 10 or later.
---

# IoUnregisterPlugPlayNotification function



## -description
<p>This routine is <u>obsolete</u> in Windows 7 and later versions of Windows. For more information, see the following Remarks section.</p>
<p>The <b>IoUnregisterPlugPlayNotification</b> routine removes the registration of a driver's callback routine for a PnP event.</p>


## -syntax

````
NTSTATUS IoUnregisterPlugPlayNotification(
  _In_ PVOID NotificationEntry
);
````


## -parameters
<dl>

### -param <i>NotificationEntry</i> [in]

<dd>
<p>Pointer to an opaque value representing the registration to be removed. The value was returned by a previous call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff549526">IoRegisterPlugPlayNotification</a>.</p>
</dd>
</dl>

## -returns
<p><b>IoUnregisterPlugPlayNotification</b> always returns STATUS_SUCCESS if <i>NotificationEntry </i>is valid.</p>

## -remarks
<p>In Windows 7 and later versions of Windows, this function is obsolete and is provided only to support existing drivers. Use the <a href="https://msdn.microsoft.com/library/windows/hardware/ff550404">IoUnregisterPlugPlayNotificationEx</a> routine instead.</p>

<p><b>IoUnregisterPlugPlayNotification</b> removes one PnP notification registration; that is, the registration of one driver callback routine for one PnP event category.</p>

<p>Drivers should unregister a notification first, then free any related context buffer.</p>

<p>A driver cannot be unloaded until it removes all of its PnP notification registrations because there is a reference on its driver object for each active registration.</p>

<p>In Windows 7 and later versions of Windows, this function is obsolete and is provided only to support existing drivers. Use the <a href="https://msdn.microsoft.com/library/windows/hardware/ff550404">IoUnregisterPlugPlayNotificationEx</a> routine instead.</p>

<p><b>IoUnregisterPlugPlayNotification</b> removes one PnP notification registration; that is, the registration of one driver callback routine for one PnP event category.</p>

<p>Drivers should unregister a notification first, then free any related context buffer.</p>

<p>A driver cannot be unloaded until it removes all of its PnP notification registrations because there is a reference on its driver object for each active registration.</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/hh975204">PowerIrpDDis</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh454220">HwStorPortProhibitedDDIs</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549526">IoRegisterPlugPlayNotification</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550404">IoUnregisterPlugPlayNotificationEx</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20IoUnregisterPlugPlayNotification routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>