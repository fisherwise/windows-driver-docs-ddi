---
UID: NC.ucxcontroller.EVT_UCX_CONTROLLER_RESET
title: EVT_UCX_CONTROLLER_RESET
author: windows-driver-content
description: The client driver's implementation that UCX calls to reset the controller.
old-location: buses\evt_ucx_controller_reset.htm
ms.assetid: 8c01d677-5ce4-44f6-8342-2152e851de87
ms.author: windowsdriverdev
ms.date: 11/3/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: usbref
req.header: ucxcontroller.h
req.include-header: Ucxclass.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 2.0
req.alt-api: PEVT_UCX_CONTROLLER_RESET
req.alt-loc: Ucxcontroller.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: UCM_PD_REQUEST_DATA_OBJECT_INIT_ULONG
req.iface: 
req.product: Windows 10 or later.
---

# EVT_UCX_CONTROLLER_RESET callback



## -description
<p>The client driver's implementation that UCX calls to reset the controller.</p>


## -prototype

````
EVT_UCX_CONTROLLER_RESET EvtUcxControllerReset;

VOID EvtUcxControllerReset(
  _In_ UCXCONTROLLER UcxController
)
{ ... }

typedef EVT_UCX_CONTROLLER_RESET PEVT_UCX_CONTROLLER_RESET;
````


## -parameters
<dl>

### -param <i>UcxController</i> [in]

<dd>
<p> A handle to the UCX controller that the client driver received in a previous call to  the <a href="https://msdn.microsoft.com/library/windows/hardware/mt188033">UcxControllerCreate</a> method.</p>
</dd>
</dl>

## -returns
<p>This callback function does not return a value.</p>

## -remarks
<p>The UCX client driver registers its <i>EVT_UCX_CONTROLLER_RESET</i> implementation with the USB host controller extension (UCX) by calling the <a href="https://msdn.microsoft.com/library/windows/hardware/mt188033">UcxControllerCreate</a> method.</p>

<p>The client driver indicates completion of this event by calling the <a href="https://msdn.microsoft.com/library/windows/hardware/mt188035">UcxControllerResetComplete</a> method. Doing so ensures that UCX does not call <i>EVT_UCX_CONTROLLER_RESET</i> a second time before this event callback completes.</p>

<p>If the client driver calls <a href="https://msdn.microsoft.com/library/windows/hardware/mt188034">UcxControllerNeedsReset</a>, UCX calls this event callback function.  However, UCX may call this event callback function even when the client driver has not called <b>UcxControllerNeedsReset</b>. </p>

<p>The UCX client driver registers its <i>EVT_UCX_CONTROLLER_RESET</i> implementation with the USB host controller extension (UCX) by calling the <a href="https://msdn.microsoft.com/library/windows/hardware/mt188033">UcxControllerCreate</a> method.</p>

<p>The client driver indicates completion of this event by calling the <a href="https://msdn.microsoft.com/library/windows/hardware/mt188035">UcxControllerResetComplete</a> method. Doing so ensures that UCX does not call <i>EVT_UCX_CONTROLLER_RESET</i> a second time before this event callback completes.</p>

<p>If the client driver calls <a href="https://msdn.microsoft.com/library/windows/hardware/mt188034">UcxControllerNeedsReset</a>, UCX calls this event callback function.  However, UCX may call this event callback function even when the client driver has not called <b>UcxControllerNeedsReset</b>. </p>

## -requirements
<table>
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
<dt>Ucxcontroller.h (include Ucxclass.h)</dt>
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
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/mt188033">UcxControllerCreate</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/mt188035">UcxControllerResetComplete</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/mt188034">UcxControllerNeedsReset</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [usbref\buses]:%20EVT_UCX_CONTROLLER_RESET callback function%20 RELEASE:%20(11/3/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>