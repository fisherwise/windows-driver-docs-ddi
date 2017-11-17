---
UID: NF.ndis.NdisSendNetBufferLists
title: NdisSendNetBufferLists
author: windows-driver-content
description: Protocol drivers call the NdisSendNetBufferLists function to send network data that is contained in a list of NET_BUFFER_LIST structures.
old-location: netvista\ndissendnetbufferlists.htm
ms.assetid: f615acc4-7e3e-4390-8a6a-e68663fcc162
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: netvista
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Universal
req.target-min-winverclnt: Supported in NDIS 6.0 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NdisSendNetBufferLists
req.alt-loc: ndis.lib,ndis.dll
req.ddi-compliance: Irql_SendRcv_Function
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ndis.lib
req.dll: 
req.irql: <=DISPATCH_LEVEL
ms.keywords: NdisSendNetBufferLists
req.iface: 
---

# NdisSendNetBufferLists function



## -description
<p>Protocol drivers call the 
  <b>NdisSendNetBufferLists</b> function to send network data that is contained in a list of 
  <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> structures.</p>


## -syntax

````
VOID NdisSendNetBufferLists(
  _In_ NDIS_HANDLE      NdisBindingHandle,
  _In_ PNET_BUFFER_LIST NetBufferLists,
  _In_ NDIS_PORT_NUMBER PortNumber,
  _In_ ULONG            SendFlags
);
````


## -parameters
<dl>

### -param <i>NdisBindingHandle</i> [in]

<dd>
<p>A handle that identifies the target adapter. A previous call to 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff563715">NdisOpenAdapterEx</a> returned this
     handle.</p>
</dd>

### -param <i>NetBufferLists</i> [in]

<dd>
<p>A pointer to a linked list of 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> structures. Each
     NET_BUFFER_LIST structure describes a list of 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff568376">NET_BUFFER</a> structures.</p>
</dd>

### -param <i>PortNumber</i> [in]

<dd>
<p>A port number that identifies a miniport adapter port. The default port number of a miniport
     adapter is zero. Protocol drivers that do not use miniport adapter ports should specify the default
     port.</p>
</dd>

### -param <i>SendFlags</i> [in]

<dd>
<p>Flags that define attributes for the send operation. The flags can be combined with an OR
     operation. To clear all the flags, set this member to zero. This function supports the following flags:
     </p>
<p></p>
<dl>

### -param <a id="NDIS_SEND_FLAGS_DISPATCH_LEVEL"></a><a id="ndis_send_flags_dispatch_level"></a>NDIS_SEND_FLAGS_DISPATCH_LEVEL

<dd>
<p>Specifies that the current IRQL is DISPATCH_LEVEL. For more information about this flag, see 
       <a href="NULL">Dispatch IRQL Tracking</a>.</p>
</dd>

### -param <a id="NDIS_SEND_FLAGS_CHECK_FOR_LOOPBACK"></a><a id="ndis_send_flags_check_for_loopback"></a>NDIS_SEND_FLAGS_CHECK_FOR_LOOPBACK

<dd>
<p>Specifies that NDIS should check for loopback. By default, NDIS does not loop back data to the
       driver that submitted the send request. An overlying driver can override this behavior by setting this
       flag. When this flag is set, NDIS identifies all the NET_BUFFER structures that contain data that
       matches the receive criteria for the binding. NDIS indicates NET_BUFFER structures that match the
       criteria to the overlying driver. This flag has no affect on checking for loopback, or looping back,
       on other bindings.</p>
</dd>
</dl>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>After a protocol driver calls 
    <b>NdisSendNetBufferLists</b>, NDIS submits the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> structures to an underlying
    driver's 
    <a href="https://msdn.microsoft.com/0bd5966d-66a6-4548-8c84-7cedced2cf40">
    MiniportSendNetBufferLists</a> function.</p>

<p>The protocol driver must allocate each NET_BUFFER_LIST structure from a pool by calling one of the
    following functions:</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561609">NdisAllocateNetBufferList</a>
