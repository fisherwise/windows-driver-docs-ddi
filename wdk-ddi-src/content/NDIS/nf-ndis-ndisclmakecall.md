---
UID: NF.ndis.NdisClMakeCall
title: NdisClMakeCall
author: windows-driver-content
description: NdisClMakeCall sets up an outgoing call on a client-created VC.
old-location: netvista\ndisclmakecall.htm
ms.assetid: 69775220-71d8-497c-aaf7-9bc3ec90d00f
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: netvista
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Desktop
req.target-min-winverclnt: Supported for NDIS 6.0 and NDIS 5.1 drivers (see 
   NdisClMakeCall (NDIS 5.1)) in
   Windows Vista. Supported for NDIS 5.1 drivers (see 
   NdisClMakeCall (NDIS 5.1)) in
   Windows XP.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NdisClMakeCall
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
req.irql: <= DISPATCH_LEVEL
ms.keywords: NdisClMakeCall
req.iface: 
---

# NdisClMakeCall function



## -description
<p><b>NdisClMakeCall</b> sets up an outgoing call on a client-created VC.</p>


## -syntax

````
NDIS_STATUS NdisClMakeCall(
  _In_      NDIS_HANDLE         NdisVcHandle,
  _Inout_   PCO_CALL_PARAMETERS CallParameters,
  _In_opt_  NDIS_HANDLE         ProtocolPartyContext,
  _Out_opt_ PNDIS_HANDLE        NdisPartyHandle
);
````


## -parameters
<dl>

### -param <i>NdisVcHandle</i> [in]

<dd>
<p>Specifies the handle returned by a preceding call to 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff561696">NdisCoCreateVc</a>.</p>
</dd>

### -param <i>CallParameters</i> [in, out]

<dd>
<p>Pointer to a structure of type 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff545384">CO_CALL_PARAMETERS</a> in which the caller has
     specified the attributes for this connection, such as the address of the target for the call, latency,
     bandwidth, and quality of service if the network medium and address family supported by the call manager
     permits QoS specifications.</p>
</dd>

### -param <i>ProtocolPartyContext</i> [in, optional]

<dd>
<p>Optionally specifies a caller-supplied handle to a resident context area in which the client will
     maintain per-party state for the initial party on its multipoint VC. This parameter is <b>NULL</b> if the given
     VC does not represent a multipoint connection. For a multipoint VC, NDIS passes this handle back to the
     client's ProtocolCl<i>Xxx</i> functions in all subsequent calls that affect this particular party.</p>
</dd>

### -param <i>NdisPartyHandle</i> [out, optional]

<dd>
<p>Pointer to a caller-supplied variable, usually in the caller-allocated party context area, in
     which NDIS returns a handle representing the initial party to the multipoint connection if the request
     to set up an outgoing call is successful. If 
     <i>ProtocolPartyContext</i> is <b>NULL</b>, this variable, usually in the client's VC context area, also is set
     to <b>NULL</b> on completion of outgoing-call setup.</p>
</dd>
</dl>

## -returns
<p>When 
     <b>NdisClMakeCall</b> returns anything other than NDIS_STATUS_PENDING, the client should make an internal
     call to its 
     <a href="https://msdn.microsoft.com/6bb69f78-8dab-46a7-84fb-7bc17e894535">
     ProtocolClMakeCallComplete</a> function. Otherwise, NDIS calls the client's 
     <i>ProtocolClMakeCallComplete</i> function when this operation is completed.</p>

## -remarks
<p><b>NdisClMakeCall</b> sets up the attributes of a client-created VC for a client-initiated outgoing call.
    The client must set up the VC with 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff561696">NdisCoCreateVc</a> before it attempts to make
    an outgoing call.</p>

<p>A call to 
    <b>NdisClMakeCall</b> causes NDIS to forward this request to the 
    <a href="https://msdn.microsoft.com/ede0a18a-cd3b-4fbb-a16b-e7493940d633">ProtocolCmMakeCall</a> function of the
    call manager with which the client shares the given 
    <a href="https://msdn.microsoft.com/6bb69f78-8dab-46a7-84fb-7bc17e894535">NdisVcHandle</a>. The CM is
    responsible for validating the given data at 
    <i>CallParameters</i> . It can modify this client-supplied data while negotiating with relevant network
    components and can return different traffic parameters than the client originally gave to 
    <b>NdisClMakeCall</b>. The client's 
    <i>
    ProtocolClMakeCallComplete</i> function is responsible for accepting the modified call parameters if
    this occurs or for tearing down the call if the CM's proposed call parameters are unacceptable.</p>

