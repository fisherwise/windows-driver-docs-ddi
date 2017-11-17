---
UID: NC.ndis.PROTOCOL_CO_OID_REQUEST_COMPLETE
title: PROTOCOL_CO_OID_REQUEST_COMPLETE
author: windows-driver-content
description: The ProtocolCoOidRequestComplete function completes the processing of an asynchronous CoNDIS OID request.Note  You must declare the function by using the PROTOCOL_CO_OID_REQUEST_COMPLETE type.
old-location: netvista\protocolcooidrequestcomplete.htm
ms.assetid: 16883c64-3cc6-4f50-8be7-7c58c422a717
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
req.alt-api: ProtocolCoOidRequestComplete
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
req.irql: <= DISPATCH_LEVEL (see Remarks section)
ms.keywords: RxNameCacheInitialize
req.iface: 
---

# PROTOCOL_CO_OID_REQUEST_COMPLETE callback



## -description
<p>The 
  <i>ProtocolCoOidRequestComplete</i> function completes the processing of an asynchronous
  CoNDIS OID request.</p>


## -prototype

````
PROTOCOL_CO_OID_REQUEST_COMPLETE ProtocolCoOidRequestComplete;

VOID ProtocolCoOidRequestComplete(
  _In_    NDIS_HANDLE       ProtocolAfContext,
  _In_    NDIS_HANDLE       ProtocolVcContext,
  _In_    NDIS_HANDLE       ProtocolPartyContext,
  _Inout_ PNDIS_OID_REQUEST OidRequest,
  _In_    NDIS_STATUS       Status
)
{ ... }
````


## -parameters
<dl>

### -param <i>ProtocolAfContext</i> [in]

<dd>
<p>A handle that identifies an address family (AF) context area. If the driver is a client, it
     supplied this handle when it called the 
     <a href="https://msdn.microsoft.com/54170917-60b4-4d8f-bf92-df7d7dc0faee">
     NdisClOpenAddressFamilyEx</a> function to connect itself to the call manager. If the driver is a call
     manager or miniport call manager (MCM), it supplied this handle from its 
     <a href="https://msdn.microsoft.com/7422c205-bc41-4121-b430-ff9e6b49dc2e">ProtocolCmOpenAf</a> function.</p>
</dd>

### -param <i>ProtocolVcContext</i> [in]

<dd>
<p>A handle that identifies the active virtual connection (VC) that the driver requested or set
     information for, if the request was VC-specific. Otherwise, this parameter is <b>NULL</b>.</p>
</dd>

### -param <i>ProtocolPartyContext</i> [in]

<dd>
<p>A handle that identifies the party on a multipoint VC that the driver requested or set information
     for, if the request is party-specific. Otherwise, this parameter is <b>NULL</b>.</p>
</dd>

### -param <i>OidRequest</i> [in, out]

<dd>
<p>A pointer to the driver-supplied 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff566710">NDIS_OID_REQUEST</a> structure that was
     previously passed to the 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff561711">NdisCoOidRequest</a> or 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff563548">NdisMCmOidRequest</a> function.</p>
</dd>

### -param <i>Status</i> [in]

<dd>
<p>The final status of the request. The target driver or NDIS determines this final status. This
     parameter determines what 
     <i>ProtocolCoOidRequestComplete</i> does with the information at 
     <i>OidRequest</i>.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>NDIS calls the 
    <i>ProtocolCoOidRequestComplete</i> function to complete the processing of CoNDIS
    client, call manager, or MCM OID request for which the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff561711">NdisCoOidRequest</a> function or 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff563548">NdisMCmOidRequest</a> function returned
    NDIS_STATUS_PENDING.</p>

