---
UID: NF.wudfddi.IWDFIoRequest.ForwardToIoQueue
title: IWDFIoRequest::ForwardToIoQueue
author: windows-driver-content
description: The ForwardToIoQueue method forwards (that is, requeues) an I/O request to one of the calling driver's I/O queues.
old-location: wdf\iwdfiorequest_forwardtoioqueue.htm
ms.assetid: 07317157-1222-4b34-89f4-d546818e9851
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: wdf
req.header: wudfddi.h
req.include-header: Wudfddi.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 1.5
req.alt-api: IWDFIoRequest.ForwardToIoQueue
req.alt-loc: WUDFx.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: Unavailable in UMDF 2.0 and later.
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: WUDFx.dll
req.irql: <= DISPATCH_LEVEL
ms.keywords: IWDFIoRequest, ForwardToIoQueue, IWDFIoRequest::ForwardToIoQueue
req.iface: IWDFIoRequest
req.product: Windows 10 or later.
---

# IWDFIoRequest::ForwardToIoQueue method



## -description
<p class="CCE_Message">[<b>Warning:</b> UMDF 2 is the latest version of UMDF and supersedes UMDF 1.  All new UMDF drivers should be written using UMDF 2.  No new features are being added to UMDF 1 and there is limited support for UMDF 1 on newer versions of Windows 10.  Universal Windows drivers must use UMDF 2.  For more info, see <a href="https://docs.microsoft.com/en-us/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2">Getting Started with UMDF</a>.]</p>
<p>The <b>ForwardToIoQueue</b> method forwards (that is, requeues) an I/O request to one of the calling driver's I/O queues.</p>


## -syntax

````
HRESULT ForwardToIoQueue(
  [in] IWDFIoQueue *pDestination
);
````


## -parameters
<dl>

### -param <i>pDestination</i> [in]

<dd>
<p>A pointer to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff558943">IWDFIoQueue</a> interface for the destination queue object.</p>
</dd>
</dl>

## -returns
<p><b>ForwardToIoQueue</b> returns S_OK if the operation succeeds. Otherwise, this method returns one of the error codes that are defined in Winerror.h.</p>

## -remarks
<p>The driver must own the I/O request and must have obtained the request from one of its I/O queues.</p>

<p>The source and destination queues cannot be the same. In other words, the driver cannot call <b>ForwardToIoQueue</b> to return a request to the queue that it came from. To return an I/O request to the I/O queue that it came from, the driver can call <a href="https://msdn.microsoft.com/library/windows/hardware/ff559028">IWDFIoRequest2::Requeue</a>.</p>

<p>Both the source and destination queues must belong to the same device.</p>

<p>Also, the <b>ForwardToIoQueue</b> method cannot requeue a request that the driver obtained by calling the <a href="https://msdn.microsoft.com/library/windows/hardware/ff558967">IWDFIoQueue::RetrieveNextRequest</a> method.</p>

<p>The request cannot be cancelable. If the driver previously called the <a href="https://msdn.microsoft.com/library/windows/hardware/ff559146">IWDFIoRequest::MarkCancelable</a> method to make the request cancelable, the driver must call the <a href="https://msdn.microsoft.com/library/windows/hardware/ff559163">IWDFIoRequest::UnmarkCancelable</a> method before calling <b>ForwardToIoQueue</b>.</p>

<p>The following code example shows how to forward a request to another queue if the request's buffer is insufficient to hold the required information.</p>

<p>The driver must own the I/O request and must have obtained the request from one of its I/O queues.</p>

<p>The source and destination queues cannot be the same. In other words, the driver cannot call <b>ForwardToIoQueue</b> to return a request to the queue that it came from. To return an I/O request to the I/O queue that it came from, the driver can call <a href="https://msdn.microsoft.com/library/windows/hardware/ff559028">IWDFIoRequest2::Requeue</a>.</p>

<p>Both the source and destination queues must belong to the same device.</p>

<p>Also, the <b>ForwardToIoQueue</b> method cannot requeue a request that the driver obtained by calling the <a href="https://msdn.microsoft.com/library/windows/hardware/ff558967">IWDFIoQueue::RetrieveNextRequest</a> method.</p>

<p>The request cannot be cancelable. If the driver previously called the <a href="https://msdn.microsoft.com/library/windows/hardware/ff559146">IWDFIoRequest::MarkCancelable</a> method to make the request cancelable, the driver must call the <a href="https://msdn.microsoft.com/library/windows/hardware/ff559163">IWDFIoRequest::UnmarkCancelable</a> method before calling <b>ForwardToIoQueue</b>.</p>

<p>The following code example shows how to forward a request to another queue if the request's buffer is insufficient to hold the required information.</p>

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
<p>End of support</p>
</th>
<td width="70%">
<p>Unavailable in UMDF 2.0 and later.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum UMDF version</p>
</th>
<td width="70%">
<p>1.5</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wudfddi.h (include Wudfddi.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>WUDFx.dll</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff558985">IWDFIoRequest</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff558943">IWDFIoQueue</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff558967">IWDFIoQueue::RetrieveNextRequest</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff559146">IWDFIoRequest::MarkCancelable</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff559163">IWDFIoRequest::UnmarkCancelable</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20IWDFIoRequest::ForwardToIoQueue method%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>