---
UID: NF.ntifs.ZwWaitForSingleObject
title: ZwWaitForSingleObject
author: windows-driver-content
description: The ZwWaitForSingleObject routine waits until the specified object attains a state of Signaled. An optional time-out can also be specified.
old-location: kernel\zwwaitforsingleobject.htm
ms.assetid: 5eea0877-329d-4fa3-847e-365d6a545b07
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: ntifs.h
req.include-header: Ntifs.h, FltKernel.h
req.target-type: Universal
req.target-min-winverclnt: Available starting with Windows XP.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: ZwWaitForSingleObject,NtWaitForSingleObject
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: HwStorPortProhibitedDDIs, SpNoWait
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: PASSIVE_LEVEL
ms.keywords: ZwWaitForSingleObject
req.iface: 
---

# ZwWaitForSingleObject function



## -description
<p>The <b>ZwWaitForSingleObject</b> routine waits until the specified object attains a state of Signaled. An optional time-out can also be specified.</p>


## -syntax

````
NTSTATUS ZwWaitForSingleObject(
  _In_     HANDLE         Handle,
  _In_     BOOLEAN        Alertable,
  _In_opt_ PLARGE_INTEGER Timeout
);
````


## -parameters
<dl>

### -param <i>Handle</i> [in]

<dd>
<p>A handle to the object.</p>
</dd>

### -param <i>Alertable</i> [in]

<dd>
<p>A boolean value that specifies whether the wait is alertable.</p>
</dd>

### -param <i>Timeout</i> [in, optional]

<dd>
<p>An optional pointer to a time-out value that specifies the absolute or relative time at which the wait is to be completed. A negative value specifies an interval relative to the current time. The value should be expressed in units of 100 nanoseconds. Absolute expiration times track any changes in the system time. Relative expiration times are not affected by system time changes.</p>
</dd>
</dl>

## -returns
<p><b>ZwWaitForSingleObject</b> can return one of the following possible status codes:</p><dl>
<dt><b>STATUS_ACCESS_DENIED</b></dt>
</dl><p>The caller did not have the required privileges to the event specified by the <i>Handle</i> parameter.</p><dl>
<dt><b>STATUS_ALERTED</b></dt>
</dl><p>The wait was aborted to deliver an alert to the current thread.</p><dl>
<dt><b>STATUS_INVALID_HANDLE</b></dt>
</dl><p>The supplied <i>Handle</i> parameter was invalid.</p><dl>
<dt><b>STATUS_SUCCESS</b></dt>
</dl><p>The specified object satisfied the wait.</p><dl>
<dt><b>STATUS_TIMEOUT</b></dt>
</dl><p>A time-out occurred before the object was set to a signaled state. This value can be returned when the specified set of wait conditions cannot be immediately met and the <i>Timeout</i> parameter is set to zero.</p><dl>
<dt><b>STATUS_USER_APC</b></dt>
</dl><p>The wait was aborted to deliver a user APC to the current thread.</p>

<p> </p>

<p>Note that the NT_SUCCESS macro recognizes the STATUS_ALERTED, STATUS_SUCCESS, STATUS_TIMEOUT, and STATUS_USER_APC status values as "success" values.</p>

## -remarks
<p><b>ZwWaitForSingleObject</b> waits until the specified object attains a state of Signaled. An optional timeout can also be specified. <b>ZwWaitForSingleObject</b> examines the current state of the specified object to determine whether the wait can be satisfied immediately. If so, actions are performed. Otherwise, the current thread is put in a waiting state and a new thread is selected for execution on the current processor.</p>

<p>If a <i>Timeout</i> parameter is not specified, then the wait will not be satisfied until the object attains a state of Signaled. If a <i>Timeout</i> parameter is specified, and the object has not attained a state of Signaled when the time-out expires, then the wait is automatically satisfied. If an explicit <i>Timeout</i> value of zero is specified, then no wait will occur if the wait cannot be satisfied immediately. A <i>Timeout</i> value of zero allows the testing of a set of wait conditions and for the conditional performance of any side effects if the wait can be immediately satisfied, as in the acquisition of a mutex. The wait can also be specified as alertable.</p>

<p>The <i>Alertable</i> parameter specifies whether the thread can be alerted and its wait state consequently aborted. If the value of this parameter is <b>FALSE</b> then the thread cannot be alerted. The only exception to this rule is that of a terminating thread. Under certain circumstances a terminating thread can be alerted while it is in the process of winding down. A thread is automatically made alertable, for instance, when terminated by a user with a CTRL+C.</p>

