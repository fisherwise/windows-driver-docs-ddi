---
UID: NF.fwpsk.FwpsInjectMacReceiveAsync0
title: FwpsInjectMacReceiveAsync0
author: windows-driver-content
description: The FwpsInjectMacReceiveAsync0 function can reinject a previously absorbed media access control (MAC) frame (or a clone of the frame) back to the layer 2 inbound data path it was intercepted from, or inject an invented MAC frame.
old-location: netvista\fwpsinjectmacreceiveasync0.htm
ms.assetid: 8B03835A-98EE-4157-BD05-C52D01EE5F5E
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: netvista
req.header: fwpsk.h
req.include-header: Fwpsk.h
req.target-type: Universal
req.target-min-winverclnt: Available starting with Windows 8.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FwpsInjectMacSendAsync0
req.alt-loc: fwpkclnt.lib,fwpkclnt.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Fwpkclnt.lib
req.dll: 
req.irql: <= DISPATCH_LEVEL
ms.keywords: FwpsInjectMacReceiveAsync0
req.iface: 
---

# FwpsInjectMacReceiveAsync0 function



## -description
<p>The <b>FwpsInjectMacReceiveAsync0</b> function can  reinject a previously absorbed media access control (MAC) frame (or a clone of the frame) back to the layer 2 inbound data path it was intercepted from, or inject an invented MAC frame.<div class="alert"><b>Note</b>  <b>FwpsInjectMacReceiveAsync0</b> is a specific version of <b>FwpsInjectMacReceiveAsync</b>. See <a href="fwp.wfp_version-independent_names_and_targeting_specific_versions_of_windows">WFP Version-Independent Names and Targeting Specific Versions of Windows</a> for more information.</div>
<div> </div>
</p>


## -syntax

````
NTSTATUS NTAPI FwpsInjectMacSendAsync0(
  _In_     HANDLE               injectionHandle,
  _In_opt_ HANDLE               injectionContext,
  _In_     UINT32               flags,
  _In_     UINT16               layerId,
  _In_     IF_INDEX             interfaceIndex,
  _In_     NDIS_PORT_NUMBER     NdisPortNumber,
  _Inout_  NET_BUFFER_LIST      *netBufferLists,
  _In_     FWPS_INJECT_COMPLETE completionFn,
  _In_opt_ HANDLE               completionContext
);
````


## -parameters
<dl>

### -param <i>injectionHandle</i> [in]

<dd>
<p>An injection handle that was previously obtained by a call to  the <a href="https://msdn.microsoft.com/library/windows/hardware/ff551180">FwpsInjectionHandleCreate0</a> function with the <i>flags</i> parameter set to FWPS_INJECTION_TYPE_L2. </p>
<div class="alert"><b>Note</b>  Set the <i>addressFamily</i> parameter of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff551180">FwpsInjectionHandleCreate0</a> function to AF_UNSPEC.</div>
<div> </div>
</dd>

### -param <i>injectionContext</i> [in, optional]

<dd>
<p>An optional handle to the injection context. If specified, it can be obtained by calling the 
     <a href="https://msdn.microsoft.com/785d99a5-a8c9-4763-bdd4-e26f604f6be7">
     FwpsQueryPacketInjectionState0</a> function when the packet injection state 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff552408">FWPS_PACKET_INJECTION_STATE</a> is
     <b>FWPS_PACKET_INJECTED_BY_SELF</b> or <b>FWPS_PACKET_PREVIOUSLY_INJECTED_BY_SELF</b>.</p>
</dd>

### -param <i>flags</i> [in]

<dd>
<p>Reserved. Must be set to zero.</p>
</dd>

### -param <i>layerId</i> [in]

<dd>
<p>The run-time identifier for the filtering layer at which the data stream is being processed. </p>
</dd>

### -param <i>interfaceIndex</i> [in]

<dd>
<p>The interface index that is passed to the callout driver's <a href="https://msdn.microsoft.com/library/windows/hardware/ff544887">classifyFn</a> incoming value FWPS_FIELD_<i>Xxx</i>_MAC_FRAME_<i>Xxx</i>_INTERFACE_INDEX.</p>
</dd>

### -param <i>NdisPortNumber</i> [in]

<dd>
<p>The NDIS port number  that is passed to the callout driver's <a href="https://msdn.microsoft.com/library/windows/hardware/ff544887">classifyFn</a> incoming value FWPS_FIELD_<i>Xxx</i>_MAC_FRAME_<i>Xxx</i>_NDIS_PORT.</p>
</dd>

### -param <i>netBufferLists</i> [in, out]

