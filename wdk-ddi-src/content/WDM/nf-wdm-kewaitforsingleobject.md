---
UID: NF.wdm.KeWaitForSingleObject
title: KeWaitForSingleObject
author: windows-driver-content
description: The KeWaitForSingleObject routine puts the current thread into a wait state until the given dispatcher object is set to a signaled state or (optionally) until the wait times out.
old-location: kernel\kewaitforsingleobject.htm
ms.assetid: 65a1aa46-571b-46f7-b60e-ef8c6dc14d39
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
req.alt-api: KeWaitForSingleObject
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: CompleteRequestStatusCheck, IoAllocateIrpSignalEventInCompletionTimeout, IoBuildDeviceControlWait, IoBuildDeviceControlWaitTimeout, IoBuildFsdIrpSignalEventInCompletionTimeout, IoBuildSynchronousFsdRequestWait, IoBuildSynchronousFsdRequestWaitTimeout, IrpProcessingComplete, IrqlKeWaitForMutexObject, LowerDriverReturn, MarkIrpPending2, PendedCompletedRequest, PendedCompletedRequest2, PendedCompletedRequest3, PendedCompletedRequestEx, RemoveLockForwardDeviceControl, RemoveLockForwardDeviceControlInternal, RemoveLockForwardRead, RemoveLockForwardWrite, StartDeviceWait, StartDeviceWait2, StartDeviceWait3, StartDeviceWait4, HwStorPortProhibitedDDIs, SpNoWait
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: See Remarks section.
ms.keywords: KeWaitForSingleObject
req.iface: 
req.product: Windows 10 or later.
---

# KeWaitForSingleObject function



## -description
<p>The <b>KeWaitForSingleObject</b> routine puts the current thread into a wait state until the given dispatcher object is set to a signaled state or (optionally) until the wait times out.</p>


## -syntax

````
NTSTATUS KeWaitForSingleObject(
  _In_     PVOID           Object,
  _In_     KWAIT_REASON    WaitReason,
  _In_     KPROCESSOR_MODE WaitMode,
  _In_     BOOLEAN         Alertable,
  _In_opt_ PLARGE_INTEGER  Timeout
);
````


## -parameters
<dl>

### -param <i>Object</i> [in]

<dd>
<p>Pointer to an initialized dispatcher object (event, mutex, semaphore, thread, or timer) for which the caller supplies the storage.</p>
</dd>

### -param <i>WaitReason</i> [in]

<dd>
<p>Specifies the reason for the wait. A driver should set this value to <b>Executive</b>, unless it is doing work on behalf of a user and is running in the context of a user thread, in which case it should set this value to <b>UserRequest</b>.</p>
</dd>

### -param <i>WaitMode</i> [in]

<dd>
<p>Specifies whether the caller waits in <b>KernelMode</b> or <b>UserMode</b>. Lowest-level and intermediate drivers should specify <b>KernelMode</b>. If the given <i>Object</i> is a mutex, the caller must specify <b>KernelMode</b>.</p>
</dd>

### -param <i>Alertable</i> [in]

<dd>
<p>Specifies a Boolean value that is <b>TRUE</b> if the wait is alertable and <b>FALSE</b> otherwise.</p>
</dd>

### -param <i>Timeout</i> [in, optional]

<dd>
<p>Pointer to a time-out value that specifies the absolute or relative time, in 100-nanosecond units, at which the wait is to be completed.</p>
<p>A positive value specifies an absolute time, relative to January 1, 1601. A negative value specifies an interval relative to the current time. Absolute expiration times track any changes in the system time; relative expiration times are not affected by system time changes. </p>
<p>If *<i>Timeout</i> = 0, the routine returns without waiting. If the caller supplies a <b>NULL</b> pointer, the routine waits indefinitely until the dispatcher object is set to the signaled state. For more information, see the following Remarks section.</p>
</dd>
</dl>

## -returns
<p><b>KeWaitForSingleObject</b> can return one of the following:</p><dl>
<dt><b>STATUS_SUCCESS</b></dt>
</dl><p>The dispatcher object specified by the <i>Object</i> parameter satisfied the wait.</p><dl>
<dt><b>STATUS_ALERTED</b></dt>
</dl><p>The wait was interrupted to deliver an alert to the calling thread.</p><dl>
<dt><b>STATUS_USER_APC</b></dt>
</dl><p>The wait was interrupted to deliver a user asynchronous procedure call (APC) to the calling thread.</p><dl>
<dt><b>STATUS_TIMEOUT</b></dt>
</dl><p>A time-out occurred before the object was set to a signaled state. This value can be returned when the specified set of wait conditions cannot be immediately met and <i>Timeout</i> is set to zero.</p>