<p>If the value of <i>Alertable</i>is <b>TRUE</b> and one of the following conditions is present, the thread will be alerted:</p>

<p>If the origin of the alert is an internal, undocumented kernel-mode routine used to alert threads.</p>

<p>The origin of the alert is a user-mode APC.</p>

<p>In the first of these two cases, the thread's wait is satisfied with a completion status of STATUS_ALERTED. In the second case, it is satisfied with a completion status of STATUS_USER_APC.</p>

<p>The thread must be alertable for a user-mode APC to be delivered. This is not the case for kernel-mode APCs. A kernel-mode APC can be delivered and executed even though the thread is not alerted. Once the APC's execution completes, the thread's wait resumes. A thread is never alerted, nor is its wait aborted, by the delivery of a kernel-mode APC.</p>

<p>The delivery of kernel-mode APCs to a waiting thread does not depend on whether the thread can be alerted. If the kernel-mode APC is a special kernel-mode APC, then the APC is delivered provided that the IRQL is less than APC_LEVEL. If the kernel-mode APC is a normal kernel-mode APC, then the APC is delivered provided that the following three conditions hold: (1) the IRQL is less than APC_LEVEL, (2) no kernel APC is in progress, and (3) the thread is not in a critical section.</p>

<p>If the handle passed to <b>ZwWaitForSingleObject</b> refers to a mutex, the APC delivery is the same as for all other dispatcher objects during the wait. However, once <b>ZwWaitForSingleObject</b> returns with STATUS_SUCCESS and the thread actually holds the mutex, only special kernel-mode APCs are delivered. Delivery of all other APCs, both kernel-mode and user-mode, is disabled. This restriction on the delivery of APCs persists until the mutex is released.</p>

<p>It is especially important to check the return value of <b>ZwWaitForSingleObject</b> when the <i>Alertable</i> parameter is <b>TRUE</b>, because <b>ZwWaitForSingleObject</b> might return early with a status of STATUS_USER_APC or STATUS_ALERTED.</p>

<p>All long term waits can be aborted by a user if the <i>Alertable</i> parameter is set to <b>FALSE</b>.</p>

<p>For additional information, see <a href="https://msdn.microsoft.com/b967beec-922c-4acf-a578-c476ce024fdb">Do Waiting Threads Receive Alerts and APCs?</a>
</p>

<p>Callers of <b>ZwWaitForSingleObject</b> must be running at IRQL less than or equal to DISPATCH_LEVEL. Usually, the caller must be running at IRQL PASSIVE_LEVEL and in a nonarbitrary thread context. A call while running at IRQL DISPATCH_LEVEL is valid if and only if the caller specifies a <i>Timeout</i> parameter of zero. That is, a driver must not wait for a nonzero interval at IRQL equal to DISPATCH_LEVEL.</p>

<p>Time-out intervals are measured relative to the system clock, and the accuracy of the time-out measurement is limited by the granularity of the system clock. For more information, see <a href="https://msdn.microsoft.com/library/windows/hardware/jj602805">Timer Accuracy</a>.</p>

<p>For calls from kernel-mode drivers, the <b>Nt<i>Xxx</i></b> and <b>Zw<i>Xxx</i></b> versions of a Windows Native System Services routine can behave differently in the way that they handle and interpret input parameters. For more information about the relationship between the <b>Nt<i>Xxx</i></b> and <b>Zw<i>Xxx</i></b> versions of a routine, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff565438">Using Nt and Zw Versions of the Native System Services Routines</a>.</p>

<p><b>ZwWaitForSingleObject</b> waits until the specified object attains a state of Signaled. An optional timeout can also be specified. <b>ZwWaitForSingleObject</b> examines the current state of the specified object to determine whether the wait can be satisfied immediately. If so, actions are performed. Otherwise, the current thread is put in a waiting state and a new thread is selected for execution on the current processor.</p>

<p>If a <i>Timeout</i> parameter is not specified, then the wait will not be satisfied until the object attains a state of Signaled. If a <i>Timeout</i> parameter is specified, and the object has not attained a state of Signaled when the time-out expires, then the wait is automatically satisfied. If an explicit <i>Timeout</i> value of zero is specified, then no wait will occur if the wait cannot be satisfied immediately. A <i>Timeout</i> value of zero allows the testing of a set of wait conditions and for the conditional performance of any side effects if the wait can be immediately satisfied, as in the acquisition of a mutex. The wait can also be specified as alertable.</p>

