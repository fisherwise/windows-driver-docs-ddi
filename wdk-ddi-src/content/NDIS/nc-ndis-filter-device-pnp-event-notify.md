---
UID: NC.ndis.FILTER_DEVICE_PNP_EVENT_NOTIFY
title: FILTER_DEVICE_PNP_EVENT_NOTIFY
author: windows-driver-content
description: NDIS calls a filter driver's FilterDevicePnPEventNotify function to notify the driver of device Plug and Play (PnP) and Power Management events.Note  You must declare the function by using the FILTER_DEVICE_PNP_EVENT_NOTIFY type.
old-location: netvista\filterdevicepnpeventnotify.htm
ms.assetid: dea4ab30-ba1d-4c9c-9f00-e48cc3cc0b46
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: netvista
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Windows
req.target-min-winverclnt: Supported in NDIS 6.0 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FilterDevicePnPEventNotify
req.alt-loc: Ndis.h
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
ms.keywords: RxNameCacheInitialize
req.iface: 
---

# FILTER_DEVICE_PNP_EVENT_NOTIFY callback



## -description
<p>NDIS calls a filter driver's 
  <i>FilterDevicePnPEventNotify</i> function to notify the driver of device Plug and Play (PnP) and Power
  Management events.</p>


## -prototype

````
FILTER_DEVICE_PNP_EVENT_NOTIFY FilterDevicePnPEventNotify;

VOID FilterDevicePnPEventNotify(
  _In_ NDIS_HANDLE           FilterModuleContext,
  _In_ PNET_DEVICE_PNP_EVENT NetDevicePnPEvent
)
{ ... }
````


## -parameters
<dl>

### -param <i>FilterModuleContext</i> [in]

<dd>
<p>A handle to the context area for the filter module. The filter driver created and initialized this
     context area in the 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff540442">FilterAttach</a> function.</p>
</dd>

### -param <i>NetDevicePnPEvent</i> [in]

<dd>
<p>A pointer to a 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff568730">NET_DEVICE_PNP_EVENT</a> structure that
     describes a device Plug and Play event.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p><i>FilterDevicePnPEventNotify</i> is an optional function. If a filter driver does not use device PnP
    requests, it can set the entry point for this function to <b>NULL</b> when it calls the 
    <a href="https://msdn.microsoft.com/14381de2-36d9-4ec8-9d4e-7af3e6d8ecf3">
    NdisFRegisterFilterDriver</a> function.</p>

<p><i>FilterDevicePnPEventNotify</i> is similar to a miniport driver's 
    <a href="https://msdn.microsoft.com/e41240c0-17be-42ef-a72c-c5311115cf64">
    MiniportDevicePnPEventNotify</a> function. Filter drivers can forward these notifications to underlying
    drivers. To forward a request, call the 
    <a href="https://msdn.microsoft.com/ae5dd48b-7777-4232-89ad-ac4464e03e57">
    NdisFDevicePnPEventNotify</a> function.</p>

<p>NDIS calls 
    <i>FilterDevicePnPEventNotify</i> at IRQL = PASSIVE_LEVEL.</p>

<p>To define a <i>FilterDevicePnPEventNotify</i> function, you must first provide a function declaration that identifies the type of function you're defining. Windows provides a set of function types for drivers. Declaring a function using the function types helps <a href="NULL">Code Analysis for Drivers</a>, <a href="NULL">Static Driver Verifier</a> (SDV), and other verification tools find errors, and it's a requirement for writing drivers for the Windows operating system.</p>

<p>For example, to define a <i>FilterDevicePnPEventNotify</i> function that is named "MyDevicePnPEventNotify", use the <b>FILTER_DEVICE_PNP_EVENT_NOTIFY</b> type as shown in this code example:</p>

<p>Then, implement your function as follows:</p>

<p>The <b>FILTER_DEVICE_PNP_EVENT_NOTIFY</b> function type is defined in the Ndis.h header file. To more accurately identify errors when you run the code analysis tools, be sure to add the _Use_decl_annotations_ annotation to your function definition.  The _Use_decl_annotations_ annotation ensures that the annotations that are applied to the <b>FILTER_DEVICE_PNP_EVENT_NOTIFY</b> function type in the header file are used.  For more information about the requirements for function declarations, see <a href="NULL">Declaring Functions by Using Function Role Types for NDIS Drivers</a>.

For information about  _Use_decl_annotations_, see <a href="http://go.microsoft.com/fwlink/p/?linkid=286697">Annotating Function Behavior</a>. </p>

<p><i>FilterDevicePnPEventNotify</i> is an optional function. If a filter driver does not use device PnP
    requests, it can set the entry point for this function to <b>NULL</b> when it calls the 
    <a href="https://msdn.microsoft.com/14381de2-36d9-4ec8-9d4e-7af3e6d8ecf3">
    NdisFRegisterFilterDriver</a> function.</p>

<p><i>FilterDevicePnPEventNotify</i> is similar to a miniport driver's 
    <a href="https://msdn.microsoft.com/e41240c0-17be-42ef-a72c-c5311115cf64">
    MiniportDevicePnPEventNotify</a> function. Filter drivers can forward these notifications to underlying
    drivers. To forward a request, call the 
    <a href="https://msdn.microsoft.com/ae5dd48b-7777-4232-89ad-ac4464e03e57">
    NdisFDevicePnPEventNotify</a> function.</p>

<p>NDIS calls 
    <i>FilterDevicePnPEventNotify</i> at IRQL = PASSIVE_LEVEL.</p>

<p>To define a <i>FilterDevicePnPEventNotify</i> function, you must first provide a function declaration that identifies the type of function you're defining. Windows provides a set of function types for drivers. Declaring a function using the function types helps <a href="NULL">Code Analysis for Drivers</a>, <a href="NULL">Static Driver Verifier</a> (SDV), and other verification tools find errors, and it's a requirement for writing drivers for the Windows operating system.</p>

<p>For example, to define a <i>FilterDevicePnPEventNotify</i> function that is named "MyDevicePnPEventNotify", use the <b>FILTER_DEVICE_PNP_EVENT_NOTIFY</b> type as shown in this code example:</p>

<p>Then, implement your function as follows:</p>

<p>The <b>FILTER_DEVICE_PNP_EVENT_NOTIFY</b> function type is defined in the Ndis.h header file. To more accurately identify errors when you run the code analysis tools, be sure to add the _Use_decl_annotations_ annotation to your function definition.  The _Use_decl_annotations_ annotation ensures that the annotations that are applied to the <b>FILTER_DEVICE_PNP_EVENT_NOTIFY</b> function type in the header file are used.  For more information about the requirements for function declarations, see <a href="NULL">Declaring Functions by Using Function Role Types for NDIS Drivers</a>.

For information about  _Use_decl_annotations_, see <a href="http://go.microsoft.com/fwlink/p/?linkid=286697">Annotating Function Behavior</a>. </p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Supported in NDIS 6.0 and later.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ndis.h (include Ndis.h)</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff540442">FilterAttach</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/e41240c0-17be-42ef-a72c-c5311115cf64">
   MiniportDevicePnPEventNotify</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561804">NdisFDevicePnPEventNotify</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562608">NdisFRegisterFilterDriver</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564672">NdisWriteEventLogEntry</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff568730">NET_DEVICE_PNP_EVENT</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20FILTER_DEVICE_PNP_EVENT_NOTIFY callback function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>