<p> </p>

<p>Note that the NT_SUCCESS macro recognizes all of these status values as "success" values.</p>

## -remarks
<p>The current state of the specified <i>Object</i> is examined to determine whether the wait can be satisfied immediately. If so, the necessary side effects are performed on the object. Otherwise, the current thread is put in a waiting state and a new thread is selected for execution on the current processor.</p>

<p>The <i>Alertable</i> parameter determines when the thread can be alerted and its wait state consequently aborted. For additional information, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff565592">Waits and APCs</a>.</p>

<p>A special consideration applies when the <i>Object</i> parameter passed to <b>KeWaitForSingleObject</b> is a mutex. If the dispatcher object waited on is a mutex, APC delivery is the same as for all other dispatcher objects <u>during the wait</u>. However, after <b>KeWaitForSingleObject</b> returns with STATUS_SUCCESS and the thread actually holds the mutex, only special kernel-mode APCs are delivered. Delivery of all other APCs, both kernel-mode and user-mode, is disabled. This restriction on the delivery of APCs persists until the mutex is released.</p>

<p>If the <i>WaitMode</i> parameter is <b>UserMode</b>, the kernel stack can be swapped out during the wait. Consequently, a caller must <u>never</u> attempt to pass parameters on the stack when calling <b>KeWaitForSingleObject</b> using the <b>UserMode</b> argument. If you allocate the event on the stack, you must set the <i>WaitMode</i> parameter to <b>KernelMode</b>.</p>

<p>It is especially important to check the return value of <b>KeWaitForSingleObject</b> when the <i>WaitMode</i> parameter is <b>UserMode</b> or <i>Alertable</i> is <b>TRUE</b>, because <b>KeWaitForSingleObject</b> might return early with a status of STATUS_USER_APC or STATUS_ALERTED.</p>

<p>All long-term waits that can be aborted by a user should be <b>UserMode</b> waits and <i>Alertable</i> should be set to <b>FALSE</b>.</p>

<p>Where possible, <i>Alertable</i> should be set to <b>FALSE</b> and <i>WaitMode</i> should be set to <b>KernelMode</b>, in order to reduce driver complexity. The principal exception to this is when the wait is a long-term wait.</p>

<p>If a <b>NULL</b> pointer is supplied for <i>Timeout</i>, the calling thread remains in a wait state until the <i>Object</i> is signaled.</p>

<p>A time-out value of zero allows the testing of a set of wait conditions and for the conditional performance of any side effects if the wait can be immediately satisfied, as in the acquisition of a mutex.</p>

<p>Time-out intervals are measured relative to the system clock, and the accuracy with which the operating system can detect the end of a time-out interval is limited by the granularity of the system clock. For more information, see <a href="https://msdn.microsoft.com/library/windows/hardware/jj602805">Timer Accuracy</a>.</p>

<p>A mutex can be recursively acquired only MINLONG times. If this limit is exceeded, the routine raises a STATUS_MUTANT_LIMIT_EXCEEDED exception.</p>

<p>Callers of <b>KeWaitForSingleObject</b> must be running at IRQL &lt;= DISPATCH_LEVEL. However, if <i>Timeout</i> = <b>NULL</b> or *<i>Timeout</i> != 0, the caller must be running at IRQL &lt;= APC_LEVEL and in a nonarbitrary thread context. (If <i>Timeout</i> != <b>NULL</b> and *<i>Timeout</i> = 0, the caller must be running at IRQL &lt;= DISPATCH_LEVEL.)</p>

<p>The current state of the specified <i>Object</i> is examined to determine whether the wait can be satisfied immediately. If so, the necessary side effects are performed on the object. Otherwise, the current thread is put in a waiting state and a new thread is selected for execution on the current processor.</p>

<p>The <i>Alertable</i> parameter determines when the thread can be alerted and its wait state consequently aborted. For additional information, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff565592">Waits and APCs</a>.</p>

