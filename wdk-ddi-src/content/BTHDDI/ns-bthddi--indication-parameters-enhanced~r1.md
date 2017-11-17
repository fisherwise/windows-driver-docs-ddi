---
UID: NS.bthddi._INDICATION_PARAMETERS_ENHANCED~r1
title: INDICATION_PARAMETERS_ENHANCED
author: windows-driver-content
description: The INDICATION_PARAMETERS_ENHANCED structure is passed as the Parameters parameter to a profile driver's enhanced L2CAP Callback Function.
old-location: bltooth\indication_parameters_enhanced.htm
ms.assetid: D0FBA555-B61F-4D6F-B93F-C77D395F2BCD
ms.author: windowsdriverdev
ms.date: 10/23/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: bltooth
req.header: bthddi.h
req.include-header: Bthddi.h
req.target-type: Windows
req.target-min-winverclnt: Versions: Supported in Windows 8 and later versions of Windows
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: INDICATION_PARAMETERS_ENHANCED
req.alt-loc: Bthddi.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: Developers should code this function to operate at either IRQL = DISPATCH_LEVEL (if the callback
   function does not access paged memory), or IRQL = PASSIVE_LEVEL (if the callback function must access
   paged memory)
ms.keywords: INDICATION_PARAMETERS_ENHANCED, INDICATION_PARAMETERS_ENHANCED, *PINDICATION_PARAMETERS_ENHANCED
req.iface: IBidiSpl2
---

# INDICATION_PARAMETERS_ENHANCED structure



## -description
<p>The INDICATION_PARAMETERS_ENHANCED structure is passed as the Parameters parameter to a profile driver's <a href="https://msdn.microsoft.com/1C08937A-2B0C-4A6C-ACDF-1A751BF0D6F6">enhanced L2CAP Callback Function</a>
</p>


## -syntax

````
typedef struct _INDICATION_PARAMETERS_ENHANCED {
  L2CAP_CHANNEL_HANDLE ConnectionHandle;
  BTH_ADDR             BtAddress;
  union {
    struct {
      struct {
        USHORT PSM;
      } Request;
    } Connect;
    struct {
      CHANNEL_CONFIG_PARAMETERS_ENHANCED CurrentParams;
      CHANNEL_CONFIG_PARAMETERS_ENHANCED RequestedParams;
      CHANNEL_CONFIG_PARAMETERS_ENHANCED ResponseParams;
      USHORT                             Response;
    } ConfigRequest;
    struct {
      CHANNEL_CONFIG_PARAMETERS_ENHANCED CurrentParams;
      CHANNEL_CONFIG_PARAMETERS_ENHANCED RequestedParams;
      CHANNEL_CONFIG_PARAMETERS_ENHANCED RejectedParams;
      PCO_TYPE                           UnknownTypes;
      ULONG                              NumUnknownTypes;
      CHANNEL_CONFIG_PARAMETERS_ENHANCED NewRequestParams;
      USHORT                             Response;
    } ConfigResponse;
    struct {
      ULONG                NumExtraOptions;
      PL2CAP_CONFIG_OPTION ExtraOptions;
    } FreeExtraOptions;
    struct {
      L2CAP_DISCONNECT_REASON Reason;
      BOOLEAN                 CloseNow;
    } Disconnect;
    struct {
      ULONG PacketLength;
      ULONG TotalQueueLength;
    } RecvPacket;
    PVOID  Reserved;
  } Parameters;
} INDICATION_PARAMETERS_ENHANCED, *PINDICATION_PARAMETERS_ENHANCED;
````


## -struct-fields
<dl>

### -field <b>ConnectionHandle</b>

<dd>
<p>The L2CAP connection handle to the remote device. This handle is only valid for notifications that
     arrive over an established L2CAP connection.</p>
</dd>

### -field <b>BtAddress</b>

<dd>
<p>The Bluetooth address of the remote device.</p>
</dd>

### -field <b>Parameters</b>

<dd>
<dl>

### -field <b>Connect</b>

<dd>
<p>The structure that contains parameters for the 
      <i>IndicationRemoteConnect</i> callback function.</p>
<dl>