<p>Consequently, the data at 
    <i>CallParameters</i> must remain available to the call manager at least for the duration of call setup.
    The client cannot free this buffer when 
    <b>NdisClMakeCall</b> returns NDIS_STATUS_PENDING. It must defer releasing this client-allocated resource
    until its 
    <i>ProtocolClMakeCallComplete</i> function is called.</p>

<p>If 
    <b>NdisClMakeCall</b> sets up a multipoint connection, the client is establishing the traffic parameters
    globally for the given VC, unless the underlying network medium supports per-party traffic
    parameters.</p>

<p>The client's 
    <i>ProtocolClMakeCallComplete</i> function should check the input 
    <i>Status</i> for NDIS_STATUS_SUCCESS before it uses any returned handle at 
    <i>NdisPartyHandle</i> . If the call manager fails the request to set up a call on a multipoint
    connection, the value of this client-supplied variable is invalid.</p>

<p><b>NdisClMakeCall</b> sets up the attributes of a client-created VC for a client-initiated outgoing call.
    The client must set up the VC with 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff561696">NdisCoCreateVc</a> before it attempts to make
    an outgoing call.</p>

<p>A call to 
    <b>NdisClMakeCall</b> causes NDIS to forward this request to the 
    <a href="https://msdn.microsoft.com/ede0a18a-cd3b-4fbb-a16b-e7493940d633">ProtocolCmMakeCall</a> function of the
    call manager with which the client shares the given 
    <a href="https://msdn.microsoft.com/6bb69f78-8dab-46a7-84fb-7bc17e894535">NdisVcHandle</a>. The CM is
    responsible for validating the given data at 
    <i>CallParameters</i> . It can modify this client-supplied data while negotiating with relevant network
    components and can return different traffic parameters than the client originally gave to 
    <b>NdisClMakeCall</b>. The client's 
    <i>
    ProtocolClMakeCallComplete</i> function is responsible for accepting the modified call parameters if
    this occurs or for tearing down the call if the CM's proposed call parameters are unacceptable.</p>

<p>Consequently, the data at 
    <i>CallParameters</i> must remain available to the call manager at least for the duration of call setup.
    The client cannot free this buffer when 
    <b>NdisClMakeCall</b> returns NDIS_STATUS_PENDING. It must defer releasing this client-allocated resource
    until its 
    <i>ProtocolClMakeCallComplete</i> function is called.</p>

<p>If 
    <b>NdisClMakeCall</b> sets up a multipoint connection, the client is establishing the traffic parameters
    globally for the given VC, unless the underlying network medium supports per-party traffic
    parameters.</p>

<p>The client's 
    <i>ProtocolClMakeCallComplete</i> function should check the input 
    <i>Status</i> for NDIS_STATUS_SUCCESS before it uses any returned handle at 
    <i>NdisPartyHandle</i> . If the call manager fails the request to set up a call on a multipoint
    connection, the value of this client-supplied variable is invalid.</p>

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
<p>Supported for NDIS 6.0 and NDIS 5.1 drivers (see 
   <a href="https://msdn.microsoft.com/library/windows/hardware/ff550884">NdisClMakeCall (NDIS 5.1)</a>) in
   Windows Vista. Supported for NDIS 5.1 drivers (see 
   <b>NdisClMakeCall (NDIS 5.1)</b>) in
   Windows XP.</p>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547996">Irql_Protocol_Driver_Function</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545384">CO_CALL_PARAMETERS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/df690a05-359d-44f0-b063-4fc21d6c4d76">
   NdisAllocateFromNPagedLookasideList</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561625">NdisClAddParty</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561627">NdisClCloseCall</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561636">NdisClModifyCallQoS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561649">NdisCmActivateVc</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561677">NdisCmMakeCallComplete</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561696">NdisCoCreateVc</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/6bb69f78-8dab-46a7-84fb-7bc17e894535">ProtocolClMakeCallComplete</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/ede0a18a-cd3b-4fbb-a16b-e7493940d633">ProtocolCmMakeCall</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NdisClMakeCall function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>