<p>A special consideration applies when the <i>Object</i> parameter passed to <b>KeWaitForSingleObject</b> is a mutex. If the dispatcher object waited on is a mutex, APC delivery is the same as for all other dispatcher objects <u>during the wait</u>. However, after <b>KeWaitForSingleObject</b> returns with STATUS_SUCCESS and the thread actually holds the mutex, only special kernel-mode APCs are delivered. Delivery of all other APCs, both kernel-mode and user-mode, is disabled. This restriction on the delivery of APCs persists until the mutex is released.</p>

<p>If the <i>WaitMode</i> parameter is <b>UserMode</b>, the kernel stack can be swapped out during the wait. Consequently, a caller must <u>never</u> attempt to pass parameters on the stack when calling <b>KeWaitForSingleObject</b> using the <b>UserMode</b> argument. If you allocate the event on the stack, you must set the <i>WaitMode</i> parameter to <b>KernelMode</b>.</p>

<p>It is especially important to check the return value of <b>KeWaitForSingleObject</b> when the <i>WaitMode</i> parameter is <b>UserMode</b> or <i>Alertable</i> is <b>TRUE</b>, because <b>KeWaitForSingleObject</b> might return early with a status of STATUS_USER_APC or STATUS_ALERTED.</p>

<p>All long-term waits that can be aborted by a user should be <b>UserMode</b> waits and <i>Alertable</i> should be set to <b>FALSE</b>.</p>

<p>Where possible, <i>Alertable</i> should be set to <b>FALSE</b> and <i>WaitMode</i> should be set to <b>KernelMode</b>, in order to reduce driver complexity. The principal exception to this is when the wait is a long-term wait.</p>

<p>If a <b>NULL</b> pointer is supplied for <i>Timeout</i>, the calling thread remains in a wait state until the <i>Object</i> is signaled.</p>

<p>A time-out value of zero allows the testing of a set of wait conditions and for the conditional performance of any side effects if the wait can be immediately satisfied, as in the acquisition of a mutex.</p>

<p>Time-out intervals are measured relative to the system clock, and the accuracy with which the operating system can detect the end of a time-out interval is limited by the granularity of the system clock. For more information, see <a href="https://msdn.microsoft.com/library/windows/hardware/jj602805">Timer Accuracy</a>.</p>

<p>A mutex can be recursively acquired only MINLONG times. If this limit is exceeded, the routine raises a STATUS_MUTANT_LIMIT_EXCEEDED exception.</p>

<p>Callers of <b>KeWaitForSingleObject</b> must be running at IRQL &lt;= DISPATCH_LEVEL. However, if <i>Timeout</i> = <b>NULL</b> or *<i>Timeout</i> != 0, the caller must be running at IRQL &lt;= APC_LEVEL and in a nonarbitrary thread context. (If <i>Timeout</i> != <b>NULL</b> and *<i>Timeout</i> = 0, the caller must be running at IRQL &lt;= DISPATCH_LEVEL.)</p>

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
<p>See Remarks section.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/hh975144">CompleteRequestStatusCheck</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975158">IoAllocateIrpSignalEventInCompletionTimeout</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975161">IoBuildDeviceControlWait</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975162">IoBuildDeviceControlWaitTimeout</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975170">IoBuildFsdIrpSignalEventInCompletionTimeout</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975173">IoBuildSynchronousFsdRequestWait</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975174">IoBuildSynchronousFsdRequestWaitTimeout</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff547325">IrpProcessingComplete</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff547843">IrqlKeWaitForMutexObject</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff548273">LowerDriverReturn</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff549021">MarkIrpPending2</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff550374">PendedCompletedRequest</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975198">PendedCompletedRequest2</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975199">PendedCompletedRequest3</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975200">PendedCompletedRequestEx</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975210">RemoveLockForwardDeviceControl</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975212">RemoveLockForwardDeviceControlInternal</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975214">RemoveLockForwardRead</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975216">RemoveLockForwardWrite</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975252">StartDeviceWait</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975253">StartDeviceWait2</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975254">StartDeviceWait3</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975255">StartDeviceWait4</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh454220">HwStorPortProhibitedDDIs</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh454255">SpNoWait</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545293">ExInitializeFastMutex</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551961">KeBugCheckEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552137">KeInitializeEvent</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552147">KeInitializeMutex</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552150">KeInitializeSemaphore</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552168">KeInitializeTimer</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553324">KeWaitForMultipleObjects</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553344">KeWaitForMutexObject</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20KeWaitForSingleObject routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>