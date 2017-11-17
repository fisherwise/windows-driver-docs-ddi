---
UID: NF.rxcontx.RxInitializeContext
title: RxInitializeContext
author: windows-driver-content
description: RxInitializeContext initializes an existing RX_CONTEXT data structure.
old-location: ifsk\rxinitializecontext.htm
ms.assetid: 71b595be-61ac-4a8f-af5e-d504e5091e0c
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: ifsk
req.header: rxcontx.h
req.include-header: Rxprocs.h  rxcontx.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RxInitializeContext
req.alt-loc: rxcontx.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: <= APC_LEVEL
ms.keywords: RxInitializeContext
req.iface: 
req.product: Windows 10 or later.
---

# RxInitializeContext function



## -description
<p><b>RxInitializeContext</b> initializes an existing RX_CONTEXT data structure. </p>


## -syntax

````
VOID RxInitializeContext(
  _In_opt_ PIRP                 Irp,
  _In_     PRDBSS_DEVICE_OBJECT RxDeviceObject,
  _In_     ULONG                InitialContextFlags,
  _Inout_  PRX_CONTEXT          RxContext
);
````


## -parameters
<dl>

### -param <i>Irp</i> [in, optional]

<dd>
<p>A pointer to the IRP to be encapsulated by this RX_CONTEXT structure.</p>
</dd>

### -param <i>RxDeviceObject</i> [in]

<dd>
<p>A pointer to the device object to which this RX_CONTEXT and IRP apply.</p>
</dd>

### -param <i>InitialContextFlags</i> [in]

<dd>
<p>The set of initial values for <i>Flags</i> member of the RX_CONTEXT data structure to be stored in the RX_CONTEXT structure. These initial values can be any combination of the following enumerations:</p>
<p></p>
<dl>

### -param <a id="RX_CONTEXT_FLAG_WAIT"></a><a id="rx_context_flag_wait"></a>RX_CONTEXT_FLAG_WAIT

<dd>
<p>When this value is set, the IRP should be not be posted for later execution by the file system process, but should be waited on to complete.</p>
</dd>

### -param <a id="RX_CONTEXT_FLAG_MUST_SUCCEED"></a><a id="rx_context_flag_must_succeed"></a>RX_CONTEXT_FLAG_MUST_SUCCEED

<dd>
<p>When this value is set, the operation must succeed. This value is not currently used by RDBSS, but it may be used by network mini-redirector drivers. </p>
</dd>

### -param <a id="RX_CONTEXT_FLAG_MUST_SUCCEED_NONBLOCKING"></a><a id="rx_context_flag_must_succeed_nonblocking"></a>RX_CONTEXT_FLAG_MUST_SUCCEED_NONBLOCKING

<dd>
<p>When this value is set, the operation must succeed for non-blocking operations. This value is not currently used by RDBSS, but it may be used by network mini-redirector drivers. </p>
</dd>
</dl>
</dd>

### -param <i>RxContext</i> [in, out]

<dd>
<p>Pointer to the RX_CONTEXT to be initialized.</p>
</dd>
</dl>

## -returns
<p>None </p>

## -remarks
<p><b>RxInitializeContext</b> is called internally by the <b>RxCreateRxContext</b> routine. So the <b>RxInitializeContext</b> routine would normally only be used by network min-redirector drivers that allocate RX_CONTEXT structures directly rather than calling the <b>RxCreateRxContext</b> routine to allocate and initialize an RX_CONTEXT structure. </p>

<p>If the <i>Irp</i> parameter is configured for asynchronous operation, then the <b>Flags</b> member of the RX_CONTEXT structure pointed to by <i>RxContext</i> also has the following value set:</p>

<p></p><dl>
<dt><a id="RX_CONTEXT_FLAG_ASYNC_OPERATION"></a><a id="rx_context_flag_async_operation"></a>RX_CONTEXT_FLAG_ASYNC_OPERATION</dt>
<dd>
<p>When this value is set, the RX_CONTEXT structure is tagged for asynchronous operation.</p>
</dd>
</dl><p>When this value is set, the RX_CONTEXT structure is tagged for asynchronous operation.</p>

<p>RX_CONTEXT_FLAG_ASYNC_OPERATION is also set for the following conditions:</p>

<p>The <b>MajorFunction</b> member of the <i>Irp</i> is IRP_MJ_READ, IRP_MJ_WRITE, or IRP_MJ_DEVICE_CONTROL.</p>

