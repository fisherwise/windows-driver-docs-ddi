---
UID: NF.ndis.NdisCoDeleteVc
title: NdisCoDeleteVc
author: windows-driver-content
description: NdisCoDeleteVc destroys a caller-created VC.
old-location: netvista\ndiscodeletevc.htm
ms.assetid: 31e88a5b-d97c-482a-aab0-dd987b15d657
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: netvista
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Desktop
req.target-min-winverclnt: Supported for NDIS 6.0 and NDIS 5.1 drivers (see 
   NdisCoDeleteVc (NDIS 5.1)) in
   Windows Vista. Supported for NDIS 5.1 drivers (see 
   NdisCoDeleteVc (NDIS 5.1)) in
   Windows XP.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NdisCoDeleteVc
req.alt-loc: ndis.lib,ndis.dll
req.ddi-compliance: Irql_Connection_Function
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ndis.lib
req.dll: 
req.irql: <= DISPATCH_LEVEL
ms.keywords: NdisCoDeleteVc
req.iface: 
---

# NdisCoDeleteVc function



## -description
<p><b>NdisCoDeleteVc</b> destroys a caller-created VC.</p>


## -syntax

````
NDIS_STATUS NdisCoDeleteVc(
  _In_ NDIS_HANDLE NdisVcHandle
);
````


## -parameters
<dl>

### -param <i>NdisVcHandle</i> [in]

<dd>
<p>Specifies the handle identifying the VC to be deleted. The caller originally obtained this handle
     from 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff561696">NdisCoCreateVc</a>.</p>
</dd>
</dl>

## -returns
<p><b>NdisCoDeleteVc</b> can return one of the following:</p><dl>
<dt><b>NDIS_STATUS_SUCCESS</b></dt>
</dl><p>NDIS deleted the VC.</p><dl>
<dt><b>NDIS_STATUS_NOT_ACCEPTED</b></dt>
</dl><p>The VC is still active, so it could not be deleted.</p><dl>
<dt><b>NDIS_STATUS_CLOSING</b></dt>
</dl><p>This call is redundant, but deactivation on the given VC is still pending.</p>

<p> </p>

## -remarks
<p>When a protocol calls 
    <b>NdisCoDeleteVc</b>, there must be no outstanding calls on the given VC and that VC already has been
    deactivated. To meet these requirements implies that the following conditions hold:</p>

<p>If the call tear-down was initiated by a local client, that client has already called 
      <a href="https://msdn.microsoft.com/library/windows/hardware/ff561627">NdisClCloseCall</a> with the given 
      <i>NdisVcHandle</i> and its close-call request has completed successfully.</p>

<p>If the call tear-down was initiated by a remote client, the stand-alone call manager has already
      called 
      <a href="https://msdn.microsoft.com/library/windows/hardware/ff561657">NdisCmDeactivateVc</a> with the given 
      <i>NdisVcHandle</i> and its deactivation request has completed successfully.</p>

<p>Only the protocol that created a particular VC can delete that VC. A call to 
    <b>NdisCoDeleteVc</b> causes NDIS to call both the underlying miniport driver's 
    <a href="https://msdn.microsoft.com/ed9b6ad1-059b-47d9-b1f7-10d498c5d2d4">MiniportCoDeleteVc</a> function and the 
    <a href="https://msdn.microsoft.com/d761270f-bf77-441e-834c-9ac7fb3d350f">ProtocolCoDeleteVc</a> function of the
    client or call manager with which the caller shares the 
    <i>NdisVcHandle</i> .</p>

<p>When 
    <b>NdisCoDeleteVc</b> returns control, the 
    <i>NdisVcHandle</i> is no longer valid.</p>

<p>Stand-alone call managers, which register themselves with NDIS as protocol drivers, can call 
    <b>NdisCoDeleteVc</b>. Connection-oriented miniport drivers that provide integrated call-management
    support call 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff562819">NdisMCmDeleteVc</a> instead.</p>

<p>When a protocol calls 
    <b>NdisCoDeleteVc</b>, there must be no outstanding calls on the given VC and that VC already has been
    deactivated. To meet these requirements implies that the following conditions hold:</p>

<p>If the call tear-down was initiated by a local client, that client has already called 
      <a href="https://msdn.microsoft.com/library/windows/hardware/ff561627">NdisClCloseCall</a> with the given 
      <i>NdisVcHandle</i> and its close-call request has completed successfully.</p>

<p>If the call tear-down was initiated by a remote client, the stand-alone call manager has already
      called 
      <a href="https://msdn.microsoft.com/library/windows/hardware/ff561657">NdisCmDeactivateVc</a> with the given 
      <i>NdisVcHandle</i> and its deactivation request has completed successfully.</p>

<p>Only the protocol that created a particular VC can delete that VC. A call to 
    <b>NdisCoDeleteVc</b> causes NDIS to call both the underlying miniport driver's 
    <a href="https://msdn.microsoft.com/ed9b6ad1-059b-47d9-b1f7-10d498c5d2d4">MiniportCoDeleteVc</a> function and the 
    <a href="https://msdn.microsoft.com/d761270f-bf77-441e-834c-9ac7fb3d350f">ProtocolCoDeleteVc</a> function of the
    client or call manager with which the caller shares the 
    <i>NdisVcHandle</i> .</p>

<p>When 
    <b>NdisCoDeleteVc</b> returns control, the 
    <i>NdisVcHandle</i> is no longer valid.</p>

<p>Stand-alone call managers, which register themselves with NDIS as protocol drivers, can call 
    <b>NdisCoDeleteVc</b>. Connection-oriented miniport drivers that provide integrated call-management
    support call 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff562819">NdisMCmDeleteVc</a> instead.</p>

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
   <a href="https://msdn.microsoft.com/library/windows/hardware/ff551027">NdisCoDeleteVc (NDIS 5.1)</a>) in
   Windows Vista. Supported for NDIS 5.1 drivers (see 
   <b>NdisCoDeleteVc (NDIS 5.1)</b>) in
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547924">Irql_Connection_Function</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/ed9b6ad1-059b-47d9-b1f7-10d498c5d2d4">MiniportCoDeleteVc</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561627">NdisClCloseCall</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561657">NdisCmDeactivateVc</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561696">NdisCoCreateVc</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562819">NdisMCmDeleteVc</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/a7ba1ab2-04c9-45b5-a184-e1ad1448561a">ProtocolClCloseCallComplete</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/01c7d887-eb54-47c3-98f0-bc567b60fb4b">ProtocolClIncomingCloseCall</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/b5307e1b-3905-4e43-a0b0-0068ba18ef0d">ProtocolCmCloseCall</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/d761270f-bf77-441e-834c-9ac7fb3d350f">ProtocolCoDeleteVc</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NdisCoDeleteVc function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>