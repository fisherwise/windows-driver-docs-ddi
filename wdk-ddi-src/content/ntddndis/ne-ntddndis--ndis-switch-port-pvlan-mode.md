---
UID: NE.ntddndis._NDIS_SWITCH_PORT_PVLAN_MODE
title: NDIS_SWITCH_PORT_PVLAN_MODE
author: windows-driver-content
description: The NDIS_SWITCH_PORT_PVLAN_MODE enumeration specifies the operation mode of a private virtual local area network (PVLAN) policy property. This property is specified for a port on the Hyper-V extensible switch.
old-location: netvista\ndis_switch_port_pvlan_mode.htm
ms.assetid: 8B07B225-D612-47D2-B93C-7F9E3A23ACE1
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: netvista
req.header: ntddndis.h
req.include-header: Ndis.h
req.target-type: Windows
req.target-min-winverclnt: Supported in NDIS 6.30 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NDIS_SWITCH_PORT_PVLAN_MODE
req.alt-loc: Ntddndis.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: GET_CONFIGURATION_IOCTL_INPUT, GET_CONFIGURATION_IOCTL_INPUT, *PGET_CONFIGURATION_IOCTL_INPUT
req.iface: 
---

# NDIS_SWITCH_PORT_PVLAN_MODE enumeration



## -description
<p>
<p>The <b>NDIS_SWITCH_PORT_PVLAN_MODE</b> enumeration specifies the operation mode of a private virtual local area network (PVLAN) policy property. This property is specified for a port on the Hyper-V extensible switch.</p>
</p>
<p>The <b>NDIS_SWITCH_PORT_PVLAN_MODE</b> enumeration specifies the operation mode of a private virtual local area network (PVLAN) policy property. This property is specified for a port on the Hyper-V extensible switch.</p>


## -syntax

````
typedef enum  { 
  NdisSwitchPortPvlanModeUndefined    = 0,
  NdisSwitchPortPvlanModeIsolated,
  NdisSwitchPortPvlanModeCommunity,
  NdisSwitchPortPvlanModePromiscuous
} NDIS_SWITCH_PORT_PVLAN_MODE, *PNDIS_SWITCH_PORT_PVLAN_MODE;
````


## -enum-fields
<dl>

### -field <a id="NdisSwitchPortPvlanModeUndefined"></a><a id="ndisswitchportpvlanmodeundefined"></a><a id="NDISSWITCHPORTPVLANMODEUNDEFINED"></a><b>NdisSwitchPortPvlanModeUndefined</b>

<dd>
<p>This value specifies an undefined PVLAN operation mode.</p>
</dd>

### -field <a id="NdisSwitchPortPvlanModeIsolated"></a><a id="ndisswitchportpvlanmodeisolated"></a><a id="NDISSWITCHPORTPVLANMODEISOLATED"></a><b>NdisSwitchPortPvlanModeIsolated</b>

<dd>
<p>This value specifies a port that operates in PVLAN isolated mode. In isolated mode, the port can receive traffic only on the primary VLAN. It sends traffic on the secondary VLAN.</p>
</dd>

### -field <a id="NdisSwitchPortPvlanModeCommunity"></a><a id="ndisswitchportpvlanmodecommunity"></a><a id="NDISSWITCHPORTPVLANMODECOMMUNITY"></a><b>NdisSwitchPortPvlanModeCommunity</b>

<dd>
<p>This value specifies a port that operates in PVLAN community mode. In community mode, the port can receive traffic on the primary and secondary VLAN. However, the port can send traffic only on its secondary VLAN.</p>
</dd>

### -field <a id="NdisSwitchPortPvlanModePromiscuous"></a><a id="ndisswitchportpvlanmodepromiscuous"></a><a id="NDISSWITCHPORTPVLANMODEPROMISCUOUS"></a><b>NdisSwitchPortPvlanModePromiscuous</b>

<dd>
<p>This value specifies a port that operates in PVLAN promiscuous mode. In promiscuous mode, the port can receive traffic on a defined set of primary and secondary VLANs. However, the port can send traffic only on its primary VLAN.</p>
</dd>
</dl>

## -remarks
<p>The <b>PvlanMode</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/hh598243">NDIS_SWITCH_PORT_PROPERTY_VLAN</a> structure is an <a href="https://msdn.microsoft.com/library/windows/hardware/hh598246">NDIS_SWITCH_PORT_VLAN_MODE</a> enumeration data type. 

</p>

<p>For more information about extensible switch port policies, see <a href="NULL">Hyper-V Extensible Switch Policies</a>.

</p>

<p>The <b>PvlanMode</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/hh598243">NDIS_SWITCH_PORT_PROPERTY_VLAN</a> structure is an <a href="https://msdn.microsoft.com/library/windows/hardware/hh598246">NDIS_SWITCH_PORT_VLAN_MODE</a> enumeration data type. 

</p>

<p>For more information about extensible switch port policies, see <a href="NULL">Hyper-V Extensible Switch Policies</a>.

</p>

<p>The <b>PvlanMode</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/hh598243">NDIS_SWITCH_PORT_PROPERTY_VLAN</a> structure is an <a href="https://msdn.microsoft.com/library/windows/hardware/hh598246">NDIS_SWITCH_PORT_VLAN_MODE</a> enumeration data type. 

</p>

<p>For more information about extensible switch port policies, see <a href="NULL">Hyper-V Extensible Switch Policies</a>.

</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Supported in NDIS 6.30 and later.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntddndis.h (include Ndis.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt><b></b></dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh598210">NDIS_SWITCH_FORWARDING_DESTINATION_ARRAY</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh598243">NDIS_SWITCH_PORT_PROPERTY_VLAN</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NDIS_SWITCH_PORT_PVLAN_MODE enumeration%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>