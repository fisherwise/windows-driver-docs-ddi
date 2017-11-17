---
UID: NS.ndis._NDIS_CO_CALL_MANAGER_OPTIONAL_HANDLERS
title: NDIS_CO_CALL_MANAGER_OPTIONAL_HANDLERS
author: windows-driver-content
description: The NDIS_CO_CALL_MANAGER_OPTIONAL_HANDLERS structure specifies CoNDIS call manager ProtocolXxx functions for the driver that passes this structure to the NdisSetOptionalHandlers function.
old-location: netvista\ndis_co_call_manager_optional_handlers.htm
ms.assetid: 12d541e1-04dd-4512-827e-d27f16260fe3
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: netvista
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Windows
req.target-min-winverclnt: Supported in NDIS 6.0 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NDIS_CO_CALL_MANAGER_OPTIONAL_HANDLERS
req.alt-loc: ndis.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: See Remarks section
ms.keywords: NDIS_CO_CALL_MANAGER_OPTIONAL_HANDLERS, NDIS_CO_CALL_MANAGER_OPTIONAL_HANDLERS, *PNDIS_CO_CALL_MANAGER_OPTIONAL_HANDLERS
req.iface: 
---

# NDIS_CO_CALL_MANAGER_OPTIONAL_HANDLERS structure



## -description
<p>The NDIS_CO_CALL_MANAGER_OPTIONAL_HANDLERS structure specifies CoNDIS call manager 
  <i>ProtocolXxx</i> functions for the driver that passes this structure to the 
  <a href="https://msdn.microsoft.com/97649f4f-942a-47fc-a541-6f160c8b4eb4">
  NdisSetOptionalHandlers</a> function.</p>


## -syntax

````
typedef struct _NDIS_CO_CALL_MANAGER_OPTIONAL_HANDLERS {
  NDIS_OBJECT_HEADER                  Header;
  ULONG                               Reserved;
  CO_CREATE_VC_HANDLER                CmCreateVcHandler;
  CO_DELETE_VC_HANDLER                CmDeleteVcHandler;
  CM_OPEN_AF_HANDLER                  CmOpenAfHandler;
  CM_CLOSE_AF_HANDLER                 CmCloseAfHandler;
  CM_REG_SAP_HANDLER                  CmRegisterSapHandler;
  CM_DEREG_SAP_HANDLER                CmDeregisterSapHandler;
  CM_MAKE_CALL_HANDLER                CmMakeCallHandler;
  CM_CLOSE_CALL_HANDLER               CmCloseCallHandler;
  CM_INCOMING_CALL_COMPLETE_HANDLER   CmIncomingCallCompleteHandler;
  CM_ADD_PARTY_HANDLER                CmAddPartyHandler;
  CM_DROP_PARTY_HANDLER               CmDropPartyHandler;
  CM_ACTIVATE_VC_COMPLETE_HANDLER     CmActivateVcCompleteHandler;
  CM_DEACTIVATE_VC_COMPLETE_HANDLER   CmDeactivateVcCompleteHandler;
  CM_MODIFY_CALL_QOS_HANDLER          CmModifyCallQoSHandler;
  CO_OID_REQUEST_HANDLER              CmOidRequestHandler;
  CO_OID_REQUEST_COMPLETE_HANDLER     CmOidRequestCompleteHandler;
  CM_NOTIFY_CLOSE_AF_COMPLETE_HANDLER CmNotifyCloseAfCompleteHandler;
} NDIS_CO_CALL_MANAGER_OPTIONAL_HANDLERS, *PNDIS_CO_CALL_MANAGER_OPTIONAL_HANDLERS;
````


## -struct-fields
<dl>

### -field <b>Header</b>

<dd>
<p>The 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff566588">NDIS_OBJECT_HEADER</a> structure for the
     call manager CoNDIS characteristics structure (NDIS_CO_CALL_MANAGER_OPTIONAL_HANDLERS). Set the 
     <b>Type</b> member of the structure that 
     <b>Header</b> specifies to NDIS_OBJECT_TYPE_CO_CALL_MANAGER_OPTIONAL_HANDLERS, the 
     <b>Revision</b> member to NDIS_CO_CALL_MANAGER_OPTIONAL_HANDLERS_REVISION_1, and the 
     <b>Size</b> member to NDIS_SIZEOF_CO_CALL_MANAGER_OPTIONAL_HANDLERS_REVISION_1.</p>
