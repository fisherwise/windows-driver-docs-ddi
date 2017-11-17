---
UID: NF.wdfworkitem.WdfWorkItemFlush
title: WdfWorkItemFlush
author: windows-driver-content
description: The WdfWorkItemFlush method returns after a specified work item has been serviced.
old-location: wdf\wdfworkitemflush.htm
ms.assetid: 5868dd01-17ba-4edf-b665-c90d2b1aa2ba
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: wdf
req.header: wdfworkitem.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 2.0
req.alt-api: WdfWorkItemFlush
req.alt-loc: Wdf01000.sys,Wdf01000.sys.dll,WUDFx02000.dll,WUDFx02000.dll.dll
req.ddi-compliance: DriverCreate, KmdfIrql, KmdfIrql2
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Wdf01000.sys (KMDF); 
WUDFx02000.dll (UMDF)
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: WdfWorkItemFlush
req.iface: 
req.product: Windows 10 or later.
---

# WdfWorkItemFlush function



## -description
<p class="CCE_Message">[Applies to KMDF and UMDF]</p>
<p>The <b>WdfWorkItemFlush</b> method returns after a specified work item has been serviced.</p>


## -syntax

````
VOID WdfWorkItemFlush(
  _In_ WDFWORKITEM WorkItem
);
````


## -parameters
<dl>

### -param <i>WorkItem</i> [in]

<dd>
<p>A handle to a framework work-item object that is obtained from a previous call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff551201">WdfWorkItemCreate</a>.</p>
</dd>
</dl>

## -returns
<p>None.</p>

<p>A bug check occurs if the driver supplies an invalid object handle.

</p>

## -remarks
<p>If your driver calls the <b>WdfWorkItemFlush</b> method, the method does not return until a system worker thread has removed the specified work item from the work-item queue and called the driver's <a href="https://msdn.microsoft.com/2a2811de-9024-40a8-b8af-b61ca4100218">EvtWorkItem</a> callback function, and the <i>EvtWorkItem</i> callback function has subsequently returned after processing the work item.</p>

<p>Most drivers that use work items do not need to call <b>WdfWorkItemFlush</b>. A driver might call <b>WdfWorkItemFlush</b> if it must synchronize completion of work items with the removal of a remote I/O target. In this case, the driver can call <b>WdfWorkItemFlush</b> from within its <a href="https://msdn.microsoft.com/cb7c97e5-081e-44fc-a759-9a1ae81de41c">EvtIoTargetQueryRemove</a> callback function. </p>

<p>For more information about work items, see <a href="wdf.using_framework_work_items">Using Framework Work Items</a>.</p>

<p>The following code example is an <a href="https://msdn.microsoft.com/cb7c97e5-081e-44fc-a759-9a1ae81de41c">EvtIoTargetQueryRemove</a> callback function from the <a href="wdf.sample_kmdf_drivers">Toaster</a> sample driver. </p>

<p>If your driver calls the <b>WdfWorkItemFlush</b> method, the method does not return until a system worker thread has removed the specified work item from the work-item queue and called the driver's <a href="https://msdn.microsoft.com/2a2811de-9024-40a8-b8af-b61ca4100218">EvtWorkItem</a> callback function, and the <i>EvtWorkItem</i> callback function has subsequently returned after processing the work item.</p>

<p>Most drivers that use work items do not need to call <b>WdfWorkItemFlush</b>. A driver might call <b>WdfWorkItemFlush</b> if it must synchronize completion of work items with the removal of a remote I/O target. In this case, the driver can call <b>WdfWorkItemFlush</b> from within its <a href="https://msdn.microsoft.com/cb7c97e5-081e-44fc-a759-9a1ae81de41c">EvtIoTargetQueryRemove</a> callback function. </p>

<p>For more information about work items, see <a href="wdf.using_framework_work_items">Using Framework Work Items</a>.</p>

<p>The following code example is an <a href="https://msdn.microsoft.com/cb7c97e5-081e-44fc-a759-9a1ae81de41c">EvtIoTargetQueryRemove</a> callback function from the <a href="wdf.sample_kmdf_drivers">Toaster</a> sample driver. </p>

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
<p>Minimum KMDF version</p>
</th>
<td width="70%">
<p>1.0</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum UMDF version</p>
</th>
<td width="70%">
<p>2.0</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdfworkitem.h (include Wdf.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Wdf01000.sys (KMDF); </dt>
<dt>WUDFx02000.dll (UMDF)</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544957">DriverCreate</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff548167">KmdfIrql</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975091">KmdfIrql2</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/2a2811de-9024-40a8-b8af-b61ca4100218">EvtWorkItem</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WdfWorkItemFlush method%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>