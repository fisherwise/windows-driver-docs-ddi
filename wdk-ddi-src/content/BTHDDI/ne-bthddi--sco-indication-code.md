---
UID: NE.bthddi._SCO_INDICATION_CODE
title: SCO_INDICATION_CODE
author: windows-driver-content
description: The SCO_INDICATION_CODE enumeration type describes the type of an incoming SCO connection or bonding state change. The Bluetooth driver stack passes a value from this enumeration in the Indication argument of a profile driver's SCO Callback Function.
old-location: bltooth\sco_indication_code.htm
ms.assetid: 4223dd79-cac7-41bd-8c94-12baf8e8367a
ms.author: windowsdriverdev
ms.date: 10/23/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: bltooth
req.header: bthddi.h
req.include-header: Bthddi.h
req.target-type: Windows
req.target-min-winverclnt: Versions: Supported in Windows Vista, and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: SCO_INDICATION_CODE
req.alt-loc: bthddi.h
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
ms.keywords: IBidiSpl2, UnbindDevice, IBidiSpl2::UnbindDevice
req.iface: IBidiSpl2
---

# SCO_INDICATION_CODE enumeration



## -description
<p>The SCO_INDICATION_CODE enumeration type describes the type of an incoming SCO connection or bonding
  state change. The Bluetooth driver stack passes a value from this enumeration in the 
  <i>Indication</i> argument of a profile driver's 
  <a href="https://msdn.microsoft.com/abc9fc88-6852-4bfb-8271-7a73a508c397">SCO Callback Function</a>.</p>


## -syntax

````
typedef enum _SCO_INDICATION_CODE { 
  ScoIndicationAddReference      = 0,
  ScoIndicationReleaseReference  = 1,
  ScoIndicationRemoteConnect     = 2,
  ScoIndicationRemoteDisconnect  = 3
} SCO_INDICATION_CODE, *PSCO_INDICATION_CODE;
````


## -enum-fields
<dl>

### -field <a id="ScoIndicationAddReference"></a><a id="scoindicationaddreference"></a><a id="SCOINDICATIONADDREFERENCE"></a><b>ScoIndicationAddReference</b>

<dd>
<p>This value indicates that the profile driver should add one reference to its device object.</p>
</dd>

### -field <a id="ScoIndicationReleaseReference"></a><a id="scoindicationreleasereference"></a><a id="SCOINDICATIONRELEASEREFERENCE"></a><b>ScoIndicationReleaseReference</b>

<dd>
<p>This value indicates that the profile driver can release one reference to its device
     object.</p>
</dd>

### -field <a id="ScoIndicationRemoteConnect"></a><a id="scoindicationremoteconnect"></a><a id="SCOINDICATIONREMOTECONNECT"></a><b>ScoIndicationRemoteConnect</b>

<dd>
<p>This value indicates to a profile driver that a remote device is trying to connect to the local
     radio. Profile drivers accept or reject this request by 
     <a href="https://msdn.microsoft.com/53a692e7-9c71-4dca-9331-32ac97b94179">building and sending</a> a 
     <a href="bltooth.brb_sco_open_channel_response">
     BRB_SCO_OPEN_CHANNEL_RESPONSE</a> request.</p>
</dd>

### -field <a id="ScoIndicationRemoteDisconnect"></a><a id="scoindicationremotedisconnect"></a><a id="SCOINDICATIONREMOTEDISCONNECT"></a><b>ScoIndicationRemoteDisconnect</b>

<dd>
<p>This value indicates to a profile driver that a remote device is disconnecting from the local
     radio.</p>
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
<p>Versions: Supported in Windows Vista, and later.</p>
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

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/abc9fc88-6852-4bfb-8271-7a73a508c397">SCO Callback Function</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536751">IOCTL_INTERNAL_BTH_SUBMIT_BRB</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536628">BRB_SCO_REGISTER_SERVER</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [bltooth\bltooth]:%20SCO_INDICATION_CODE enumeration%20 RELEASE:%20(10/23/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>