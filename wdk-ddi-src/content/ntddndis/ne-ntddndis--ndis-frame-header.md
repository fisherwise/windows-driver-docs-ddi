---
UID: NE.ntddndis._NDIS_FRAME_HEADER
title: NDIS_FRAME_HEADER
author: windows-driver-content
description: The NDIS_FRAME_HEADER enumeration identifies the type of header in a network data frame.
old-location: netvista\ndis_frame_header.htm
ms.assetid: 8897ae0c-6068-4fea-8944-1340595dbff3
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: netvista
req.header: ntddndis.h
req.include-header: Ndis.h
req.target-type: Windows
req.target-min-winverclnt: Supported in NDIS 6.20 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NDIS_FRAME_HEADER
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

# NDIS_FRAME_HEADER enumeration



## -description
<p>The <b>NDIS_FRAME_HEADER</b> enumeration identifies the type of header in a network data frame.</p>


## -syntax

````
typedef enum _NDIS_FRAME_HEADER { 
  NdisFrameHeaderUndefined,
  NdisFrameHeaderMac,
  NdisFrameHeaderArp,
  NdisFrameHeaderIPv4,
  NdisFrameHeaderIPv6,
  NdisFrameHeaderUdp,
  NdisFrameHeaderMaximum
} NDIS_FRAME_HEADER, *PNDIS_FRAME_HEADER;
````


## -enum-fields
<dl>

### -field <a id="NdisFrameHeaderUndefined"></a><a id="ndisframeheaderundefined"></a><a id="NDISFRAMEHEADERUNDEFINED"></a><b>NdisFrameHeaderUndefined</b>

<dd>
<p>An undefined frame header type.</p>
</dd>

### -field <a id="NdisFrameHeaderMac"></a><a id="ndisframeheadermac"></a><a id="NDISFRAMEHEADERMAC"></a><b>NdisFrameHeaderMac</b>

<dd>
<p>A media access control (MAC) header.</p>
</dd>

### -field <a id="NdisFrameHeaderArp"></a><a id="ndisframeheaderarp"></a><a id="NDISFRAMEHEADERARP"></a><b>NdisFrameHeaderArp</b>

<dd>
<p>An Address Resolution Protocol (ARP) header.</p>
</dd>

### -field <a id="NdisFrameHeaderIPv4"></a><a id="ndisframeheaderipv4"></a><a id="NDISFRAMEHEADERIPV4"></a><b>NdisFrameHeaderIPv4</b>

<dd>
<p>An IP version 4 (IPv4) header.</p>
</dd>

### -field <a id="NdisFrameHeaderIPv6"></a><a id="ndisframeheaderipv6"></a><a id="NDISFRAMEHEADERIPV6"></a><b>NdisFrameHeaderIPv6</b>

<dd>
<p>An IP version 6 (IPv6) header.</p>
</dd>

### -field <a id="NdisFrameHeaderUdp"></a><a id="ndisframeheaderudp"></a><a id="NDISFRAMEHEADERUDP"></a><b>NdisFrameHeaderUdp</b>

<dd>
<p>A User Datagram Protocol
(UDP) header.</p>
</dd>

### -field <a id="NdisFrameHeaderMaximum"></a><a id="ndisframeheadermaximum"></a><a id="NDISFRAMEHEADERMAXIMUM"></a><b>NdisFrameHeaderMaximum</b>

<dd>
<p>The maximum value for this enumeration. This value might change in future versions of the NDIS
     header files and binaries.</p>
</dd>
</dl>

## -remarks
<p>The NDIS_FRAME_HEADER enumeration is used in the 
    <a href="https://msdn.microsoft.com/3d387fe9-a7cc-4034-b31e-ba1359db2ae1">
    NDIS_RECEIVE_FILTER_FIELD_PARAMETERS</a> structure.</p>

<p>The NDIS_FRAME_HEADER enumeration is used in the 
    <a href="https://msdn.microsoft.com/3d387fe9-a7cc-4034-b31e-ba1359db2ae1">
    NDIS_RECEIVE_FILTER_FIELD_PARAMETERS</a> structure.</p>

<p>The NDIS_FRAME_HEADER enumeration is used in the 
    <a href="https://msdn.microsoft.com/3d387fe9-a7cc-4034-b31e-ba1359db2ae1">
    NDIS_RECEIVE_FILTER_FIELD_PARAMETERS</a> structure.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Supported in NDIS 6.20 and later.</p>
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
<dt>
<a href="https://msdn.microsoft.com/3d387fe9-a7cc-4034-b31e-ba1359db2ae1">
   NDIS_RECEIVE_FILTER_FIELD_PARAMETERS</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NDIS_FRAME_HEADER enumeration%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>