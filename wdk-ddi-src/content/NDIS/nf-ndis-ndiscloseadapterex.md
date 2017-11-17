---
UID: NF.ndis.NdisCloseAdapterEx
title: NdisCloseAdapterEx
author: windows-driver-content
description: A protocol driver calls the NdisCloseAdapterEx function to release the binding and the resources that were allocated when the driver called the NdisOpenAdapterEx function.
old-location: netvista\ndiscloseadapterex.htm
ms.assetid: 8e3c6373-e39d-4f9b-b874-e3a9c93791b9
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
req.alt-api: NdisCloseAdapterEx
req.alt-loc: ndis.lib,ndis.dll
req.ddi-compliance: Irql_Protocol_Driver_Function
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ndis.lib
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: NdisCloseAdapterEx
req.iface: 
---

# NdisCloseAdapterEx function



## -description
<p>A protocol driver calls the 
  <b>NdisCloseAdapterEx</b> function to release the binding and the resources that were allocated when the
  driver called the 
  <a href="https://msdn.microsoft.com/library/windows/hardware/ff563715">NdisOpenAdapterEx</a> function.</p>


## -syntax

````
NDIS_STATUS NdisCloseAdapterEx(
  _In_ NDIS_HANDLE NdisBindingHandle
);
````


## -parameters
<dl>

### -param <i>NdisBindingHandle</i> [in]

<dd>
<p>The handle that NDIS provided at the 
     <i>NdisBindingHandle</i> parameter of 
     <b>NdisOpenAdapterEx</b>. This handle identifies the binding that NDIS should close.</p>
</dd>
</dl>

## -returns
<p><b>NdisCloseAdapterEx</b> returns one of the following status values:</p><dl>
<dt><b>NDIS_STATUS_SUCCESS</b></dt>
</dl><p><b>NdisCloseAdapterEx</b> successfully closed the binding to the underlying miniport adapter.</p><dl>
<dt><b>NDIS_STATUS_PENDING</b></dt>
</dl><p><b>NdisCloseAdapterEx</b> did not complete the close operation and the operation will be completed
       asynchronously. NDIS calls the protocol driver's 
       <a href="https://msdn.microsoft.com/62cc047a-bc91-4e1e-817e-7fd509d4d90e">
       ProtocolCloseAdapterCompleteEx</a> function when the operation is complete.</p>

<p> </p>

## -remarks
<p>A protocol driver typically calls 
    <b>NdisCloseAdapterEx</b> from its 
    <a href="https://msdn.microsoft.com/19fa7be2-acb9-42f6-bd9f-5be3e3c8b5fa">
    ProtocolUnbindAdapterEx</a> function. The driver can also call 
    <b>NdisCloseAdapterEx</b> from its 
    <a href="https://msdn.microsoft.com/1958722e-012e-4110-a82c-751744bcf9b5">ProtocolBindAdapterEx</a> function.
    For example, if the driver failed to set an OID value after it called 
    <b>NdisOpenAdapterEx</b>, it can call 
    <b>NdisCloseAdapterEx</b> from its 
    <i>ProtocolBindAdapterEx</i> function.</p>

<p>If a protocol driver must close a miniport adapter outside the context of 
    <i>ProtocolUnbindAdapterEx</i> or 
    <i>ProtocolBindAdapterEx</i>, it must call the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff564630">NdisUnbindAdapter</a> function.</p>

<p>Protocol drivers should wait for all send requests and OID requests that they originated to complete
    before calling 
    <b>NdisCloseAdapterEx</b>.</p>

<p>As soon as the driver calls 
    <b>NdisCloseAdapterEx</b>, the handle obtained from the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff563715">NdisOpenAdapterEx</a> function at the 
    <i>NdisBindingHandle</i> parameter becomes invalid.</p>

<p>A protocol driver typically calls 
    <b>NdisCloseAdapterEx</b> from its 
    <a href="https://msdn.microsoft.com/19fa7be2-acb9-42f6-bd9f-5be3e3c8b5fa">
    ProtocolUnbindAdapterEx</a> function. The driver can also call 
    <b>NdisCloseAdapterEx</b> from its 
    <a href="https://msdn.microsoft.com/1958722e-012e-4110-a82c-751744bcf9b5">ProtocolBindAdapterEx</a> function.
    For example, if the driver failed to set an OID value after it called 
    <b>NdisOpenAdapterEx</b>, it can call 
    <b>NdisCloseAdapterEx</b> from its 
    <i>ProtocolBindAdapterEx</i> function.</p>

<p>If a protocol driver must close a miniport adapter outside the context of 
    <i>ProtocolUnbindAdapterEx</i> or 
    <i>ProtocolBindAdapterEx</i>, it must call the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff564630">NdisUnbindAdapter</a> function.</p>

<p>Protocol drivers should wait for all send requests and OID requests that they originated to complete
    before calling 
    <b>NdisCloseAdapterEx</b>.</p>

<p>As soon as the driver calls 
    <b>NdisCloseAdapterEx</b>, the handle obtained from the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff563715">NdisOpenAdapterEx</a> function at the 
    <i>NdisBindingHandle</i> parameter becomes invalid.</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547996">Irql_Protocol_Driver_Function</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563715">NdisOpenAdapterEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564630">NdisUnbindAdapter</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/1958722e-012e-4110-a82c-751744bcf9b5">ProtocolBindAdapterEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/62cc047a-bc91-4e1e-817e-7fd509d4d90e">
   ProtocolCloseAdapterCompleteEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/19fa7be2-acb9-42f6-bd9f-5be3e3c8b5fa">ProtocolUnbindAdapterEx</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NdisCloseAdapterEx function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>