</dd>

### -field <b>Reserved</b>

<dd>
<p>Reserved for NDIS.</p>
</dd>

### -field <b>CmCreateVcHandler</b>

<dd>
<p>The entry point of the caller's 
     <a href="https://msdn.microsoft.com/b086dd24-74f5-474a-8684-09bf92ac731b">ProtocolCoCreateVc</a> function.</p>
</dd>

### -field <b>CmDeleteVcHandler</b>

<dd>
<p>The entry point of the caller's 
     <a href="https://msdn.microsoft.com/d761270f-bf77-441e-834c-9ac7fb3d350f">ProtocolCoDeleteVc</a> function.</p>
</dd>

### -field <b>CmOpenAfHandler</b>

<dd>
<p>The entry point of the caller's 
     <a href="https://msdn.microsoft.com/7422c205-bc41-4121-b430-ff9e6b49dc2e">ProtocolCmOpenAf</a> function.</p>
</dd>

### -field <b>CmCloseAfHandler</b>

<dd>
<p>The entry point of the caller's 
     <a href="https://msdn.microsoft.com/a7a02813-62e4-49c5-abb6-a90f4e092b9f">ProtocolCmCloseAf</a> function.</p>
</dd>

### -field <b>CmRegisterSapHandler</b>

<dd>
<p>The entry point of the caller's 
     <a href="https://msdn.microsoft.com/3e3e7a0e-a8d2-40b2-895b-187d24867080">
     ProtocolCmRegisterSap</a> function.</p>
</dd>

### -field <b>CmDeregisterSapHandler</b>

<dd>
<p>The entry point of the caller's 
     <a href="https://msdn.microsoft.com/738c426e-aa4f-4f59-b955-fbf67071303f">
     ProtocolCmDeregisterSap</a> function.</p>
</dd>

### -field <b>CmMakeCallHandler</b>

<dd>
<p>The entry point of the caller's 
     <a href="https://msdn.microsoft.com/ede0a18a-cd3b-4fbb-a16b-e7493940d633">ProtocolCmMakeCall</a> function.</p>
</dd>

### -field <b>CmCloseCallHandler</b>

<dd>
<p>The entry point of the caller's 
     <a href="https://msdn.microsoft.com/b5307e1b-3905-4e43-a0b0-0068ba18ef0d">
     ProtocolCmCloseCall</a> function.</p>
</dd>

### -field <b>CmIncomingCallCompleteHandler</b>

<dd>
<p>The entry point of the caller's 
     <a href="https://msdn.microsoft.com/353e929b-17c8-47e8-82fd-b646e93a5b9a">
     ProtocolCmIncomingCallComplete</a> function.</p>
</dd>

### -field <b>CmAddPartyHandler</b>

<dd>
<p>The entry point of the caller's 
     <a href="https://msdn.microsoft.com/06aa5ff6-974c-43dd-8395-bc1a1a8421d5">ProtocolCmAddParty</a> function.</p>
</dd>

### -field <b>CmDropPartyHandler</b>

<dd>
<p>The entry point of the caller's 
     <a href="https://msdn.microsoft.com/be0fce3e-7308-42fa-b63a-4d5cfec7ea6c">
     ProtocolCmDropParty</a> function.</p>
</dd>

### -field <b>CmActivateVcCompleteHandler</b>

<dd>
<p>The entry point of the caller's 
     <a href="https://msdn.microsoft.com/6ec9e73e-8abd-4d27-b598-6176f2125348">
     ProtocolCmActivateVcComplete</a> function.</p>
</dd>

### -field <b>CmDeactivateVcCompleteHandler</b>

<dd>
<p>The entry point of the caller's 
     <a href="https://msdn.microsoft.com/44ee0e3c-aee9-4e24-9e54-c57248b568b6">
     ProtocolCmDeactivateVcComplete</a> function.</p>
</dd>

### -field <b>CmModifyCallQoSHandler</b>

<dd>
<p>The entry point of the caller's 
     <a href="https://msdn.microsoft.com/24523677-9f5a-4109-8484-95883a4d1bbf">
     ProtocolCmModifyCallQoS</a> function.</p>
</dd>

### -field <b>CmOidRequestHandler</b>

<dd>
<p>The entry point of the caller's 
     <a href="https://msdn.microsoft.com/8247396f-8781-45da-aba1-a31a2a26a46f">
     ProtocolCoOidRequest</a> function.</p>