### -field <b>Request</b>

<dd>
<p>The structure that contains the parameters for a connection request.</p>
<dl>

### -field <b>PSM</b>

<dd>
<p>The Protocol/Service Multiplexer (PSM) that is passed to the calling function when the 
        <i>IndicationRemoteConnect</i> INDICATION_CODE value is specified in the enhanced callback function's 
        <i>Indication</i> parameter.</p>
</dd>
</dl>
</dd>
</dl>
</dd>

### -field <b>ConfigRequest</b>

<dd>
<p>The structure that contains parameters for the 
      <i>IndicationRemoteConfigRequest</i> INDICATION_CODE value.</p>
<dl>

### -field <b>CurrentParams</b>

<dd>
<p>A 
       <a href="https://msdn.microsoft.com/library/windows/hardware/hh450869">CHANNEL_CONFIG_PARAMETERS_ENHANCED</a> structure that contains the parameters for the current channel. This
       value is only valid if the channel was previously open and is now in the process of being configured.
       This member is used when the callback function specifies the 
       <i>IndicationRemoteConfigRequest</i> INDICATION_CODE value.</p>
</dd>

### -field <b>RequestedParams</b>

<dd>
<p>A CHANNEL_CONFIG_PARAMETERS_ENHANCED structure that contains the parameters that are passed from the
       remote host for configuration requests. This member is used when the callback function specifies the 
       <i>IndicationRemoteConfigRequest</i> INDICATION_CODE value.</p>
</dd>

### -field <b>ResponseParams</b>

<dd>
<p>A CHANNEL_CONFIG_PARAMETERS_ENHANCED structure that contains the parameters that the profile driver
       responds to the configuration request with.</p>
</dd>

### -field <b>Response</b>

<dd>
<p>A flag that indicates the status of the configuration request. Valid flag values are listed in
       the following table.
       </p>
<table>
<tr>
<th>Flag</th>
<th>Description</th>
</tr>
<tr>
<td>
<p>CONFIG_STATUS_SUCCESS</p>
</td>
<td>
<p>The configuration request was successful.</p>
</td>
</tr>
<tr>
<td>
<p>CONFIG_STATUS_DISCONNECT</p>
</td>
<td>
<p>The configuration request failed because the enhanced L2CAP connection was disconnected.</p>
</td>
</tr>
<tr>
<td>
<p>CONFIG_STATUS_INVALID_PARAMETER</p>
</td>
<td>
<p>The configuration request failed because an invalid parameter was passed to the profile
          driver.</p>
</td>
</tr>
<tr>
<td>
<p>CONFIG_STATUS_REJECT</p>
</td>
<td>
<p>The profile driver rejected the configuration request.</p>
</td>
</tr>
<tr>
<td>
<p>CONFIG_STATUS_UNKNOWN_OPTION</p>
</td>
<td>
<p>The configuration request failed because one of the specified configuration options was not
          recognized by the profile driver.</p>
</td>
</tr>
</table>
<p> </p>
</dd>
</dl>
</dd>

### -field <b>ConfigResponse</b>

<dd>
<p>The structure that contains parameters for the 
      <i>IndicationRemoteConfigResponse</i> INDICATION_CODE value.</p>
<dl>

### -field <b>CurrentParams</b>

<dd>
<p>A 
       <a href="https://msdn.microsoft.com/library/windows/hardware/hh450869">CHANNEL_CONFIG_PARAMETERS_ENHANCED</a> structure that contains the parameters for the current channel. This
       value is only valid if the channel was previously open and is now in the process of being configured.
       This member is used when the callback function specifies the 
       <i>IndicationRemoteConfigRequest</i> INDICATION_CODE value.</p>
</dd>

### -field <b>RequestedParams</b>

<dd>
<p>A CHANNEL_CONFIG_PARAMETERS_ENHANCED structure that contains the parameters that are passed from the
       remote host for configuration requests. This member is used when the callback function specifies the 
       <i>IndicationRemoteConfigRequest</i> INDICATION_CODE value.</p>
</dd>

### -field <b>RejectedParams</b>

