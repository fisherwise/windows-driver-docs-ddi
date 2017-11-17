---
UID: NF.ndis.NdisMCmRegisterAddressFamilyEx
title: NdisMCmRegisterAddressFamilyEx
author: windows-driver-content
description: The NdisMCmRegisterAddressFamilyEx function registers an address family (AF) for communication between a miniport call manager (MCM) and CoNDIS clients.
old-location: netvista\ndismcmregisteraddressfamilyex.htm
ms.assetid: f58a9c08-d2cf-48d1-98d1-68aecd3b7bd0
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
req.alt-api: NdisMCmRegisterAddressFamilyEx
req.alt-loc: ndis.lib,ndis.dll
req.ddi-compliance: Irql_MCM_Function
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ndis.lib
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: NdisMCmRegisterAddressFamilyEx
req.iface: 
---

# NdisMCmRegisterAddressFamilyEx function



## -description
<p>The
  <b>NdisMCmRegisterAddressFamilyEx</b> function registers an address family (AF) for communication between a
  miniport call manager (MCM) and CoNDIS clients.</p>


## -syntax

````
NDIS_STATUS NdisMCmRegisterAddressFamilyEx(
  _In_ NDIS_HANDLE        MiniportAdapterHandle,
  _In_ PCO_ADDRESS_FAMILY AddressFamily
);
````


## -parameters
<dl>

### -param <i>MiniportAdapterHandle</i> [in]

<dd>
<p>An NDIS-supplied handle that identifies a miniport adapter. This handle is an input parameter to
     the MCM's 
     <a href="https://msdn.microsoft.com/b146fa81-005b-4a6c-962d-4cb023ea790e">
     MiniportInitializeEx</a> function.</p>
</dd>

### -param <i>AddressFamily</i> [in]

<dd>
<p>A pointer to a 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff545368">CO_ADDRESS_FAMILY</a> structure that identifies
     the AF that the MCM driver supports. 
     </p>
<p>The pointer becomes an input parameter to the 
     <a href="https://msdn.microsoft.com/272d99da-ef08-4ebd-90e7-74e99410b3f5">
     ProtocolCoAfRegisterNotify</a> functions of all of the CoNDIS clients that are bound to this MCM
     driver.</p>
</dd>
</dl>

## -returns
<p><b>NdisMCmRegisterAddressFamilyEx</b> can return any of the following:</p><dl>
<dt><b>NDIS_STATUS_SUCCESS</b></dt>
</dl><p>The miniport driver registered with NDIS as a call manager for the AF that the 
       <i>AddressFamily</i> parameter specified, so NDIS will call the 
       <a href="https://msdn.microsoft.com/272d99da-ef08-4ebd-90e7-74e99410b3f5">
       ProtocolCoAfRegisterNotify</a> functions of all of the clients that bind to the MCM driver.</p><dl>
<dt><b>NDIS_STATUS_RESOURCES</b></dt>
</dl><p>The requested operation failed because NDIS could not allocate sufficient memory or initialize
       the state information that it uses to track the MCM driver as a call manager of the specified
       AF.</p><dl>
<dt><b>NDIS_STATUS_FAILURE</b></dt>
</dl><p>NDIS failed the call to 
       <b>NdisMCmRegisterAddressFamilyEx</b>, possibly for one of the following reasons:
       </p>

<p>The caller was not registered as a connection-oriented miniport driver.</p>

<p>The caller tried to register a duplicate AF for a given miniport adapter.</p>

<p> </p>

## -remarks
<p>NDIS MCMs, which register as NDIS miniport drivers by calling the 
    <a href="https://msdn.microsoft.com/bed68aa8-499d-41fd-997b-a46316913cc8">
    NdisMRegisterMiniportDriver</a> function, should call the 
    <b>NdisMCmRegisterAddressFamilyEx</b> function to register an AF. Stand-alone call managers should instead
    call the 
    <a href="https://msdn.microsoft.com/8890bf31-f2c7-48b0-926d-8931893ede86">
    NdisCmRegisterAddressFamilyEx</a> function.</p>

<p>To register an AF for a miniport adapter, the MCM should call 
    <b>NdisMCmRegisterAddressFamilyEx</b> from the 
    <a href="https://msdn.microsoft.com/b146fa81-005b-4a6c-962d-4cb023ea790e">MiniportInitializeEx</a> function.</p>

<p>The driver of any network interface card (NIC) that has on-board connection-oriented signaling support
    can register itself as an MCM driver for better performance in managing calls. If a driver registers as
    an MCM driver, any stand-alone call manager with the NIC driver's own call-management support is
    displaced.</p>

<p>An MCM driver calls 
    <b>NdisMCmRegisterAddressFamilyEx</b> after it has determined that a NIC is fully operational and the
    driver can complete network I/O operations. That is, such an MCM registers itself as a call manager and
    advertises its specific signaling services for CoNDIS clients.</p>

