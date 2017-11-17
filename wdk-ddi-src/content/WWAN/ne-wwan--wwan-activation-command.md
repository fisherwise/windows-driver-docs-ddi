---
UID: NE.wwan._WWAN_ACTIVATION_COMMAND
title: WWAN_ACTIVATION_COMMAND
author: windows-driver-content
description: The WWAN_ACTIVATION_COMMAND enumeration lists the Packet Data Protocol (PDP) activation commands that are supported by the MB device.
old-location: netvista\wwan_activation_command.htm
ms.assetid: e9d25ac3-8ffc-4137-8409-731d8caaa730
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: netvista
req.header: wwan.h
req.include-header: Wwan.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows 7 and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: WWAN_ACTIVATION_COMMAND
req.alt-loc: wwan.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: 
ms.keywords: WUDF_WORKITEM_CONFIG, WUDF_WORKITEM_CONFIG, *PWUDF_WORKITEM_CONFIG
req.iface: 
req.product: Windows 10 or later.
---

# WWAN_ACTIVATION_COMMAND enumeration



## -description
<p>The WWAN_ACTIVATION_COMMAND enumeration lists the Packet Data Protocol (PDP) activation commands that
  are supported by the MB device.</p>


## -syntax

````
typedef enum _WWAN_ACTIVATION_COMMAND { 
  WwanActivationCommandDeactivate  = 0,
  WwanActivationCommandActivate,
  WwanActivationCommandMax
} WWAN_ACTIVATION_COMMAND, *PWWAN_ACTIVATION_COMMAND;
````


## -enum-fields
<dl>

### -field <a id="WwanActivationCommandDeactivate"></a><a id="wwanactivationcommanddeactivate"></a><a id="WWANACTIVATIONCOMMANDDEACTIVATE"></a><b>WwanActivationCommandDeactivate</b>

<dd>
<p>Deactivate a currently activated PDP context identified by 
     <b>ConnectionId</b> .</p>
</dd>

### -field <a id="WwanActivationCommandActivate"></a><a id="wwanactivationcommandactivate"></a><a id="WWANACTIVATIONCOMMANDACTIVATE"></a><b>WwanActivationCommandActivate</b>

<dd>
<p>Activate PDP context.</p>
</dd>

### -field <a id="WwanActivationCommandMax"></a><a id="wwanactivationcommandmax"></a><a id="WWANACTIVATIONCOMMANDMAX"></a><b>WwanActivationCommandMax</b>

<dd>
<p>The total number of supported activation commands.</p>
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
<p>Available in Windows 7 and later versions of Windows.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wwan.h (include Wwan.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff571235">WWAN_SET_CONTEXT_STATE</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20WWAN_ACTIVATION_COMMAND enumeration%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>