<p>The <b>MajorFunction</b> member of the <i>Irp</i> is an IRP_MJ_DIRECTORY_CONTROL and the <b>MinorFunction</b> member of the <i>IRP</i> is an IRP_MN_NOTIFY_CHANGE_DIRECTORY.</p>

<p>The <b>MajorFunction</b> member of the <i>Irp</i> is an IRP_MJ_FILE_SYSTEM_CONTROL and <b>NetRoot</b> member of the associated FCB is not <b>NULL</b> and the <b>Type</b> member of the NET_ROOT is NET_ROOT_PIPE.</p>

<p>If this is a recursive file system call (the TopLevelIrp member in the thread local storage is the current <i>Irp</i>) then the <b>Flags</b> member of <i>RxContext</i> also has the following value set:</p>

<p></p><dl>
<dt><a id="RX_CONTEXT_FLAG_RECURSIVE_CALL"></a><a id="rx_context_flag_recursive_call"></a>RX_CONTEXT_FLAG_RECURSIVE_CALL</dt>
<dd>
<p>When this value is set, the RX_CONTEXT structure is tagged as a recursive call.</p>
</dd>
</dl><p>When this value is set, the RX_CONTEXT structure is tagged as a recursive call.</p>

<p>If the <i>RxDeviceObject</i> parameter indicates that this is the top level RDBSS device object, then the <b>Flags</b> member of the RX_CONTEXT structure also has the following value set:</p>

<p></p><dl>
<dt><a id="RX_CONTEXT_FLAG_THIS_DEVICE_TOP_LEVEL"></a><a id="rx_context_flag_this_device_top_level"></a>RX_CONTEXT_FLAG_THIS_DEVICE_TOP_LEVEL</dt>
<dd>
<p>When this value is set, the RX_CONTEXT structure is tagged as using the top level device object.</p>
</dd>
</dl><p>When this value is set, the RX_CONTEXT structure is tagged as using the top level device object.</p>

<p>If the <i>Irp</i> FileObject Flags member has the FO_WRITE_THROUGH option set, then the <b>Flags</b> member of the RX_CONTEXT structure also has the following value set:</p>

<p></p><dl>
<dt><a id="RX_CONTEXT_FLAG_WRITE_THROUGH"></a><a id="rx_context_flag_write_through"></a>RX_CONTEXT_FLAG_WRITE_THROUGH</dt>
<dd>
<p>When this value is set, the RX_CONTEXT structure is tagged as set to write through mode.</p>
</dd>
</dl><p>When this value is set, the RX_CONTEXT structure is tagged as set to write through mode.</p>

<p><b>RxInitializeContext</b> sets a number of other members in the RX_CONTEXT structure including the following:</p>

<p>Sets the proper <b>NodeTypeCode</b>, <b>NodeByteSize</b>, <b>SerialNumber</b>, <b>RxDeviceObject</b>, and initializes the <b>ReferenceCount</b> to 1.</p>

<p>Initializes the SyncEvent</p>

<p>Initialize the associated ScavengerEntry</p>

<p>Initializes the list entry of BlockedOperations</p>

<p>Sets the RX_CONTEXT members based on the <i>Irp</i>. These include <b>CurrentIrp</b>, <b>OriginalThread</b>, <b>MajorFunction</b>, <b>MinorFunction</b>, <b>CurrentIrpSp</b>, <b>pFcb</b>, <b>NonPagedFcb</b>, <b>pFobx</b>, <b>pRelevantSrvOpen</b>, and <b>FobxSerialNumber</b> members.</p>

<p><b>RxInitializeContext</b> is called internally by the <b>RxCreateRxContext</b> routine. So the <b>RxInitializeContext</b> routine would normally only be used by network min-redirector drivers that allocate RX_CONTEXT structures directly rather than calling the <b>RxCreateRxContext</b> routine to allocate and initialize an RX_CONTEXT structure. </p>

<p>If the <i>Irp</i> parameter is configured for asynchronous operation, then the <b>Flags</b> member of the RX_CONTEXT structure pointed to by <i>RxContext</i> also has the following value set:</p>

<p></p><dl>
<dt><a id="RX_CONTEXT_FLAG_ASYNC_OPERATION"></a><a id="rx_context_flag_async_operation"></a>RX_CONTEXT_FLAG_ASYNC_OPERATION</dt>
<dd>
<p>When this value is set, the RX_CONTEXT structure is tagged for asynchronous operation.</p>
</dd>
</dl><p>When this value is set, the RX_CONTEXT structure is tagged for asynchronous operation.</p>

