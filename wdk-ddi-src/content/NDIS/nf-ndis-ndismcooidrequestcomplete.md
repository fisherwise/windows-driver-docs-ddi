---
UID: NF.ndis.NdisMCoOidRequestComplete
title: NdisMCoOidRequestComplete
author: windows-driver-content
description: The NdisMCoOidRequestComplete function returns the final status of an OID requestthat a miniport driver's MiniportCoOidRequest function returned NDIS_STATUS_PENDING for.
old-location: netvista\ndismcooidrequestcomplete.htm
ms.assetid: 18242351-3dec-40df-b112-2335253903d2
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
req.alt-api: NdisMCoOidRequestComplete
req.alt-loc: ndis.lib,ndis.dll
req.ddi-compliance: Irql_MCO_Function
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ndis.lib
req.dll: 
req.irql: <= DISPATCH_LEVEL
ms.keywords: NdisMCoOidRequestComplete
req.iface: 
---

# NdisMCoOidRequestComplete function



## -description
<p>The 
  <b>NdisMCoOidRequestComplete</b> function returns the final status of an OID requestthat a miniport driver's
  
  <a href="https://msdn.microsoft.com/903bcdc5-9d42-4067-a054-057edc95ccf7">MiniportCoOidRequest</a> function
  returned NDIS_STATUS_PENDING for.</p>


## -syntax

````
VOID NdisMCoOidRequestComplete(
  _In_ NDIS_HANDLE       MiniportAdapterHandle,
  _In_ NDIS_HANDLE       NdisVcHandle,
  _In_ PNDIS_OID_REQUEST OidRequest,
  _In_ NDIS_STATUS       Status
);
````


## -parameters
<dl>

### -param <i>MiniportAdapterHandle</i> [in]

<dd>
<p>A miniport adapter handle that NDIS passed to the 
     <i>MiniportAdapterHandle</i> parameter of the 
     <a href="https://msdn.microsoft.com/b146fa81-005b-4a6c-962d-4cb023ea790e">
     MiniportInitializeEx</a> function.</p>
</dd>

### -param <i>NdisVcHandle</i> [in]

<dd>
<p>A handle that identifies the virtual connection (VC). The miniport driver obtained this handle as
     an input parameter to its 
     <a href="https://msdn.microsoft.com/99eaba29-ce17-4e79-878e-5fdf7411e56c">MiniportCoCreateVc</a> function, either
     when a client set up an outgoing call or when the call manager created a VC for a client-registered
     service access point (SAP). The call manager created the VC to indicate an incoming-call notification.
     If the request is 
     <u>not</u> VC-specific, this parameter is <b>NULL</b>.</p>
</dd>

### -param <i>OidRequest</i> [in]

<dd>
<p>A pointer to a buffer that is formatted as an 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff566710">NDIS_OID_REQUEST</a> structure. The miniport
     driver obtained this pointer as an input parameter to its 
     <a href="https://msdn.microsoft.com/903bcdc5-9d42-4067-a054-057edc95ccf7">
     MiniportCoOidRequest</a> function.</p>
</dd>

### -param <i>Status</i> [in]

<dd>
<p>The final status of the request operation, either NDIS_STATUS_SUCCESS,
     NDIS_STATUS_REQUEST_ABORTED, or any driver-determined NDIS_STATUS_<i>XXX</i> value 
     <u>except</u> NDIS_STATUS_PENDING.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>A CoNDIS miniport driver that returns NDIS_STATUS_PENDING from its 
    <a href="https://msdn.microsoft.com/903bcdc5-9d42-4067-a054-057edc95ccf7">MiniportCoOidRequest</a> function must
    call 
    <b>NdisMCoOidRequestComplete</b> after the miniport driver has finished the request operation.</p>

<p>A call to 
    <b>NdisMCoOidRequestComplete</b> causes a call to the 
    <a href="https://msdn.microsoft.com/16883c64-3cc6-4f50-8be7-7c58c422a717">
    ProtocolCoOidRequestComplete</a> function of the overlying driver that called the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff561711">NdisCoOidRequest</a> function.</p>

<p>A CoNDIS miniport driver that returns NDIS_STATUS_PENDING from its 
    <a href="https://msdn.microsoft.com/903bcdc5-9d42-4067-a054-057edc95ccf7">MiniportCoOidRequest</a> function must
    call 
    <b>NdisMCoOidRequestComplete</b> after the miniport driver has finished the request operation.</p>

<p>A call to 
    <b>NdisMCoOidRequestComplete</b> causes a call to the 
    <a href="https://msdn.microsoft.com/16883c64-3cc6-4f50-8be7-7c58c422a717">
    ProtocolCoOidRequestComplete</a> function of the overlying driver that called the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff561711">NdisCoOidRequest</a> function.</p>

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
<p>&lt;= DISPATCH_LEVEL</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547971">Irql_MCO_Function</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/99eaba29-ce17-4e79-878e-5fdf7411e56c">MiniportCoCreateVc</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/903bcdc5-9d42-4067-a054-057edc95ccf7">MiniportCoOidRequest</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/b146fa81-005b-4a6c-962d-4cb023ea790e">MiniportInitializeEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff566710">NDIS_OID_REQUEST</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561711">NdisCoOidRequest</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/16883c64-3cc6-4f50-8be7-7c58c422a717">
   ProtocolCoOidRequestComplete</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NdisMCoOidRequestComplete function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>