<dd>
<p>A pointer to a 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> structure that describes
     the packet data that is being injected. A callout driver allocates a NET_BUFFER_LIST structure to use to
     inject packet data by calling either the 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff551134">FwpsAllocateCloneNetBufferList0</a> function or the 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff551135">FwpsAllocateNetBufferAndNetBufferList0</a> function. The NET_BUFFER_LIST structure must begin with an
     IP header.</p>
</dd>

### -param <i>completionFn</i> [in]

<dd>
<p>A pointer to a 
     <a href="https://msdn.microsoft.com/c03656ec-f0fe-49f5-8a04-2d26ef23c50a">completionFn</a> callout function provided by
     the callout driver. The filter engine calls this function after the packet data, described by the 
     <i>netBufferLists</i> parameter, has been injected into the network stack. This pointer must be specified when injecting cloned or created NET_BUFFER_LIST structures. When injecting original  NET_BUFFER_LIST structures, this parameter can be NULL if the original structures  are not altered.</p>
</dd>

### -param <i>completionContext</i> [in, optional]

<dd>
<p>A pointer to a callout driver–provided context that is passed to the callout function pointed to
     by the 
     <i>completionFn</i> parameter. This parameter is optional and can be <b>NULL</b>.</p>
</dd>
</dl>

## -returns
<p>The 
     <b>FwpsInjectMacReceiveAsync0</b> function returns one of the following NTSTATUS codes.</p><dl>
<dt><b>STATUS_SUCCESS</b></dt>
</dl><p>The MAC frame data injection was initiated successfully. The filter engine calls the completion
       function after the filter engine has completed injecting the MAC frame data, or
       when an error occurred subsequently. In case of an error, the 
       <b>Status</b> member of the completed 
       <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> structure will indicate
       the reason for failure.</p><dl>
<dt><b>STATUS_FWP_TCPIP_NOT_READY</b></dt>
</dl><p>The MAC layer is not ready to accept injection of packet data.</p><dl>
<dt><b>STATUS_FWP_INJECT_HANDLE_CLOSING</b></dt>
</dl><p>The injection handle is being closed.</p><dl>
<dt><b>STATUS_FWP_INJECT_HANDLE_STALE</b></dt>
</dl><p>The injection handle was not created with the 
       <i>flags</i> parameter of the 
       <a href="https://msdn.microsoft.com/61cee8ef-1070-46d4-a541-94a9f09b593b">
       FwpsInjectionHandleCreate0</a> function set to FWPS_INJECTION_TYPE_L2.</p><dl>
<dt><b>Other status codes</b></dt>
</dl><p>An error occurred.</p>

<p> </p>

## -remarks
<p>A callback driver calls the <b>FwpsInjectMacReceiveAsync0</b>  function to reinject a previously absorbed MAC frame (or a clone of the frame) back to the layer 2 inbound data path it was intercepted from, or to inject an invented MAC frame.</p>

<p>The <i>netBufferLists</i> parameter can be a <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> chain. However the completion function could be invoked multiple times each, completing a segment (or single NET_BUFFER_LIST) of the chain.

</p>

<p>Injected frames could get classified again if the packets match the same filter as originally classified. Therefore, as with callouts at IP layers, layer 2 callouts must also protect against infinite packet inspection by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff551202">FwpsQueryPacketInjectionState0</a>.
</p>

<p>A callback driver calls the <b>FwpsInjectMacReceiveAsync0</b>  function to reinject a previously absorbed MAC frame (or a clone of the frame) back to the layer 2 inbound data path it was intercepted from, or to inject an invented MAC frame.</p>

<p>The <i>netBufferLists</i> parameter can be a <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> chain. However the completion function could be invoked multiple times each, completing a segment (or single NET_BUFFER_LIST) of the chain.

</p>

<p>Injected frames could get classified again if the packets match the same filter as originally classified. Therefore, as with callouts at IP layers, layer 2 callouts must also protect against infinite packet inspection by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff551202">FwpsQueryPacketInjectionState0</a>.
</p>

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
<p>Version</p>
</th>
<td width="70%">
<p>Available starting with Windows 8.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Fwpsk.h (include Fwpsk.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Fwpkclnt.lib</dt>
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
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544887">classifyFn</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/c03656ec-f0fe-49f5-8a04-2d26ef23c50a">completionFn</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/72759748-fac6-45b9-9a81-ab71e6e7c3ef">
     FwpsAllocateCloneNetBufferList0</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/d7f2d3c0-f2c9-4624-b3e1-9fbbf64c7186">
     FwpsAllocateNetBufferAndNetBufferList0</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/61cee8ef-1070-46d4-a541-94a9f09b593b">
       FwpsInjectionHandleCreate0</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551202">FwpsQueryPacketInjectionState0</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20FwpsInjectMacReceiveAsync0 function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>