</p>

<p>
<a href="https://msdn.microsoft.com/b872eff3-2d0a-4f01-874d-e00e09195801">
       NdisAllocateNetBufferAndNetBufferList</a>
</p>

<p>
<a href="https://msdn.microsoft.com/357605a1-5c57-44ed-97b3-f466f9a7182c">
       NdisAllocateCloneNetBufferList</a>
</p>

<p>The protocol driver can preallocate NET_BUFFER_LIST structures--for example, in its 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff552644">DriverEntry</a> routine. Alternatively, the driver,
    can allocate the structures just prior to calling 
    <b>NdisSendNetBufferLists</b> and then free them when the send operation is complete. When NDIS returns a
    NET_BUFFER_LIST structure to 
    <a href="https://msdn.microsoft.com/bc9197c5-ce0b-42b2-8225-fb9d83427ac8">
    ProtocolSendNetBufferListsComplete</a>, the miniport driver can prepare the NET_BUFFER_LIST structure
    and any associated resources for reuse. Reusing the NET_BUFFER_LIST structures can yield better
    performance than returning the structures to a pool and then reallocating them for another send
    operation.</p>

<p>A protocol driver must set the 
    <b>SourceHandle</b> member of each NET_BUFFER_LIST structure to the same value that it passes to the 
    <i>NdisBindingHandle</i> parameter. The binding handle provides the information that
    NDIS requires to return the NET_BUFFER_LIST structure to the protocol driver after the underlying
    miniport driver calls 
    <a href="https://msdn.microsoft.com/33890582-5eba-4cc1-a0d9-ec07f18da453">
    NdisMSendNetBufferListsComplete</a>.</p>

<p>Before calling 
    <b>NdisSendNetBufferLists</b>, a protocol driver can set information that accompanies the send request
    with the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff568401">NET_BUFFER_LIST_INFO</a> macro . The
    underlying driver can retrieve this information with the NET_BUFFER_LIST_INFO macro.</p>

<p>Before a protocol driver calls 
    <b>NdisSendNetBufferLists</b> with a list of NET_BUFFER_LIST structures, the protocol driver must ensure
    that the NET_BUFFER_LIST structures are set up in the order that the network data should be sent over the
    wire.</p>

<p>As soon as a protocol driver calls 
    <b>NdisSendNetBufferLists</b>, it relinquishes ownership of the NET_BUFFER_LIST structures and all
    associated resources. NDIS calls the 
    <i>ProtocolSendNetBufferListsComplete</i> function to return the structures and data
    to the protocol driver. NDIS can collect the structures and data from multiple send requests into a
    single linked list of NET_BUFFER_LIST structures before it passes the list to 
    <i>ProtocolSendNetBufferListsComplete.</i></p>

<p>Until NDIS calls 
    <i>ProtocolSendNetBufferListsComplete</i>, the current status of a
    protocol-driver-initiated send is not available to the protocol driver. A protocol driver temporarily
    releases ownership of all resources that it allocated for a send request when it calls 
    <b>NdisSendNetBufferLists</b>. A protocol driver should 
    <i>never</i> attempt to examine the NET_BUFFER_LIST structures or any associated data
    after calling 
    <b>NdisSendNetBufferLists</b>.</p>

<p>After a protocol driver calls 
    <b>NdisSendNetBufferLists</b>, NDIS submits the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> structures to an underlying
    driver's 
    <a href="https://msdn.microsoft.com/0bd5966d-66a6-4548-8c84-7cedced2cf40">
    MiniportSendNetBufferLists</a> function.</p>

<p>The protocol driver must allocate each NET_BUFFER_LIST structure from a pool by calling one of the
    following functions:</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561609">NdisAllocateNetBufferList</a>
</p>

<p>
<a href="https://msdn.microsoft.com/b872eff3-2d0a-4f01-874d-e00e09195801">
       NdisAllocateNetBufferAndNetBufferList</a>
</p>

