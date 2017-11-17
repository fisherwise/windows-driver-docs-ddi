---
UID: NF.storport.StorPortIssueDpc
title: StorPortIssueDpc
author: windows-driver-content
description: The StorPortIssueDpc routine issues a deferred procedure call (DPC).
old-location: storage\storportissuedpc.htm
ms.assetid: a0c46c51-f6c4-4609-9dba-b730f33c3ed6
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: Storage
req.header: storport.h
req.include-header: Storport.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: StorPortIssueDpc
req.alt-loc: storport.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: 
ms.keywords: StorPortIssueDpc
req.iface: 
req.product: Windows 10 or later.
---

# StorPortIssueDpc function



## -description
<p>The <b>StorPortIssueDpc</b> routine issues a deferred procedure call (DPC). </p>


## -syntax

````
BOOLEAN StorPortIssueDpc(
  _In_ PVOID     DeviceExtension,
  _In_ PSTOR_DPC Dpc,
  _In_ PVOID     SystemArgument1,
  _In_ PVOID     SystemArgument2
);
````


## -parameters
<dl>

### -param <i>DeviceExtension</i> [in]

<dd>
<p>Pointer to the per-adapter device extension. </p>
</dd>

### -param <i>Dpc</i> [in]

<dd>
<p>Pointer to a buffer containing an initialized DPC object of type <a href="https://msdn.microsoft.com/library/windows/hardware/ff567579">STOR_DPC</a> returned by the <a href="https://msdn.microsoft.com/library/windows/hardware/ff567110">StorPortInitializeDpc</a> routine. </p>
</dd>

### -param <i>SystemArgument1</i> [in]

<dd>
<p>Pointer to caller-supplied information that will be passed to the deferred routine. </p>
</dd>

### -param <i>SystemArgument2</i> [in]

<dd>
<p>Pointer to caller-supplied information that will be passed to the deferred routine. </p>
</dd>
</dl>

## -returns
<p>The <b>StorPortIssueDpc</b> routine returns <b>TRUE</b> if the DPC was successfully inserted into the DPC queue, and <b>FALSE</b> otherwise. </p>

## -remarks
<p>The <b>StorPortIssueDpc</b>  routine calls the <a href="https://msdn.microsoft.com/library/windows/hardware/ff552185">KeInsertQueueDpc</a> kernel routine to queue the DPC. The <b>KeInsertQueueDpc</b> kernel routine does not allow a DPC to be queued multiple times. Thus, if the DPC object specified by the <i>Dpc</i> parameter is already in the DPC queue, <b>KeInsertQueueDpc</b> ignores the queue request. This ensures that a deferred routine initialized with <a href="https://msdn.microsoft.com/library/windows/hardware/ff567110">StorPortInitializeDpc</a> is always synchronized with itself. In other words, the caller does not need to sequentialize calls to the <b>StorPortIssueDpc</b> routine to ensure that multiple instances the routine do not run simultaneously. </p>

<p>If a miniport driver has multiple work-items that must be performed by the same DPC, the miniport driver must ensure that each work item completes before issuing the DPC for the next work item. </p>

<p>The <b>StorPortIssueDpc</b>  routine calls the <a href="https://msdn.microsoft.com/library/windows/hardware/ff552185">KeInsertQueueDpc</a> kernel routine to queue the DPC. The <b>KeInsertQueueDpc</b> kernel routine does not allow a DPC to be queued multiple times. Thus, if the DPC object specified by the <i>Dpc</i> parameter is already in the DPC queue, <b>KeInsertQueueDpc</b> ignores the queue request. This ensures that a deferred routine initialized with <a href="https://msdn.microsoft.com/library/windows/hardware/ff567110">StorPortInitializeDpc</a> is always synchronized with itself. In other words, the caller does not need to sequentialize calls to the <b>StorPortIssueDpc</b> routine to ensure that multiple instances the routine do not run simultaneously. </p>

<p>If a miniport driver has multiple work-items that must be performed by the same DPC, the miniport driver must ensure that each work item completes before issuing the DPC for the next work item. </p>

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
<dt>Storport.h (include Storport.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552185">KeInsertQueueDpc</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567110">StorPortInitializeDpc</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567579">STOR_DPC</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20StorPortIssueDpc routine%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>