<p>To register 
    <i>ProtocolCoOidRequestComplete</i> as a client, a driver initializes an 
    <a href="https://msdn.microsoft.com/1f2285bb-be70-4496-905d-89106bf3712a">
    NDIS_CO_CLIENT_OPTIONAL_HANDLERS</a> structure and passes it at the 
    <i>OptionalHandlers</i> parameter of the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff564550">NdisSetOptionalHandlers</a> function.
    To register 
    <i>ProtocolCoOidRequestComplete</i> as a call manager, a driver initializes an 
    <a href="https://msdn.microsoft.com/12d541e1-04dd-4512-827e-d27f16260fe3">
    NDIS_CO_CALL_MANAGER_OPTIONAL_HANDLERS</a> structure and passes it at the 
    <i>OptionalHandlers</i> parameter of 
    <b>NdisSetOptionalHandlers</b>.</p>

<p>The target driver is the driver that serviced the OID information request. A target driver's call to
    the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff563568">NdisMCoOidRequestComplete</a>, 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff561716">NdisCoOidRequestComplete</a>, or 
    <a href="https://msdn.microsoft.com/4c45be9f-3d07-4150-830a-3aa6d74531ff">
    NdisMCmOidRequestComplete</a> function caused NDIS to call the 
    <i>ProtocolCoOidRequestComplete</i> function. NDIS forwards the value of the 
    <i>Status</i> parameter that was passed to these functions as the input 
    <i>Status</i> parameter to 
    <i>ProtocolCoOidRequestComplete</i>.</p>

<p><i>ProtocolCoOidRequestComplete</i> uses the input value of 
    <i>Status</i> as follows:</p>

<p>If 
      <i>Status</i> is NDIS_STATUS_SUCCESS, the 
      <b>BytesRead</b> or 
      <b>BytesWritten</b> member of the 
      <a href="https://msdn.microsoft.com/library/windows/hardware/ff566710">NDIS_OID_REQUEST</a> structure that the 
      <i>OidRequest</i> parameter points to specifies how much information was transferred
      from the buffer in the 
      <b>InformationBuffer</b> member of NDIS_OID_REQUEST to the target driver or how much information was
      returned at 
      <b>InformationBuffer</b>, respectively.</p>

<p>If the driver made a query request, 
      <i>ProtocolCoOidRequestComplete</i> can use the data that is returned in 
      <b>InformationBuffer</b> as appropriate for the value that is specified in the 
      <b>Oid</b> member of NDIS_OID_REQUEST.</p>

<p>If 
      <i>Status</i> is NDIS_STATUS_INVALID_LENGTH or NDIS_STATUS_BUFFER_TOO_SHORT, the 
      <b>BytesNeeded</b> member of the NDIS_OID_REQUEST structure that 
      <i>OidRequest</i> points to specifies the OID-specific value of the 
      <b>InformationBufferLength</b> member of NDIS_OID_REQUEST that is required to carry out the requested
      operation.</p>

<p>In these circumstances, 
      <i>ProtocolCoOidRequestComplete</i> can allocate sufficient buffer space for the
      request, set up another 
      <a href="https://msdn.microsoft.com/library/windows/hardware/ff566710">NDIS_OID_REQUEST</a> structure with the
      required value for 
      <b>InformationBufferLength</b>, and retry the OID request.</p>

<p>If 
      <i>Status</i> is an NDIS_STATUS_
      <i>XXX</i> value that is an unrecoverable error, 
      <i>ProtocolCoOidRequestComplete</i> should release the memory for the
      NDIS_OID_REQUEST structure. 
      <i>ProtocolCoOidRequestComplete</i> should also determine whether the driver should
      close the binding or adjust its binding-specific state information to handle continued network I/O
      operations on the binding.</p>

<p>For more information about system-defined OIDs, see 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff566707">NDIS OIDs</a>.</p>

<p><i>ProtocolCoOidRequestComplete</i> can be called before the driver has had time to
    inspect the status code that 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff561711">NdisCoOidRequest</a> or 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff563548">NdisMCmOidRequest</a> returns.</p>

<p>NDIS calls 
    <i>ProtocolCoOidRequestComplete</i> at IRQL &lt;= DISPATCH_LEVEL.</p>