</dd>

### -field <b>CmOidRequestCompleteHandler</b>

<dd>
<p>The entry point of the caller's 
     <a href="https://msdn.microsoft.com/16883c64-3cc6-4f50-8be7-7c58c422a717">
     ProtocolCoOidRequestComplete</a> function.</p>
</dd>

### -field <b>CmNotifyCloseAfCompleteHandler</b>

<dd>
<p>The entry point of the caller's 
     <a href="https://msdn.microsoft.com/c5bdedee-dacd-4f4d-a3d1-f1cb71a68001">
     ProtocolCmNotifyCloseAfComplete</a> function.</p>
</dd>
</dl>

## -remarks
<p>To specify entry points as a CoNDIS call manager, a protocol driver or miniport call manager (MCM)
    initializes an NDIS_CO_CALL_MANAGER_OPTIONAL_HANDLERS structure and passes it to the 
    <a href="https://msdn.microsoft.com/97649f4f-942a-47fc-a541-6f160c8b4eb4">
    NdisSetOptionalHandlers</a> function.</p>

<p>A stand-alone call manager calls 
     <b>NdisSetOptionalHandlers</b> from the 
     <a href="https://msdn.microsoft.com/342e23ad-d38b-4100-949a-220b8fbdcf6e">ProtocolSetOptions</a> function. The
     call manager must set every entry point in the NDIS_CO_CALL_MANAGER_OPTIONAL_HANDLERS structure to a
     driver-supplied 
     <i>ProtocolXxx</i> function when it calls 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff564550">NdisSetOptionalHandlers</a>, even if
     the call manager does not support incoming calls, outgoing calls, or point-to-multipoint connections.
     For whatever subset of connection-oriented functionality that such a call manager does not support, its
     placeholder 
     <i>ProtocolXxx</i> functions should simply return NDIS_STATUS_NOT_SUPPORTED.</p>

<p>After a stand-alone call manager calls the 
     <a href="https://msdn.microsoft.com/8890bf31-f2c7-48b0-926d-8931893ede86">
     NdisCmRegisterAddressFamilyEx</a> function successfully, NDIS ignores any entry point that the call
     manager previously specified for the 
     <a href="https://msdn.microsoft.com/2706577e-ba03-4347-9672-7303752ec0fe">
     ProtocolOidRequestComplete</a> function of the 
     <a href="https://msdn.microsoft.com/db64c160-9db6-4b23-af14-e64acdb9ef57">
     NDIS_PROTOCOL_DRIVER_CHARACTERISTICS</a> structure that it passed to the 
     <a href="https://msdn.microsoft.com/b48571eb-13a2-4541-80ac-c8d31f378d37">
     NdisRegisterProtocolDriver</a> function.</p>

<p>An MCM calls the 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff564550">NdisSetOptionalHandlers</a> function
     from the 
     <a href="https://msdn.microsoft.com/feecae74-960c-43cf-aa70-8ab0da3d0dfe">MiniportSetOptions</a> function. The
     MCM must set every 
     <b>Cm</b><i>Xxx</i> member in the NDIS_CO_CALL_MANAGER_OPTIONAL_HANDLERS structure to a MCM-supplied 
     <i>ProtocolXxx</i> function even if the MCM does not support incoming calls, outgoing calls, or
     point-to-multipoint connections. For whatever subset of connection-oriented functionality that such an
     MCM driver does not support, its 
     <i>ProtocolXxx</i> functions should simply return NDIS_STATUS_NOT_SUPPORTED. For example, NDIS never
     calls an MCM driver's registered 
     <a href="https://msdn.microsoft.com/6ec9e73e-8abd-4d27-b598-6176f2125348">
     ProtocolCmActivateVcComplete</a> or 
     <a href="https://msdn.microsoft.com/44ee0e3c-aee9-4e24-9e54-c57248b568b6">
     ProtocolCmDeactivateVcComplete</a> function, so these functions can return NDIS_STATUS_NOT_SUPPORTED
     but must have entry points in the NDIS_CO_CALL_MANAGER_OPTIONAL_HANDLERS structure.</p>