<p>RX_CONTEXT_FLAG_ASYNC_OPERATION is also set for the following conditions:</p>

<p>The <b>MajorFunction</b> member of the <i>Irp</i> is IRP_MJ_READ, IRP_MJ_WRITE, or IRP_MJ_DEVICE_CONTROL.</p>

<p>The <b>MajorFunction</b> member of the <i>Irp</i> is an IRP_MJ_DIRECTORY_CONTROL and the <b>MinorFunction</b> member of the <i>IRP</i> is an IRP_MN_NOTIFY_CHANGE_DIRECTORY.</p>

<p>The <b>MajorFunction</b> member of the <i>Irp</i> is an IRP_MJ_FILE_SYSTEM_CONTROL and <b>NetRoot</b> member of the associated FCB is not <b>NULL</b> and the <b>Type</b> member of the NET_ROOT is NET_ROOT_PIPE.</p>

<p>If this is a recursive file system call (the TopLevelIrp member in the thread local storage is the current <i>Irp</i>) then the <b>Flags</b> member of <i>RxContext</i> also has the following value set:</p>

<p></p><dl>
<dt><a id="RX_CONTEXT_FLAG_RECURSIVE_CALL"></a><a id="rx_context_flag_recursive_call"></a>RX_CONTEXT_FLAG_RECURSIVE_CALL</dt>
<dd>
<p>When this value is set, the RX_CONTEXT structure is tagged as a recursive call.</p>
</dd>
</dl><p>When this value is set, the RX_CONTEXT structure is tagged as a recursive call.</p>

<p>If the <i>RxDeviceObject</i> parameter indicates that this is the top level RDBSS device object, then the <b>Flags</b> member of the RX_CONTEXT structure also has the following value set:</p>

<p></p><dl>
<dt><a id="RX_CONTEXT_FLAG_THIS_DEVICE_TOP_LEVEL"></a><a id="rx_context_flag_this_device_top_level"></a>RX_CONTEXT_FLAG_THIS_DEVICE_TOP_LEVEL</dt>
<dd>
<p>When this value is set, the RX_CONTEXT structure is tagged as using the top level device object.</p>
</dd>
</dl><p>When this value is set, the RX_CONTEXT structure is tagged as using the top level device object.</p>

<p>If the <i>Irp</i> FileObject Flags member has the FO_WRITE_THROUGH option set, then the <b>Flags</b> member of the RX_CONTEXT structure also has the following value set:</p>

<p></p><dl>
<dt><a id="RX_CONTEXT_FLAG_WRITE_THROUGH"></a><a id="rx_context_flag_write_through"></a>RX_CONTEXT_FLAG_WRITE_THROUGH</dt>
<dd>
<p>When this value is set, the RX_CONTEXT structure is tagged as set to write through mode.</p>
</dd>
</dl><p>When this value is set, the RX_CONTEXT structure is tagged as set to write through mode.</p>

<p><b>RxInitializeContext</b> sets a number of other members in the RX_CONTEXT structure including the following:</p>

<p>Sets the proper <b>NodeTypeCode</b>, <b>NodeByteSize</b>, <b>SerialNumber</b>, <b>RxDeviceObject</b>, and initializes the <b>ReferenceCount</b> to 1.</p>

<p>Initializes the SyncEvent</p>

<p>Initialize the associated ScavengerEntry</p>

<p>Initializes the list entry of BlockedOperations</p>

<p>Sets the RX_CONTEXT members based on the <i>Irp</i>. These include <b>CurrentIrp</b>, <b>OriginalThread</b>, <b>MajorFunction</b>, <b>MinorFunction</b>, <b>CurrentIrpSp</b>, <b>pFcb</b>, <b>NonPagedFcb</b>, <b>pFobx</b>, <b>pRelevantSrvOpen</b>, and <b>FobxSerialNumber</b> members.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt>Desktop</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Rxcontx.h (include Rxprocs.h and rxcontx.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&lt;= APC_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554340">RxCompleteRequest</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554348">RxCompleteRequest_Real</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554367">RxCreateRxContext</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554388">RxDereference</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554393">RxDereferenceAndDeleteRxContext_Real</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554643">RxPrepareContextForReuse</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/8418ed17-39f0-4a3b-9eb5-453c7cc2ae98">RxResumeBlockedOperations_Serially</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff557377">__RxSynchronizeBlockingOperations</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff557382">__RxSynchronizeBlockingOperationsMaybeDroppingFcbLock</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554751">RX_CONTEXT</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20RxInitializeContext function%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>