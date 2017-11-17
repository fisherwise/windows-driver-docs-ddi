---
UID: NF.wdm.IoCsqInsertIrpEx
title: IoCsqInsertIrpEx
author: windows-driver-content
description: The IoCsqInsertIrpEx routine inserts an IRP into the driver's cancel-safe IRP queue.
old-location: kernel\iocsqinsertirpex.htm
ms.assetid: b1eb237d-ad4d-428c-beee-5f24677bd0d3
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: Available in Windows Server 2003 and later versions of the Windows operating system. The routine is also available in the Csq.lib library that ships with the Windows Driver Kit (WDK) and the Driver Development Kit (DDK) for Windows Server 2003. Drivers that must also work for on Windows XP, Windows 2000, and Windows 98/Me can instead link to Csq.lib to use the routine.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IoCsqInsertIrpEx
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: IoAllocateFree, IoReuseIrp, IrpCancelField, RemoveLockCheck, RemoveLockForward, RemoveLockForward2, RemoveLockForwardDeviceControl, RemoveLockForwardDeviceControl2, RemoveLockForwardDeviceControlInternal, RemoveLockForwardDeviceControlInternal2, RemoveLockForwardRead, RemoveLockForwardRead2, RemoveLockForwardWrite, RemoveLockForwardWrite2, RemoveLockReleaseCleanup, RemoveLockReleaseClose, RemoveLockReleaseCreate, RemoveLockReleaseDeviceControl, RemoveLockReleaseInternalDeviceControl, RemoveLockReleasePower, RemoveLockReleaseRead, RemoveLockReleaseShutdown, RemoveLockReleaseSystemControl, RemoveLockReleaseWrite
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: <= DISPATCH_LEVEL (see Remarks section)
ms.keywords: IoCsqInsertIrpEx
req.iface: 
req.product: Windows 10 or later.
---

# IoCsqInsertIrpEx function



## -description
<p>The <b>IoCsqInsertIrpEx</b> routine inserts an IRP into the driver's cancel-safe IRP queue.</p>


## -syntax

````
NTSTATUS IoCsqInsertIrpEx(
  _Inout_   PIO_CSQ             Csq,
  _Inout_   PIRP                Irp,
  _Out_opt_ PIO_CSQ_IRP_CONTEXT Context,
  _In_opt_  PVOID               InsertContext
);
````


## -parameters
<dl>

### -param <i>Csq</i> [in, out]

<dd>
<p>Pointer to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff550560">IO_CSQ</a> structure for the driver's cancel-safe IRP queue. This structure must have been initialized by <a href="https://msdn.microsoft.com/library/windows/hardware/ff549054">IoCsqInitialize</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff549060">IoCsqInitializeEx</a>.</p>
</dd>

### -param <i>Irp</i> [in, out]

<dd>
<p>Pointer to the IRP to be queued.</p>
</dd>

### -param <i>Context</i> [out, optional]

<dd>
<p>Pointer to an <a href="https://msdn.microsoft.com/library/windows/hardware/ff550567">IO_CSQ_IRP_CONTEXT</a> structure. <b>IoCsqInsertIrpEx</b> initializes this structure with context information for the inserted IRP. The driver passes this value to <a href="https://msdn.microsoft.com/library/windows/hardware/ff549070">IoCsqRemoveIrp</a> to delete the IRP from the queue. <i>Context</i> can be <b>NULL</b> if the driver will not use <b>IoCsqRemoveIrp</b> to remove this IRP from the queue.</p>
</dd>

### -param <i>InsertContext</i> [in, optional]

<dd>
<p>Pointer to a driver-defined context value. This parameter is passed to the driver's <a href="https://msdn.microsoft.com/library/windows/hardware/ff542956">CsqInsertIrpEx</a> routine, if it has one. Otherwise, this parameter is ignored.</p>
</dd>
</dl>

## -returns
<p>If the <i>Csq</i> parameter was initialized with <a href="https://msdn.microsoft.com/library/windows/hardware/ff549054">IoCsqInitialize</a>, <b>IoCsqInsertIrpEx</b> always returns STATUS_SUCCESS. If <i>Csq</i> was initialized with <b>IoCsqInitializeEx</b>, <b>IoCsqInsertIrpEx</b> returns the value that was returned by the driver's <a href="https://msdn.microsoft.com/library/windows/hardware/ff542956">CsqInsertIrpEx</a> routine.</p>

## -remarks
<p><b>IoCsqInsertIrpEx</b> uses the queue's dispatch routines to insert the IRP. The <b>IoCsqInsertIrpEx</b> routine:</p>

<p>Calls the queue's <a href="https://msdn.microsoft.com/library/windows/hardware/ff542934">CsqAcquireLock</a> routine to lock the queue.</p>

<p>If the queue's <a href="https://msdn.microsoft.com/library/windows/hardware/ff550560">IO_CSQ</a> structure was initialized by <a href="https://msdn.microsoft.com/library/windows/hardware/ff549054">IoCsqInitialize</a>, <b>IoCsqInsertIrpEx</b> calls the queue's <a href="https://msdn.microsoft.com/library/windows/hardware/ff542947">CsqInsertIrp</a> routine to insert the IRP. If the queue's <b>IO_CSQ</b> structure was initialized by <a href="https://msdn.microsoft.com/library/windows/hardware/ff549060">IoCsqInitializeEx</a>, <b>IoCsqInsertIrpEx</b> calls the queue's <a href="https://msdn.microsoft.com/library/windows/hardware/ff542956">CsqInsertIrpEx</a> routine to insert the IRP, and passes the <i>InsertContext</i> parameter as the <i>InsertContext</i> parameter of <i>CsqInsertIrpEx</i>.</p>