<p>An MCM driver must specify entry points for the 
     <a href="https://msdn.microsoft.com/b086dd24-74f5-474a-8684-09bf92ac731b">ProtocolCoCreateVc</a> and 
     <a href="https://msdn.microsoft.com/d761270f-bf77-441e-834c-9ac7fb3d350f">ProtocolCoDeleteVc</a> functions. If
     the MCM previously registered a 
     <a href="https://msdn.microsoft.com/99eaba29-ce17-4e79-878e-5fdf7411e56c">MiniportCoCreateVc</a> or 
     <a href="https://msdn.microsoft.com/ed9b6ad1-059b-47d9-b1f7-10d498c5d2d4">MiniportCoDeleteVc</a> function. NDIS
     ignores the entry points for these functions, whenever NDIS calls the MCM driver to create or delete a
     virtual connection (VC). Therefore, NDIS passes in an 
     <i>NdisAfHandle</i> value for the initial parameter to the MCM-supplied 
     <i>ProtocolCoCreateVc</i> or 
     <i>ProtocolCoDeleteVc</i> function, rather than the 
     <i>MiniportAdapterContext</i> value that it would pass to the 
     <i>MiniportCoCreateVc</i> or 
     <i>MiniportCoDeleteVc</i> function of a non-MCM miniport driver.</p>

<p>An MCM driver cannot set the 
     <b>CmOidRequestHandler</b> member of NDIS_CO_CALL_MANAGER_OPTIONAL_HANDLERS to its 
     <a href="https://msdn.microsoft.com/903bcdc5-9d42-4067-a054-057edc95ccf7">MiniportCoOidRequest</a> function.
     The driver must provide a separate entry point for a 
     <a href="https://msdn.microsoft.com/8247396f-8781-45da-aba1-a31a2a26a46f">ProtocolCoOidRequest</a> function. An
     MCM driver must have a 
     <i>ProtocolCoOidRequest</i> function to handle call manager requests from CoNDIS clients and must have a 
     <a href="https://msdn.microsoft.com/16883c64-3cc6-4f50-8be7-7c58c422a717">
     ProtocolCoOidRequestComplete</a> function.</p>

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
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/99eaba29-ce17-4e79-878e-5fdf7411e56c">MiniportCoCreateVc</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/ed9b6ad1-059b-47d9-b1f7-10d498c5d2d4">MiniportCoDeleteVc</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/903bcdc5-9d42-4067-a054-057edc95ccf7">MiniportCoOidRequest</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/feecae74-960c-43cf-aa70-8ab0da3d0dfe">MiniportSetOptions</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff566588">NDIS_OBJECT_HEADER</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/db64c160-9db6-4b23-af14-e64acdb9ef57">
   NDIS_PROTOCOL_DRIVER_CHARACTERISTICS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/8890bf31-f2c7-48b0-926d-8931893ede86">
   NdisCmRegisterAddressFamilyEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564520">NdisRegisterProtocolDriver</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564550">NdisSetOptionalHandlers</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/6ec9e73e-8abd-4d27-b598-6176f2125348">
   ProtocolCmActivateVcComplete</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/06aa5ff6-974c-43dd-8395-bc1a1a8421d5">ProtocolCmAddParty</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/a7a02813-62e4-49c5-abb6-a90f4e092b9f">ProtocolCmCloseAf</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/b5307e1b-3905-4e43-a0b0-0068ba18ef0d">ProtocolCmCloseCall</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/44ee0e3c-aee9-4e24-9e54-c57248b568b6">
   ProtocolCmDeactivateVcComplete</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/738c426e-aa4f-4f59-b955-fbf67071303f">ProtocolCmDeregisterSap</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/be0fce3e-7308-42fa-b63a-4d5cfec7ea6c">ProtocolCmDropParty</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/353e929b-17c8-47e8-82fd-b646e93a5b9a">
   ProtocolCmIncomingCallComplete</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/ede0a18a-cd3b-4fbb-a16b-e7493940d633">ProtocolCmMakeCall</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/24523677-9f5a-4109-8484-95883a4d1bbf">ProtocolCmModifyCallQoS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/7422c205-bc41-4121-b430-ff9e6b49dc2e">ProtocolCmOpenAf</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/3e3e7a0e-a8d2-40b2-895b-187d24867080">ProtocolCmRegisterSap</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/2706577e-ba03-4347-9672-7303752ec0fe">ProtocolOidRequestComplete</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/342e23ad-d38b-4100-949a-220b8fbdcf6e">ProtocolSetOptions</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NDIS_CO_CALL_MANAGER_OPTIONAL_HANDLERS structure%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>