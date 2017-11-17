---
UID: NC.ndis.FILTER_SEND_NET_BUFFER_LISTS_COMPLETE
title: FILTER_SEND_NET_BUFFER_LISTS_COMPLETE
author: windows-driver-content
description: NDIS calls the FilterSendNetBufferListsComplete function to complete a send request that a filter driver started by calling the NdisFSendNetBufferLists function.Note  You must declare the function by using the FILTER_SEND_NET_BUFFER_LISTS_COMPLETE type.
old-location: netvista\filtersendnetbufferlistscomplete.htm
ms.assetid: 1a3a1e80-29f1-4f19-b3c7-9a8b189f18c4
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
req.alt-api: FilterSendNetBufferListsComplete
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
req.irql: <= DISPATCH_LEVEL
ms.keywords: RxNameCacheInitialize
req.iface: 
---

# FILTER_SEND_NET_BUFFER_LISTS_COMPLETE callback



## -description
<p>NDIS calls the 
  <i>FilterSendNetBufferListsComplete</i> function to complete a send request that a filter driver started by
  calling the 
  <a href="https://msdn.microsoft.com/fe0896ab-2d20-465f-a8bc-bfc0033701d6">
  NdisFSendNetBufferLists</a> function.</p>


## -prototype

````
FILTER_SEND_NET_BUFFER_LISTS_COMPLETE FilterSendNetBufferListsComplete;