<p>To define a <i>ProtocolCoOidRequestComplete</i> function, you must first provide a function declaration that identifies the type of function you're defining. Windows provides a set of function types for drivers. Declaring a function using the function types helps <a href="NULL">Code Analysis for Drivers</a>, <a href="NULL">Static Driver Verifier</a> (SDV), and other verification tools find errors, and it's a requirement for writing drivers for the Windows operating system.</p>

<p>For example, to define a <i>ProtocolCoOidRequestComplete</i> function that is named "MyCoOidRequestComplete", use the <b>PROTOCOL_CO_OID_REQUEST_COMPLETE</b> type as shown in this code example:</p>

<p>Then, implement your function as follows:</p>

<p>The <b>PROTOCOL_CO_OID_REQUEST_COMPLETE</b> function type is defined in the Ndis.h header file. To more accurately identify errors when you run the code analysis tools, be sure to add the _Use_decl_annotations_ annotation to your function definition.  The _Use_decl_annotations_ annotation ensures that the annotations that are applied to the <b>PROTOCOL_CO_OID_REQUEST_COMPLETE</b> function type in the header file are used.  For more information about the requirements for function declarations, see <a href="NULL">Declaring Functions by Using Function Role Types for NDIS Drivers</a>.

For information about  _Use_decl_annotations_, see <a href="http://go.microsoft.com/fwlink/p/?linkid=286697">Annotating Function Behavior</a>. </p>

<p>NDIS calls the 
    <i>ProtocolCoOidRequestComplete</i> function to complete the processing of CoNDIS
    client, call manager, or MCM OID request for which the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff561711">NdisCoOidRequest</a> function or 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff563548">NdisMCmOidRequest</a> function returned
    NDIS_STATUS_PENDING.</p>

<p>To register 
    <i>ProtocolCoOidRequestComplete</i> as a client, a driver initializes an 
    <a href="https://msdn.microsoft.com/1f2285bb-be70-4496-905d-89106bf3712a">
    NDIS_CO_CLIENT_OPTIONAL_HANDLERS</a> structure and passes it at the 
    <i>OptionalHandlers</i> parameter of the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff564550">NdisSetOptionalHandlers</a> function.
    To register 
    <i>ProtocolCoOidRequestComplete</i> as a call manager, a driver initializes an 
    <a href="https://msdn.microsoft.com/12d541e1-04dd-4512-827e-d27f16260fe3">
    NDIS_CO_CALL_MANAGER_OPTIONAL_HANDLERS</a> structure and passes it at the 
    <i>OptionalHandlers</i> parameter of 
    <b>NdisSetOptionalHandlers</b>.</p>

<p>The target driver is the driver that serviced the OID information request. A target driver's call to
    the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff563568">NdisMCoOidRequestComplete</a>, 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff561716">NdisCoOidRequestComplete</a>, or 
    <a href="https://msdn.microsoft.com/4c45be9f-3d07-4150-830a-3aa6d74531ff">
    NdisMCmOidRequestComplete</a> function caused NDIS to call the 
    <i>ProtocolCoOidRequestComplete</i> function. NDIS forwards the value of the 
    <i>Status</i> parameter that was passed to these functions as the input 
    <i>Status</i> parameter to 
    <i>ProtocolCoOidRequestComplete</i>.</p>

<p><i>ProtocolCoOidRequestComplete</i> uses the input value of 
    <i>Status</i> as follows:</p>

<p>If 
      <i>Status</i> is NDIS_STATUS_SUCCESS, the 
      <b>BytesRead</b> or 
      <b>BytesWritten</b> member of the 
      <a href="https://msdn.microsoft.com/library/windows/hardware/ff566710">NDIS_OID_REQUEST</a> structure that the 
      <i>OidRequest</i> parameter points to specifies how much information was transferred
      from the buffer in the 
      <b>InformationBuffer</b> member of NDIS_OID_REQUEST to the target driver or how much information was
      returned at 
      <b>InformationBuffer</b>, respectively.</p>

<p>If the driver made a query request, 
      <i>ProtocolCoOidRequestComplete</i> can use the data that is returned in 
      <b>InformationBuffer</b> as appropriate for the value that is specified in the 
      <b>Oid</b> member of NDIS_OID_REQUEST.</p>