<p>
<a href="https://msdn.microsoft.com/357605a1-5c57-44ed-97b3-f466f9a7182c">
       NdisAllocateCloneNetBufferList</a>
</p>

<p>The protocol driver can preallocate NET_BUFFER_LIST structures--for example, in its 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff552644">DriverEntry</a> routine. Alternatively, the driver,
    can allocate the structures just prior to calling 
    <b>NdisSendNetBufferLists</b> and then free them when the send operation is complete. When NDIS returns a
    NET_BUFFER_LIST structure to 
    <a href="https://msdn.microsoft.com/bc9197c5-ce0b-42b2-8225-fb9d83427ac8">
    ProtocolSendNetBufferListsComplete</a>, the miniport driver can prepare the NET_BUFFER_LIST structure
    and any associated resources for reuse. Reusing the NET_BUFFER_LIST structures can yield better
    performance than returning the structures to a pool and then reallocating them for another send
    operation.</p>

<p>A protocol driver must set the 
    <b>SourceHandle</b> member of each NET_BUFFER_LIST structure to the same value that it passes to the 
    <i>NdisBindingHandle</i> parameter. The binding handle provides the information that
    NDIS requires to return the NET_BUFFER_LIST structure to the protocol driver after the underlying
    miniport driver calls 
    <a href="https://msdn.microsoft.com/33890582-5eba-4cc1-a0d9-ec07f18da453">
    NdisMSendNetBufferListsComplete</a>.</p>

<p>Before calling 
    <b>NdisSendNetBufferLists</b>, a protocol driver can set information that accompanies the send request
    with the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff568401">NET_BUFFER_LIST_INFO</a> macro . The
    underlying driver can retrieve this information with the NET_BUFFER_LIST_INFO macro.</p>

<p>Before a protocol driver calls 
    <b>NdisSendNetBufferLists</b> with a list of NET_BUFFER_LIST structures, the protocol driver must ensure
    that the NET_BUFFER_LIST structures are set up in the order that the network data should be sent over the
    wire.</p>

<p>As soon as a protocol driver calls 
    <b>NdisSendNetBufferLists</b>, it relinquishes ownership of the NET_BUFFER_LIST structures and all
    associated resources. NDIS calls the 
    <i>ProtocolSendNetBufferListsComplete</i> function to return the structures and data
    to the protocol driver. NDIS can collect the structures and data from multiple send requests into a
    single linked list of NET_BUFFER_LIST structures before it passes the list to 
    <i>ProtocolSendNetBufferListsComplete.</i></p>

<p>Until NDIS calls 
    <i>ProtocolSendNetBufferListsComplete</i>, the current status of a
    protocol-driver-initiated send is not available to the protocol driver. A protocol driver temporarily
    releases ownership of all resources that it allocated for a send request when it calls 
    <b>NdisSendNetBufferLists</b>. A protocol driver should 
    <i>never</i> attempt to examine the NET_BUFFER_LIST structures or any associated data
    after calling 
    <b>NdisSendNetBufferLists</b>.</p>

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
<p>&lt;=DISPATCH_LEVEL</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548004">Irql_SendRcv_Function</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552644">DriverEntry</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/357605a1-5c57-44ed-97b3-f466f9a7182c">
   NdisAllocateCloneNetBufferList</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561609">NdisAllocateNetBufferList</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/b872eff3-2d0a-4f01-874d-e00e09195801">
   NdisAllocateNetBufferAndNetBufferList</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562779">NdisMAllocatePort</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/33890582-5eba-4cc1-a0d9-ec07f18da453">
   NdisMSendNetBufferListsComplete</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563715">NdisOpenAdapterEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/0bd5966d-66a6-4548-8c84-7cedced2cf40">MiniportSendNetBufferLists</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff568376">NET_BUFFER</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff568401">NET_BUFFER_LIST_INFO</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/bc9197c5-ce0b-42b2-8225-fb9d83427ac8">
   ProtocolSendNetBufferListsComplete</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NdisSendNetBufferLists function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>