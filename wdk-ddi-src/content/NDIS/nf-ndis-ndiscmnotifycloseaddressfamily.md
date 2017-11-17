---
UID: NF.ndis.NdisCmNotifyCloseAddressFamily
title: NdisCmNotifyCloseAddressFamily
author: windows-driver-content
description: The NdisCmNotifyCloseAddressFamily function notifies NDIS that a call manager is unbinding from an underlying miniport adapter and that any associated CoNDIS clients should close the specified address family (AF).
old-location: netvista\ndiscmnotifycloseaddressfamily.htm
ms.assetid: 1967f663-86ce-4e9d-9498-61951bdf4db0
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: netvista
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Desktop
req.target-min-winverclnt: Supported in NDIS 6.0 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NdisCmNotifyCloseAddressFamily
req.alt-loc: ndis.lib,ndis.dll
req.ddi-compliance: Irql_CallManager_Function
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ndis.lib
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: NdisCmNotifyCloseAddressFamily
req.iface: 
---

# NdisCmNotifyCloseAddressFamily function



## -description
<p>The 
  <b>NdisCmNotifyCloseAddressFamily</b> function notifies NDIS that a call manager is unbinding from an
  underlying miniport adapter and that any associated CoNDIS clients should close the specified address
  family (AF).</p>


## -syntax

````
NDIS_STATUS NdisCmNotifyCloseAddressFamily(
  _In_ NDIS_HANDLE NdisAfHandle
);
````


## -parameters
<dl>

### -param <i>NdisAfHandle</i> [in]

<dd>
<p>An NDIS handle that identifies the AF that NDIS should close. NDIS supplied this handle to the
     call manager's 
     <a href="https://msdn.microsoft.com/7422c205-bc41-4121-b430-ff9e6b49dc2e">ProtocolCmOpenAf</a> function.</p>
</dd>
</dl>

## -returns
<p><b>NdisCmNotifyCloseAddressFamily</b> can return one of the following:</p><dl>
<dt><b>NDIS_STATUS_SUCCESS</b></dt>
</dl><p>NDIS successfully closed the address family.</p><dl>
<dt><b>NDIS_STATUS_PENDING</b></dt>
</dl><p>NDIS is handling this request asynchronously, and it will call the call manager's 
       <a href="https://msdn.microsoft.com/c5bdedee-dacd-4f4d-a3d1-f1cb71a68001">
       ProtocolCmNotifyCloseAfComplete</a> function when the close operation is complete.</p><dl>
<dt><b>NDIS_STATUS_<i>XXX</i></b></dt>
</dl><p>NDIS failed the request for some NDIS or client driver-determined reason.</p>

<p> </p>

## -remarks
<p>Stand-alone CoNDIS call managers, which register as NDIS protocol drivers by calling the 
    <a href="https://msdn.microsoft.com/b48571eb-13a2-4541-80ac-c8d31f378d37">
    NdisRegisterProtocolDriver</a> function, can call the 
    <b>NdisCmNotifyCloseAddressFamily</b> function. Miniport call managers (MCMs) instead call the 
    <a href="https://msdn.microsoft.com/47b0b1da-e29b-45cc-921b-69d630670b44">
    NdisMCmNotifyCloseAddressFamily</a> function.</p>

<p>To close an AF for a binding, the stand-alone call manager should call 
    <b>NdisCmNotifyCloseAddressFamily</b> from the 
    <a href="https://msdn.microsoft.com/19fa7be2-acb9-42f6-bd9f-5be3e3c8b5fa">
    ProtocolUnbindAdapterEx</a> function. NDIS then calls the 
    <a href="https://msdn.microsoft.com/0f595daa-9822-4ca6-8f25-e6f82030d4ea">
    ProtocolClNotifyCloseAf</a> function of the client that has the specified AF open.</p>

<p>If 
    <b>NdisCmNotifyCloseAddressFamily</b> returns NDIS_STATUS_PENDING, NDIS calls the call manager's 
    <a href="https://msdn.microsoft.com/c5bdedee-dacd-4f4d-a3d1-f1cb71a68001">
    ProtocolCmNotifyCloseAfComplete</a> function after the client completes the AF close operation.</p>

<p>Stand-alone CoNDIS call managers, which register as NDIS protocol drivers by calling the 
    <a href="https://msdn.microsoft.com/b48571eb-13a2-4541-80ac-c8d31f378d37">
    NdisRegisterProtocolDriver</a> function, can call the 
    <b>NdisCmNotifyCloseAddressFamily</b> function. Miniport call managers (MCMs) instead call the 
    <a href="https://msdn.microsoft.com/47b0b1da-e29b-45cc-921b-69d630670b44">
    NdisMCmNotifyCloseAddressFamily</a> function.</p>

<p>To close an AF for a binding, the stand-alone call manager should call 
    <b>NdisCmNotifyCloseAddressFamily</b> from the 
    <a href="https://msdn.microsoft.com/19fa7be2-acb9-42f6-bd9f-5be3e3c8b5fa">
    ProtocolUnbindAdapterEx</a> function. NDIS then calls the 
    <a href="https://msdn.microsoft.com/0f595daa-9822-4ca6-8f25-e6f82030d4ea">
    ProtocolClNotifyCloseAf</a> function of the client that has the specified AF open.</p>

<p>If 
    <b>NdisCmNotifyCloseAddressFamily</b> returns NDIS_STATUS_PENDING, NDIS calls the call manager's 
    <a href="https://msdn.microsoft.com/c5bdedee-dacd-4f4d-a3d1-f1cb71a68001">
    ProtocolCmNotifyCloseAfComplete</a> function after the client completes the AF close operation.</p>

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
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Ndis.lib</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547917">Irql_CallManager_Function</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/47b0b1da-e29b-45cc-921b-69d630670b44">
   NdisMCmNotifyCloseAddressFamily</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564520">NdisRegisterProtocolDriver</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/0f595daa-9822-4ca6-8f25-e6f82030d4ea">ProtocolClNotifyCloseAf</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/c5bdedee-dacd-4f4d-a3d1-f1cb71a68001">
   ProtocolCmNotifyCloseAfComplete</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/7422c205-bc41-4121-b430-ff9e6b49dc2e">ProtocolCmOpenAf</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/19fa7be2-acb9-42f6-bd9f-5be3e3c8b5fa">ProtocolUnbindAdapterEx</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NdisCmNotifyCloseAddressFamily function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>