<p>If 
      <i>Status</i> is NDIS_STATUS_INVALID_LENGTH or NDIS_STATUS_BUFFER_TOO_SHORT, the 
      <b>BytesNeeded</b> member of the NDIS_OID_REQUEST structure that 
      <i>OidRequest</i> points to specifies the OID-specific value of the 
      <b>InformationBufferLength</b> member of NDIS_OID_REQUEST that is required to carry out the requested
      operation.</p>

<p>In these circumstances, 
      <i>ProtocolCoOidRequestComplete</i> can allocate sufficient buffer space for the
      request, set up another 
      <a href="https://msdn.microsoft.com/library/windows/hardware/ff566710">NDIS_OID_REQUEST</a> structure with the
      required value for 
      <b>InformationBufferLength</b>, and retry the OID request.</p>

<p>If 
      <i>Status</i> is an NDIS_STATUS_
      <i>XXX</i> value that is an unrecoverable error, 
      <i>ProtocolCoOidRequestComplete</i> should release the memory for the
      NDIS_OID_REQUEST structure. 
      <i>ProtocolCoOidRequestComplete</i> should also determine whether the driver should
      close the binding or adjust its binding-specific state information to handle continued network I/O
      operations on the binding.</p>

<p>For more information about system-defined OIDs, see 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff566707">NDIS OIDs</a>.</p>

<p><i>ProtocolCoOidRequestComplete</i> can be called before the driver has had time to
    inspect the status code that 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff561711">NdisCoOidRequest</a> or 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff563548">NdisMCmOidRequest</a> returns.</p>

<p>NDIS calls 
    <i>ProtocolCoOidRequestComplete</i> at IRQL &lt;= DISPATCH_LEVEL.</p>

<p>To define a <i>ProtocolCoOidRequestComplete</i> function, you must first provide a function declaration that identifies the type of function you're defining. Windows provides a set of function types for drivers. Declaring a function using the function types helps <a href="NULL">Code Analysis for Drivers</a>, <a href="NULL">Static Driver Verifier</a> (SDV), and other verification tools find errors, and it's a requirement for writing drivers for the Windows operating system.</p>

<p>For example, to define a <i>ProtocolCoOidRequestComplete</i> function that is named "MyCoOidRequestComplete", use the <b>PROTOCOL_CO_OID_REQUEST_COMPLETE</b> type as shown in this code example:</p>

<p>Then, implement your function as follows:</p>

<p>The <b>PROTOCOL_CO_OID_REQUEST_COMPLETE</b> function type is defined in the Ndis.h header file. To more accurately identify errors when you run the code analysis tools, be sure to add the _Use_decl_annotations_ annotation to your function definition.  The _Use_decl_annotations_ annotation ensures that the annotations that are applied to the <b>PROTOCOL_CO_OID_REQUEST_COMPLETE</b> function type in the header file are used.  For more information about the requirements for function declarations, see <a href="NULL">Declaring Functions by Using Function Role Types for NDIS Drivers</a>.

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
<p>&lt;= DISPATCH_LEVEL (see Remarks section)</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/12d541e1-04dd-4512-827e-d27f16260fe3">
   NDIS_CO_CALL_MANAGER_OPTIONAL_HANDLERS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/1f2285bb-be70-4496-905d-89106bf3712a">
   NDIS_CO_CLIENT_OPTIONAL_HANDLERS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff566710">NDIS_OID_REQUEST</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561639">NdisClOpenAddressFamilyEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561711">NdisCoOidRequest</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561716">NdisCoOidRequestComplete</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563548">NdisMCmOidRequest</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563551">NdisMCmOidRequestComplete</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563568">NdisMCoOidRequestComplete</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564550">NdisSetOptionalHandlers</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/7422c205-bc41-4121-b430-ff9e6b49dc2e">ProtocolCmOpenAf</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20PROTOCOL_CO_OID_REQUEST_COMPLETE callback function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>