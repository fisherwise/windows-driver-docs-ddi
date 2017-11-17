---
UID: NC.ndis.PROTOCOL_CM_INCOMING_CALL_COMPLETE
title: PROTOCOL_CM_INCOMING_CALL_COMPLETE
author: windows-driver-content
description: The ProtocolCmIncomingCallComplete function is required.
old-location: netvista\protocolcmincomingcallcomplete.htm
ms.assetid: 353e929b-17c8-47e8-82fd-b646e93a5b9a
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: netvista
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Windows
req.target-min-winverclnt: Supported for NDIS 6.0 and NDIS 5.1 drivers (see 
   
   ProtocolCmIncomingCallComplete (NDIS 5.1)) in Windows Vista. Supported for NDIS 5.1 drivers (see 
   
   ProtocolCmIncomingCallComplete (NDIS 5.1)) in Windows XP.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: ProtocolCmIncomingCallComplete
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

# PROTOCOL_CM_INCOMING_CALL_COMPLETE callback



## -description
<p>The 
  <i>ProtocolCmIncomingCallComplete</i> function is required. When NDIS calls this function, 
  <i>ProtocolCmIncomingCallComplete</i> indicates to the call manager that the connection-oriented client has
  finished processing of an incoming call offer that the call manager previously dispatched through 
  <a href="https://msdn.microsoft.com/2172aeec-8502-414e-9d01-9292c0eb7ce8">
  NdisCmDispatchIncomingCall</a>.</p>


## -prototype

````
PROTOCOL_CM_INCOMING_CALL_COMPLETE ProtocolCmIncomingCallComplete;

VOID ProtocolCmIncomingCallComplete(
  _In_ NDIS_STATUS         Status,
  _In_ NDIS_HANDLE         CallMgrVcContext,
  _In_ PCO_CALL_PARAMETERS CallParameters
)
{ ... }
````


## -parameters
<dl>

### -param <i>Status</i> [in]

<dd>
<p>Indicates the final status of the operation to dispatch an incoming call to a connection-oriented
     client.</p>
</dd>

### -param <i>CallMgrVcContext</i> [in]

<dd>
<p>Specifies the handle to a call manager-allocated context area in which the call manager maintains
     its per-VC state. The call manager supplied this handle from its 
     <a href="https://msdn.microsoft.com/b086dd24-74f5-474a-8684-09bf92ac731b">ProtocolCoCreateVc</a> function.</p>
</dd>

### -param <i>CallParameters</i> [in]

<dd>
<p>Pointer to the call parameters as specified by the call manager in the call to 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff561664">NdisCmDispatchIncomingCall</a>.
     The signaling protocol determines which call parameters, if any, the call manager can change.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>When the connection-oriented client has completed processing of an incoming connection offer that the
    call manager dispatched to it, this routine will be called if 
    <b>NdisCmDispatchIncomingCall</b> returned NDIS_STATUS_PENDING. The final status of the incoming call is
    found in 
    <i>Status</i>. Possible values for 
    <i>Status</i> include, but are not limited to:</p>

<p></p><dl>
<dt><a id="NDIS_STATUS_SUCCESS"></a><a id="ndis_status_success"></a>NDIS_STATUS_SUCCESS</dt>
<dd>
<p>Indicates that the call manager has accepted the incoming call.</p>
</dd>
<dt><a id="NDIS_STATUS_FAILURE"></a><a id="ndis_status_failure"></a>NDIS_STATUS_FAILURE</dt>
<dd>
<p>Indicates that either the address family or the SAP that the call dispatched for is currently in
      the process of closing.</p>
</dd>
<dt><a id="NDIS_STATUS_RESOURCES"></a><a id="ndis_status_resources"></a>NDIS_STATUS_RESOURCES</dt>
<dd>
<p>Indicates that the incoming call was not accepted because the connection-oriented client was
      unable to dynamically allocate resources required for it to process the call.</p>
</dd>
<dt><a id="NDIS_STATUS_INVALID_DATA"></a><a id="ndis_status_invalid_data"></a>NDIS_STATUS_INVALID_DATA</dt>
<dd>
<p>Indicates that the connection-oriented client rejected the call because the call parameters
      specified were invalid.</p>
</dd>
</dl><p>Indicates that the call manager has accepted the incoming call.</p>

<p>Indicates that either the address family or the SAP that the call dispatched for is currently in
      the process of closing.</p>

<p>Indicates that the incoming call was not accepted because the connection-oriented client was
      unable to dynamically allocate resources required for it to process the call.</p>

<p>Indicates that the connection-oriented client rejected the call because the call parameters
      specified were invalid.</p>

<p>If the client accepts the incoming call, the call manager should send signaling message(s) to indicate
    to the calling entity that the call has been accepted. If the client does not accept the call, the call
    manager should send signaling message(s) to indicate that the call has been rejected.</p>

<p>To define a <i>ProtocolCmIncomingCallComplete</i> function, you must first provide a function declaration that identifies the type of function you're defining. Windows provides a set of function types for drivers. Declaring a function using the function types helps <a href="NULL">Code Analysis for Drivers</a>, <a href="NULL">Static Driver Verifier</a> (SDV), and other verification tools find errors, and it's a requirement for writing drivers for the Windows operating system.</p>