<dd>
<p>A CHANNEL_CONFIG_PARAMETERS_ENHANCED structure that contains the configuration parameter settings that
       were rejected by the remote device.</p>
</dd>

### -field <b>UnknownTypes</b>

<dd>
<p>An array of types that were not recognized by the responding device.</p>
</dd>

### -field <b>NumUnknownTypes</b>

<dd>
<p>The number of unrecognized types in the 
       <b>UnknownTypes</b> member.</p>
</dd>

### -field <b>NewRequestParams</b>

<dd>
<p>A CHANNEL_CONFIG_PARAMETERS_ENHANCED structure that contains the parameter settings for the enhanced callback
       function to resubmit after the response has returned from the remote device.</p>
</dd>

### -field <b>Response</b>

<dd>
<p>A flag that indicates the status of the configuration request. Valid flag values are listed in
       the following table.
       </p>
<table>
<tr>
<th>Flag</th>
<th>Description</th>
</tr>
<tr>
<td>
<p>CONFIG_STATUS_SUCCESS</p>
</td>
<td>
<p>The configuration request was successful.</p>
</td>
</tr>
<tr>
<td>
<p>CONFIG_STATUS_DISCONNECT</p>
</td>
<td>
<p>The configuration request failed because the enhanced L2CAP connection was disconnected.</p>
</td>
</tr>
<tr>
<td>
<p>CONFIG_STATUS_INVALID_PARAMETER</p>
</td>
<td>
<p>The configuration request failed because an invalid parameter was passed to the profile
          driver.</p>
</td>
</tr>
<tr>
<td>
<p>CONFIG_STATUS_REJECT</p>
</td>
<td>
<p>The profile driver rejected the configuration request.</p>
</td>
</tr>
<tr>
<td>
<p>CONFIG_STATUS_UNKNOWN_OPTION</p>
</td>
<td>
<p>The configuration request failed because one of the specified configuration options was not
          recognized by the profile driver.</p>
</td>
</tr>
</table>
<p> </p>
</dd>
</dl>
</dd>

### -field <b>FreeExtraOptions</b>

<dd>
<p>The structure that contains parameters for the 
      <i>IndicationFreeExtraOptions</i> INDICATION_CODE value.</p>
<dl>

### -field <b>NumExtraOptions</b>

<dd>
<p>The number of extra options contained in the 
       <b>ExtraOptions</b> member.</p>
</dd>

### -field <b>ExtraOptions</b>

<dd>
<p>Extra options.</p>
</dd>
</dl>
</dd>

### -field <b>Disconnect</b>

<dd>
<p>The structure that contains the parameters for the 
      <i>IndicationRemoteDisconnect</i> INDICATION_CODE value.</p>
<dl>

### -field <b>Reason</b>

<dd>
<p>An 
       <a href="https://msdn.microsoft.com/library/windows/hardware/ff536763">L2CAP_DISCONNECT_REASON</a> value that
       indicates why the L2CAP connection to the remote device was terminated.</p>
</dd>

### -field <b>CloseNow</b>

<dd>
<p>A Boolean value that a profile driver uses to notify the Bluetooth driver stack to close the
       L2CAP connection. Set this member to <b>TRUE</b> to notify the Bluetooth driver stack to close the
       connection. Otherwise, set it to <b>FALSE</b> to keep the connection open.</p>
</dd>
</dl>
</dd>

### -field <b>RecvPacket</b>

<dd>
<p>The structure that contains the parameters for the 
      <i>IndicationRecvPacket</i> INDICATION_CODE value.</p>
<dl>

### -field <b>PacketLength</b>

<dd>
<p>The size, in bytes, of the packet that the callback function sent over the L2CAP
       connection.</p>
</dd>

### -field <b>TotalQueueLength</b>

<dd>
<p>The number of packets to be processed over the L2CAP connection.</p>
</dd>
</dl>
</dd>

### -field <b>Reserved</b>

<dd>
<p>Reserved member. Do not use.</p>
</dd>
</dl>
</dd>
</dl>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Versions: Supported in Windows 8 and later versions of Windows</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Bthddi.h (include Bthddi.h)</dt>
</dl>
</td>
</tr>
</table>