---
UID: NF.rxcontx.RxDereferenceAndDeleteRxContext_Real
title: RxDereferenceAndDeleteRxContext_Real
author: windows-driver-content
description: RxDereferenceAndDeleteRxContext_Real dereferences an RX_CONTEXT data structure and if the ReferenceCount member goes to zero, then it deallocates and removes the specified RX_CONTEXT structure from the RDBSS in-memory data structures.
old-location: ifsk\rxdereferenceanddeleterxcontext_real.htm
ms.assetid: a2a2bb57-6f5c-4bc9-8564-ab0db2efd872
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
req.alt-api: RxDereferenceAndDeleteRxContext_Real
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
ms.keywords: RxDereferenceAndDeleteRxContext_Real
req.iface: 
req.product: Windows 10 or later.
---

# RxDereferenceAndDeleteRxContext_Real function



## -description
<p><b>RxDereferenceAndDeleteRxContext_Real</b> dereferences an RX_CONTEXT data structure and if the <b>ReferenceCount</b> member goes to zero, then it deallocates and removes the specified RX_CONTEXT structure from the RDBSS in-memory data structures. </p>


## -syntax

````
VOID RxDereferenceAndDeleteRxContext_Real(
  _In_ PRX_CONTEXT RxContext
);
````


## -parameters
<dl>

### -param <i>RxContext</i> [in]

<dd>
<p>A pointer to the RX_CONTEXT structure to be removed.</p>
</dd>
</dl>

## -returns
<p>None </p>

## -remarks
<p><b>RxDereferenceAndDeleteRxContext_Real</b> is called by routines other than <b>RxCompleteRequest</b> during asynchronous requests that touch the <i>RxContext</i> parameter in either the initiating thread or in some other thread. Thus, the RX_CONTEXT data structure is reference counted and finalized on the last dereference.</p>

<p>If the <b>ReferenceCount</b> member of the RX_CONTEXT structure pointed to by the <i>RxContext</i> parameter is not zero after being derefenced (decremented) by the <b>RxDereferenceAndDeleteRxContext_Real</b> routine, then <b>RxDereferenceAndDeleteRxContext_Real</b> causes the system to ASSERT on checked builds. </p>

<p>The <b>RxDereferenceAndDeleteRxContext_Real</b> routine makes a number of specific checks before removing an RX_CONTEXT. These checks include the following:</p>

<p>If the <b>AcquireReleaseFcbTrackerX</b> member is 0, then <b>RxDereferenceAndDeleteRxContext_Real</b> causes the system to ASSERT on checked builds.</p>

<p>If the <b>NumberOfActiveContexts</b> member of the associated RDBSS_DEVICE_OBJECT structure pointed to <b><i>RxContext</i></b><b>-&gt;RxDeviceObject</b> is not zero after being dereferenced (decremented) and the <b>StartStopContext.pStopContext</b> member of the associated RDBSS_DEVICE_OBJECT structure is not <b>NULL</b>, then <b>RxDereferenceAndDeleteRxContext_Real</b> will signal the SyncEvent on the RX_CONTEXT structure in the <b>StartStopContext.pStopContext</b> member.</p>

<p>If the RX_CONTEXT structure was allocated from non-page pool memory (the <b>Flags</b> member of the RX_CONTEXT structure has the RX_CONTEXT_FLAG_FROM_POOL option set), then the RX_CONTEXT structure pointed to by the <i>RxContext</i> parameter will be returned to an internal RDBSS lookaside list or to non-paged pool memory. </p>

<p><b>RxDereferenceAndDeleteRxContext_Real</b> is called by routines other than <b>RxCompleteRequest</b> during asynchronous requests that touch the <i>RxContext</i> parameter in either the initiating thread or in some other thread. Thus, the RX_CONTEXT data structure is reference counted and finalized on the last dereference.</p>

<p>If the <b>ReferenceCount</b> member of the RX_CONTEXT structure pointed to by the <i>RxContext</i> parameter is not zero after being derefenced (decremented) by the <b>RxDereferenceAndDeleteRxContext_Real</b> routine, then <b>RxDereferenceAndDeleteRxContext_Real</b> causes the system to ASSERT on checked builds. </p>

<p>The <b>RxDereferenceAndDeleteRxContext_Real</b> routine makes a number of specific checks before removing an RX_CONTEXT. These checks include the following:</p>

<p>If the <b>AcquireReleaseFcbTrackerX</b> member is 0, then <b>RxDereferenceAndDeleteRxContext_Real</b> causes the system to ASSERT on checked builds.</p>

<p>If the <b>NumberOfActiveContexts</b> member of the associated RDBSS_DEVICE_OBJECT structure pointed to <b><i>RxContext</i></b><b>-&gt;RxDeviceObject</b> is not zero after being dereferenced (decremented) and the <b>StartStopContext.pStopContext</b> member of the associated RDBSS_DEVICE_OBJECT structure is not <b>NULL</b>, then <b>RxDereferenceAndDeleteRxContext_Real</b> will signal the SyncEvent on the RX_CONTEXT structure in the <b>StartStopContext.pStopContext</b> member.</p>

<p>If the RX_CONTEXT structure was allocated from non-page pool memory (the <b>Flags</b> member of the RX_CONTEXT structure has the RX_CONTEXT_FLAG_FROM_POOL option set), then the RX_CONTEXT structure pointed to by the <i>RxContext</i> parameter will be returned to an internal RDBSS lookaside list or to non-paged pool memory. </p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554502">RxInitializeContext</a>
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
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20RxDereferenceAndDeleteRxContext_Real function%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>