<p>For example, to define a <i>ProtocolCmIncomingCallComplete</i> function that is named "MyCmIncomingCallComplete", use the <b>PROTOCOL_CM_INCOMING_CALL_COMPLETE</b> type as shown in this code example:</p>

<p>Then, implement your function as follows:</p>

<p>The <b>PROTOCOL_CM_INCOMING_CALL_COMPLETE</b> function type is defined in the Ndis.h header file. To more accurately identify errors when you run the code analysis tools, be sure to add the _Use_decl_annotations_ annotation to your function definition.  The _Use_decl_annotations_ annotation ensures that the annotations that are applied to the <b>PROTOCOL_CM_INCOMING_CALL_COMPLETE</b> function type in the header file are used.  For more information about the requirements for function declarations, see <a href="NULL">Declaring Functions by Using Function Role Types for NDIS Drivers</a>.

For information about  _Use_decl_annotations_, see <a href="http://go.microsoft.com/fwlink/p/?linkid=286697">Annotating Function Behavior</a>. </p>

<p>When the connection-oriented client has completed processing of an incoming connection offer that the
    call manager dispatched to it, this routine will be called if 
    <b>NdisCmDispatchIncomingCall</b> returned NDIS_STATUS_PENDING. The final status of the incoming call is
    found in 
    <i>Status</i>. Possible values for 
    <i>Status</i> include, but are not limited to:</p>

<p></p><dl>
<dt><a id="NDIS_STATUS_SUCCESS"></a><a id="ndis_status_success"></a>NDIS_STATUS_SUCCESS</dt>
<dd>
<p>Indicates that the call manager has accepted the incoming call.</p>
</dd>
<dt><a id="NDIS_STATUS_FAILURE"></a><a id="ndis_status_failure"></a>NDIS_STATUS_FAILURE</dt>
<dd>
<p>Indicates that either the address family or the SAP that the call dispatched for is currently in
      the process of closing.</p>
</dd>
<dt><a id="NDIS_STATUS_RESOURCES"></a><a id="ndis_status_resources"></a>NDIS_STATUS_RESOURCES</dt>
<dd>
<p>Indicates that the incoming call was not accepted because the connection-oriented client was
      unable to dynamically allocate resources required for it to process the call.</p>
</dd>
<dt><a id="NDIS_STATUS_INVALID_DATA"></a><a id="ndis_status_invalid_data"></a>NDIS_STATUS_INVALID_DATA</dt>
<dd>
<p>Indicates that the connection-oriented client rejected the call because the call parameters
      specified were invalid.</p>
</dd>
</dl><p>Indicates that the call manager has accepted the incoming call.</p>

<p>Indicates that either the address family or the SAP that the call dispatched for is currently in
      the process of closing.</p>

<p>Indicates that the incoming call was not accepted because the connection-oriented client was
      unable to dynamically allocate resources required for it to process the call.</p>

<p>Indicates that the connection-oriented client rejected the call because the call parameters
      specified were invalid.</p>

<p>If the client accepts the incoming call, the call manager should send signaling message(s) to indicate
    to the calling entity that the call has been accepted. If the client does not accept the call, the call
    manager should send signaling message(s) to indicate that the call has been rejected.</p>

<p>To define a <i>ProtocolCmIncomingCallComplete</i> function, you must first provide a function declaration that identifies the type of function you're defining. Windows provides a set of function types for drivers. Declaring a function using the function types helps <a href="NULL">Code Analysis for Drivers</a>, <a href="NULL">Static Driver Verifier</a> (SDV), and other verification tools find errors, and it's a requirement for writing drivers for the Windows operating system.</p>

<p>For example, to define a <i>ProtocolCmIncomingCallComplete</i> function that is named "MyCmIncomingCallComplete", use the <b>PROTOCOL_CM_INCOMING_CALL_COMPLETE</b> type as shown in this code example:</p>

<p>Then, implement your function as follows:</p>

<p>The <b>PROTOCOL_CM_INCOMING_CALL_COMPLETE</b> function type is defined in the Ndis.h header file. To more accurately identify errors when you run the code analysis tools, be sure to add the _Use_decl_annotations_ annotation to your function definition.  The _Use_decl_annotations_ annotation ensures that the annotations that are applied to the <b>PROTOCOL_CM_INCOMING_CALL_COMPLETE</b> function type in the header file are used.  For more information about the requirements for function declarations, see <a href="NULL">Declaring Functions by Using Function Role Types for NDIS Drivers</a>.

For information about  _Use_decl_annotations_, see <a href="http://go.microsoft.com/fwlink/p/?linkid=286697">Annotating Function Behavior</a>. </p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Supported for NDIS 6.0 and NDIS 5.1 drivers (see 
   <a href="https://msdn.microsoft.com/bdd757ce-f052-4572-9451-8d2afe309365">
   ProtocolCmIncomingCallComplete (NDIS 5.1)</a>) in Windows Vista. Supported for NDIS 5.1 drivers (see 
   <i>
   ProtocolCmIncomingCallComplete (NDIS 5.1)</i>) in Windows XP.</p>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561664">NdisCmDispatchIncomingCall</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/8a5922ac-b22b-444e-9ea0-3bb56e71ef33">ProtocolClIncomingCall</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/3e3e7a0e-a8d2-40b2-895b-187d24867080">ProtocolCmRegisterSap</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20PROTOCOL_CM_INCOMING_CALL_COMPLETE callback function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>