VOID FilterSendNetBufferListsComplete(
  _In_ NDIS_HANDLE      FilterModuleContext,
  _In_ PNET_BUFFER_LIST NetBufferLists,
  _In_ ULONG            SendCompleteFlags
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

### -param <i>NetBufferLists</i> [in]

<dd>
<p>A pointer to a linked list of 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> structures that the filter
     driver passed to 
     <a href="https://msdn.microsoft.com/fe0896ab-2d20-465f-a8bc-bfc0033701d6">
  NdisFSendNetBufferLists</a>.</p>
</dd>

### -param <i>SendCompleteFlags</i> [in]

<dd>
<p>NDIS flags that can be combined with an OR operation. To clear all the flags, set this member to zero. This function supports the following flags:</p>
<p></p>
<dl>

### -param <a id="NDIS_SEND_COMPLETE_FLAGS_DISPATCH_LEVEL"></a><a id="ndis_send_complete_flags_dispatch_level"></a>NDIS_SEND_COMPLETE_FLAGS_DISPATCH_LEVEL

<dd>
<p>Specifies that the current IRQL is DISPATCH_LEVEL. For more information about this flag, see 
        <a href="NULL">Dispatch IRQL Tracking</a>.</p>
</dd>

### -param <a id="NDIS_SEND_COMPLETE_FLAGS_SWITCH_SINGLE_SOURCE"></a><a id="ndis_send_complete_flags_switch_single_source"></a>NDIS_SEND_COMPLETE_FLAGS_SWITCH_SINGLE_SOURCE

<dd>
<p>If this flag is set, all packets in a linked list of <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> structures originated from the same Hyper-V extensible switch source port.</p>
<p>For more information, see <a href="NULL">Hyper-V Extensible Switch Send and Receive Flags</a>.</p>
<div class="alert"><b>Note</b>  If each packet in the linked list of <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> structures uses the same source port, the extension should set the <b>NDIS_SEND_FLAGS_SWITCH_SINGLE_SOURCE</b> flag in the <i>SendFlags</i> parameter of <a href="https://msdn.microsoft.com/1b3fc0c8-95da-47e5-8ff1-b7967f5148e7">SendNetBufferLists</a> when it sends the request.</div>
<div> </div>
<div class="alert"><b>Note</b>  This flag is available in NDIS 6.30 and later.</div>
<div> </div>
</dd>
</dl>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p><i>FilterSendNetBufferListsComplete</i> is an optional function. If a filter driver does not filter send
    requests, it can set the entry point for this function to <b>NULL</b> when it calls the 
    <a href="https://msdn.microsoft.com/14381de2-36d9-4ec8-9d4e-7af3e6d8ecf3">
    NdisFRegisterFilterDriver</a> function.</p>

<p>The filter driver can call the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff564550">NdisSetOptionalHandlers</a> function,
    from the 
    <a href="https://msdn.microsoft.com/04b7ac32-8996-4648-8c88-aa9f630b1bc4">FilterSetModuleOptions</a> function,
    to specify a 
    <i>FilterSendNetBufferListsComplete</i> function for a filter module.</p>

<p>When NDIS calls 
    <i>FilterSendNetBufferListsComplete</i>, the filter driver regains ownership of the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> structures and associated
    data.</p>

<p>If an overlying driver initiated the send request, the filter driver should call the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff562618">NdisFSendNetBufferListsComplete</a> function to complete the send request.</p>

<p>If the filter driver originated the send request, 
    <i>FilterSendNetBufferListsComplete</i> can either release the <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> structures and associated
    data or prepare them for reuse in a subsequent call to 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff562616">NdisFSendNetBufferLists</a>.</p>

<p>NDIS calls 
    <i>FilterSendNetBufferListsComplete</i> at IRQL &lt;= DISPATCH_LEVEL.</p>

<p>To define a <i>FilterSendNetBufferListsComplete</i> function, you must first provide a function declaration that identifies the type of function you're defining. Windows provides a set of function types for drivers. Declaring a function using the function types helps <a href="NULL">Code Analysis for Drivers</a>, <a href="NULL">Static Driver Verifier</a> (SDV), and other verification tools find errors, and it's a requirement for writing drivers for the Windows operating system.</p>

<p>For example, to define a <i>FilterSendNetBufferListsComplete</i> function that is named "MySendNetBufferListsComplete", use the <b>FILTER_SEND_NET_BUFFER_LISTS_COMPLETE</b> type as shown in this code example:</p>

<p>Then, implement your function as follows:</p>

<p>The <b>FILTER_SEND_NET_BUFFER_LISTS_COMPLETE</b> function type is defined in the Ndis.h header file. To more accurately identify errors when you run the code analysis tools, be sure to add the _Use_decl_annotations_ annotation to your function definition.  The _Use_decl_annotations_ annotation ensures that the annotations that are applied to the <b>FILTER_SEND_NET_BUFFER_LISTS_COMPLETE</b> function type in the header file are used.  For more information about the requirements for function declarations, see <a href="NULL">Declaring Functions by Using Function Role Types for NDIS Drivers</a>.

For information about  _Use_decl_annotations_, see <a href="http://go.microsoft.com/fwlink/p/?linkid=286697">Annotating Function Behavior</a>. </p>

<p><i>FilterSendNetBufferListsComplete</i> is an optional function. If a filter driver does not filter send
    requests, it can set the entry point for this function to <b>NULL</b> when it calls the 
    <a href="https://msdn.microsoft.com/14381de2-36d9-4ec8-9d4e-7af3e6d8ecf3">
    NdisFRegisterFilterDriver</a> function.</p>

<p>The filter driver can call the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff564550">NdisSetOptionalHandlers</a> function,
    from the 
    <a href="https://msdn.microsoft.com/04b7ac32-8996-4648-8c88-aa9f630b1bc4">FilterSetModuleOptions</a> function,
    to specify a 
    <i>FilterSendNetBufferListsComplete</i> function for a filter module.</p>

<p>When NDIS calls 
    <i>FilterSendNetBufferListsComplete</i>, the filter driver regains ownership of the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> structures and associated
    data.</p>

<p>If an overlying driver initiated the send request, the filter driver should call the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff562618">NdisFSendNetBufferListsComplete</a> function to complete the send request.</p>

<p>If the filter driver originated the send request, 
    <i>FilterSendNetBufferListsComplete</i> can either release the <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> structures and associated
    data or prepare them for reuse in a subsequent call to 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff562616">NdisFSendNetBufferLists</a>.</p>

<p>NDIS calls 
    <i>FilterSendNetBufferListsComplete</i> at IRQL &lt;= DISPATCH_LEVEL.</p>

<p>To define a <i>FilterSendNetBufferListsComplete</i> function, you must first provide a function declaration that identifies the type of function you're defining. Windows provides a set of function types for drivers. Declaring a function using the function types helps <a href="NULL">Code Analysis for Drivers</a>, <a href="NULL">Static Driver Verifier</a> (SDV), and other verification tools find errors, and it's a requirement for writing drivers for the Windows operating system.</p>

<p>For example, to define a <i>FilterSendNetBufferListsComplete</i> function that is named "MySendNetBufferListsComplete", use the <b>FILTER_SEND_NET_BUFFER_LISTS_COMPLETE</b> type as shown in this code example:</p>

<p>Then, implement your function as follows:</p>

<p>The <b>FILTER_SEND_NET_BUFFER_LISTS_COMPLETE</b> function type is defined in the Ndis.h header file. To more accurately identify errors when you run the code analysis tools, be sure to add the _Use_decl_annotations_ annotation to your function definition.  The _Use_decl_annotations_ annotation ensures that the annotations that are applied to the <b>FILTER_SEND_NET_BUFFER_LISTS_COMPLETE</b> function type in the header file are used.  For more information about the requirements for function declarations, see <a href="NULL">Declaring Functions by Using Function Role Types for NDIS Drivers</a>.

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
<p>&lt;= DISPATCH_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff540442">FilterAttach</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/04b7ac32-8996-4648-8c88-aa9f630b1bc4">FilterSetModuleOptions</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562608">NdisFRegisterFilterDriver</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562616">NdisFSendNetBufferLists</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/5a9008eb-86ad-4e3c-85a2-c8fd1b8fb4cb">
   NdisFSendNetBufferListsComplete</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564550">NdisSetOptionalHandlers</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff568376">NET_BUFFER</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20FILTER_SEND_NET_BUFFER_LISTS_COMPLETE callback function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>