<p>Calls the queue's <a href="https://msdn.microsoft.com/library/windows/hardware/ff542965">CsqReleaseLock</a> routine to unlock the queue.</p>

<p>If the IRP to be inserted has already been canceled, <b>IoCsqInsertIrpEx</b> does not attempt to insert the IRP into the queue.</p>

<p>For more information, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff540755">Cancel-Safe IRP Queues</a>.</p>

<p>Note that <b>IoCsq<i>Xxx</i></b> routines use the <b>DriverContext</b>[3] member of the IRP to hold IRP context information. Drivers that use these routines to queue IRPs must leave that member unused.</p>

<p>Callers of <b>IoCsqInsertIrpEx</b> must be running at an IRQL &lt;= DISPATCH_LEVEL. The driver's callback routines must work correctly at this IRQL. </p>

<p><b>IoCsqInsertIrpEx</b> uses the queue's dispatch routines to insert the IRP. The <b>IoCsqInsertIrpEx</b> routine:</p>

<p>Calls the queue's <a href="https://msdn.microsoft.com/library/windows/hardware/ff542934">CsqAcquireLock</a> routine to lock the queue.</p>

<p>If the queue's <a href="https://msdn.microsoft.com/library/windows/hardware/ff550560">IO_CSQ</a> structure was initialized by <a href="https://msdn.microsoft.com/library/windows/hardware/ff549054">IoCsqInitialize</a>, <b>IoCsqInsertIrpEx</b> calls the queue's <a href="https://msdn.microsoft.com/library/windows/hardware/ff542947">CsqInsertIrp</a> routine to insert the IRP. If the queue's <b>IO_CSQ</b> structure was initialized by <a href="https://msdn.microsoft.com/library/windows/hardware/ff549060">IoCsqInitializeEx</a>, <b>IoCsqInsertIrpEx</b> calls the queue's <a href="https://msdn.microsoft.com/library/windows/hardware/ff542956">CsqInsertIrpEx</a> routine to insert the IRP, and passes the <i>InsertContext</i> parameter as the <i>InsertContext</i> parameter of <i>CsqInsertIrpEx</i>.</p>

<p>Calls the queue's <a href="https://msdn.microsoft.com/library/windows/hardware/ff542965">CsqReleaseLock</a> routine to unlock the queue.</p>

<p>If the IRP to be inserted has already been canceled, <b>IoCsqInsertIrpEx</b> does not attempt to insert the IRP into the queue.</p>

<p>For more information, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff540755">Cancel-Safe IRP Queues</a>.</p>

<p>Note that <b>IoCsq<i>Xxx</i></b> routines use the <b>DriverContext</b>[3] member of the IRP to hold IRP context information. Drivers that use these routines to queue IRPs must leave that member unused.</p>

<p>Callers of <b>IoCsqInsertIrpEx</b> must be running at an IRQL &lt;= DISPATCH_LEVEL. The driver's callback routines must work correctly at this IRQL. </p>

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
<p>Available in Windows Server 2003 and later versions of the Windows operating system. The routine is also available in the Csq.lib library that ships with the Windows Driver Kit (WDK) and the Driver Development Kit (DDK) for Windows Server 2003. Drivers that must also work for on Windows XP, Windows 2000, and Windows 98/Me can instead link to Csq.lib to use the routine.</p>
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
<p>&lt;= DISPATCH_LEVEL (see Remarks section)</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/hh975154">IoAllocateFree</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff549661">IoReuseIrp</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff547319">IrpCancelField</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975207">RemoveLockCheck</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975208">RemoveLockForward</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975209">RemoveLockForward2</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975210">RemoveLockForwardDeviceControl</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975211">RemoveLockForwardDeviceControl2</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975212">RemoveLockForwardDeviceControlInternal</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975213">RemoveLockForwardDeviceControlInternal2</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975214">RemoveLockForwardRead</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975215">RemoveLockForwardRead2</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975216">RemoveLockForwardWrite</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975217">RemoveLockForwardWrite2</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975237">RemoveLockReleaseCleanup</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975238">RemoveLockReleaseClose</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975239">RemoveLockReleaseCreate</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975240">RemoveLockReleaseDeviceControl</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975241">RemoveLockReleaseInternalDeviceControl</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975243">RemoveLockReleasePower</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975244">RemoveLockReleaseRead</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975245">RemoveLockReleaseShutdown</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975246">RemoveLockReleaseSystemControl</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975247">RemoveLockReleaseWrite</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550560">IO_CSQ</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550567">IO_CSQ_IRP_CONTEXT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549054">IoCsqInitialize</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549060">IoCsqInitializeEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549066">IoCsqInsertIrp</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549070">IoCsqRemoveIrp</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549072">IoCsqRemoveNextIrp</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542934">CsqAcquireLock</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542940">CsqCompleteCanceledIrp</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542947">CsqInsertIrp</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542956">CsqInsertIrpEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542959">CsqPeekNextIrp</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542965">CsqReleaseLock</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542968">CsqRemoveIrp</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20IoCsqInsertIrpEx routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>