<p>After 
    <i>MiniportInitializeEx</i> returns control with a successful registration as a call manager, NDIS calls
    the 
    <a href="https://msdn.microsoft.com/1958722e-012e-4110-a82c-751744bcf9b5">ProtocolBindAdapterEx</a> functions
    of potential clients and, then, the 
    <a href="https://msdn.microsoft.com/272d99da-ef08-4ebd-90e7-74e99410b3f5">
    ProtocolCoAfRegisterNotify</a> functions of all of the clients that bind themselves to the associated
    MCM miniport adapter. These clients then cause NDIS to call the 
    <a href="https://msdn.microsoft.com/7422c205-bc41-4121-b430-ff9e6b49dc2e">ProtocolCmOpenAf</a> function of the
    MCM.</p>

<p>An MCM can support more than one AF for a single NIC that it manages. The MCM driver must call 
    <b>NdisMCmRegisterAddressFamilyEx</b> once for each AF that it registers for a miniport adapter. Only one
    MCM driver can support a particular type of AF for clients that are bound to a given miniport
    adapter.</p>

<p>NDIS MCMs, which register as NDIS miniport drivers by calling the 
    <a href="https://msdn.microsoft.com/bed68aa8-499d-41fd-997b-a46316913cc8">
    NdisMRegisterMiniportDriver</a> function, should call the 
    <b>NdisMCmRegisterAddressFamilyEx</b> function to register an AF. Stand-alone call managers should instead
    call the 
    <a href="https://msdn.microsoft.com/8890bf31-f2c7-48b0-926d-8931893ede86">
    NdisCmRegisterAddressFamilyEx</a> function.</p>

<p>To register an AF for a miniport adapter, the MCM should call 
    <b>NdisMCmRegisterAddressFamilyEx</b> from the 
    <a href="https://msdn.microsoft.com/b146fa81-005b-4a6c-962d-4cb023ea790e">MiniportInitializeEx</a> function.</p>

<p>The driver of any network interface card (NIC) that has on-board connection-oriented signaling support
    can register itself as an MCM driver for better performance in managing calls. If a driver registers as
    an MCM driver, any stand-alone call manager with the NIC driver's own call-management support is
    displaced.</p>

<p>An MCM driver calls 
    <b>NdisMCmRegisterAddressFamilyEx</b> after it has determined that a NIC is fully operational and the
    driver can complete network I/O operations. That is, such an MCM registers itself as a call manager and
    advertises its specific signaling services for CoNDIS clients.</p>

<p>After 
    <i>MiniportInitializeEx</i> returns control with a successful registration as a call manager, NDIS calls
    the 
    <a href="https://msdn.microsoft.com/1958722e-012e-4110-a82c-751744bcf9b5">ProtocolBindAdapterEx</a> functions
    of potential clients and, then, the 
    <a href="https://msdn.microsoft.com/272d99da-ef08-4ebd-90e7-74e99410b3f5">
    ProtocolCoAfRegisterNotify</a> functions of all of the clients that bind themselves to the associated
    MCM miniport adapter. These clients then cause NDIS to call the 
    <a href="https://msdn.microsoft.com/7422c205-bc41-4121-b430-ff9e6b49dc2e">ProtocolCmOpenAf</a> function of the
    MCM.</p>

<p>An MCM can support more than one AF for a single NIC that it manages. The MCM driver must call 
    <b>NdisMCmRegisterAddressFamilyEx</b> once for each AF that it registers for a miniport adapter. Only one
    MCM driver can support a particular type of AF for clients that are bound to a given miniport
    adapter.</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547967">Irql_MCM_Function</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545368">CO_ADDRESS_FAMILY</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/b146fa81-005b-4a6c-962d-4cb023ea790e">MiniportInitializeEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/8890bf31-f2c7-48b0-926d-8931893ede86">
   NdisCmRegisterAddressFamilyEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563654">NdisMRegisterMiniportDriver</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/1958722e-012e-4110-a82c-751744bcf9b5">ProtocolBindAdapterEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/7422c205-bc41-4121-b430-ff9e6b49dc2e">ProtocolCmOpenAf</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/272d99da-ef08-4ebd-90e7-74e99410b3f5">ProtocolCoAfRegisterNotify</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/b086dd24-74f5-474a-8684-09bf92ac731b">ProtocolCoCreateVc</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/d761270f-bf77-441e-834c-9ac7fb3d350f">ProtocolCoDeleteVc</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/8247396f-8781-45da-aba1-a31a2a26a46f">ProtocolCoOidRequest</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/16883c64-3cc6-4f50-8be7-7c58c422a717">
   ProtocolCoOidRequestComplete</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NdisMCmRegisterAddressFamilyEx function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>