<p>The <i>Alertable</i> parameter specifies whether the thread can be alerted and its wait state consequently aborted. If the value of this parameter is <b>FALSE</b> then the thread cannot be alerted. The only exception to this rule is that of a terminating thread. Under certain circumstances a terminating thread can be alerted while it is in the process of winding down. A thread is automatically made alertable, for instance, when terminated by a user with a CTRL+C.</p>

<p>If the value of <i>Alertable</i>is <b>TRUE</b> and one of the following conditions is present, the thread will be alerted:</p>

<p>If the origin of the alert is an internal, undocumented kernel-mode routine used to alert threads.</p>

<p>The origin of the alert is a user-mode APC.</p>

<p>In the first of these two cases, the thread's wait is satisfied with a completion status of STATUS_ALERTED. In the second case, it is satisfied with a completion status of STATUS_USER_APC.</p>

<p>The thread must be alertable for a user-mode APC to be delivered. This is not the case for kernel-mode APCs. A kernel-mode APC can be delivered and executed even though the thread is not alerted. Once the APC's execution completes, the thread's wait resumes. A thread is never alerted, nor is its wait aborted, by the delivery of a kernel-mode APC.</p>

<p>The delivery of kernel-mode APCs to a waiting thread does not depend on whether the thread can be alerted. If the kernel-mode APC is a special kernel-mode APC, then the APC is delivered provided that the IRQL is less than APC_LEVEL. If the kernel-mode APC is a normal kernel-mode APC, then the APC is delivered provided that the following three conditions hold: (1) the IRQL is less than APC_LEVEL, (2) no kernel APC is in progress, and (3) the thread is not in a critical section.</p>

<p>If the handle passed to <b>ZwWaitForSingleObject</b> refers to a mutex, the APC delivery is the same as for all other dispatcher objects during the wait. However, once <b>ZwWaitForSingleObject</b> returns with STATUS_SUCCESS and the thread actually holds the mutex, only special kernel-mode APCs are delivered. Delivery of all other APCs, both kernel-mode and user-mode, is disabled. This restriction on the delivery of APCs persists until the mutex is released.</p>

<p>It is especially important to check the return value of <b>ZwWaitForSingleObject</b> when the <i>Alertable</i> parameter is <b>TRUE</b>, because <b>ZwWaitForSingleObject</b> might return early with a status of STATUS_USER_APC or STATUS_ALERTED.</p>

<p>All long term waits can be aborted by a user if the <i>Alertable</i> parameter is set to <b>FALSE</b>.</p>

<p>For additional information, see <a href="https://msdn.microsoft.com/b967beec-922c-4acf-a578-c476ce024fdb">Do Waiting Threads Receive Alerts and APCs?</a>
</p>

<p>Callers of <b>ZwWaitForSingleObject</b> must be running at IRQL less than or equal to DISPATCH_LEVEL. Usually, the caller must be running at IRQL PASSIVE_LEVEL and in a nonarbitrary thread context. A call while running at IRQL DISPATCH_LEVEL is valid if and only if the caller specifies a <i>Timeout</i> parameter of zero. That is, a driver must not wait for a nonzero interval at IRQL equal to DISPATCH_LEVEL.</p>

<p>Time-out intervals are measured relative to the system clock, and the accuracy of the time-out measurement is limited by the granularity of the system clock. For more information, see <a href="https://msdn.microsoft.com/library/windows/hardware/jj602805">Timer Accuracy</a>.</p>

<p>For calls from kernel-mode drivers, the <b>Nt<i>Xxx</i></b> and <b>Zw<i>Xxx</i></b> versions of a Windows Native System Services routine can behave differently in the way that they handle and interpret input parameters. For more information about the relationship between the <b>Nt<i>Xxx</i></b> and <b>Zw<i>Xxx</i></b> versions of a routine, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff565438">Using Nt and Zw Versions of the Native System Services Routines</a>.</p>

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
<p>Available starting with Windows XP.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntifs.h (include Ntifs.h or FltKernel.h)</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/hh454220">HwStorPortProhibitedDDIs</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh454255">SpNoWait</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549039">IoCreateNotificationEvent</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549045">IoCreateSynchronizationEvent</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551980">KeClearEvent</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553176">KeResetEvent</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553253">KeSetEvent</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553350">KeWaitForSingleObject</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff565438">Using Nt and Zw Versions of the Native System Services Routines</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff566417">ZwClose</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff566423">ZwCreateEvent</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567092">ZwSetEvent</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20ZwWaitForSingleObject routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>