---
UID: NE.ntddndis._NDIS_NIC_SWITCH_TYPE
title: NDIS_NIC_SWITCH_TYPE
author: windows-driver-content
description: The NDIS_NIC_SWITCH_TYPE enumeration specifies the type of the NIC switch on a network adapter.
old-location: netvista\ndis_nic_switch_type.htm
ms.assetid: F990F166-D9DA-43F5-95D3-86B9B11FACF1
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
req.alt-api: NDIS_NIC_SWITCH_TYPE
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

# NDIS_NIC_SWITCH_TYPE enumeration



## -description
<p>The <b>NDIS_NIC_SWITCH_TYPE</b> enumeration specifies the type of the NIC switch on a network adapter.

</p>


## -syntax

````
typedef enum _NDIS_NIC_SWITCH_TYPE { 
  NdisNicSwitchTypeUnspecified  = 0,
  NdisNicSwitchTypeExternal     = 1,
  NdisNicSwitchTypeMax          = 2
} NDIS_NIC_SWITCH_TYPE, *PNDIS_NIC_SWITCH_TYPE;
````


## -enum-fields
<dl>

### -field <a id="NdisNicSwitchTypeUnspecified"></a><a id="ndisnicswitchtypeunspecified"></a><a id="NDISNICSWITCHTYPEUNSPECIFIED"></a><b>NdisNicSwitchTypeUnspecified</b>

<dd>
<p>The NIC switch type is not specified.</p>
</dd>

### -field <a id="NdisNicSwitchTypeExternal"></a><a id="ndisnicswitchtypeexternal"></a><a id="NDISNICSWITCHTYPEEXTERNAL"></a><b>NdisNicSwitchTypeExternal</b>

<dd>
<p>This value specifies an external switch. The single root I/O virtualization (SR-IOV) virtual ports (VPorts) connected to this type of switch, including the default VPort, can access the external network through the physical port on the network adapter.</p>
</dd>

### -field <a id="NdisNicSwitchTypeMax"></a><a id="ndisnicswitchtypemax"></a><a id="NDISNICSWITCHTYPEMAX"></a><b>NdisNicSwitchTypeMax</b>

<dd>
<p>The maximum value for this enumeration. This value might change in future versions of the NDIS header files and binaries.

</p>
</dd>
</dl>

## -remarks
<p>The <b>SwitchType</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/hh451587">NDIS_NIC_SWITCH_PARAMETERS</a> and <a href="https://msdn.microsoft.com/library/windows/hardware/hh451582">NDIS_NIC_SWITCH_INFO</a> structures is an <b>NDIS_NIC_SWITCH_TYPE</b> enumeration data type. 

</p>

<p>For more information about the NIC switch, see <a href="NULL">SR-IOV Architecture</a>.</p>

<p>The <b>SwitchType</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/hh451587">NDIS_NIC_SWITCH_PARAMETERS</a> and <a href="https://msdn.microsoft.com/library/windows/hardware/hh451582">NDIS_NIC_SWITCH_INFO</a> structures is an <b>NDIS_NIC_SWITCH_TYPE</b> enumeration data type. 

</p>

<p>For more information about the NIC switch, see <a href="NULL">SR-IOV Architecture</a>.</p>

<p>The <b>SwitchType</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/hh451587">NDIS_NIC_SWITCH_PARAMETERS</a> and <a href="https://msdn.microsoft.com/library/windows/hardware/hh451582">NDIS_NIC_SWITCH_INFO</a> structures is an <b>NDIS_NIC_SWITCH_TYPE</b> enumeration data type. 

</p>

<p>For more information about the NIC switch, see <a href="NULL">SR-IOV Architecture</a>.</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/hh451582">NDIS_NIC_SWITCH_INFO</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh451587">NDIS_NIC_SWITCH_PARAMETERS</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NDIS_NIC_SWITCH_TYPE enumeration%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>