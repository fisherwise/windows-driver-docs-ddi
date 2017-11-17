---
UID: NS.ntddndis._NDIS_TCP_IP_CHECKSUM_OFFLOAD
title: NDIS_TCP_IP_CHECKSUM_OFFLOAD
author: windows-driver-content
description: The NDIS_TCP_IP_CHECKSUM_OFFLOAD structure provides checksum task offload information in the NDIS_OFFLOAD structure.
old-location: netvista\ndis_tcp_ip_checksum_offload.htm
ms.assetid: bf5369c5-8656-41a4-a23f-79e40a60d111
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: netvista
req.header: ntddndis.h
req.include-header: Ndis.h
req.target-type: Windows
req.target-min-winverclnt: Supported in NDIS 6.0 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NDIS_TCP_IP_CHECKSUM_OFFLOAD
req.alt-loc: ntddndis.h
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
ms.keywords: NDIS_TCP_IP_CHECKSUM_OFFLOAD, NDIS_TCP_IP_CHECKSUM_OFFLOAD, *PNDIS_TCP_IP_CHECKSUM_OFFLOAD
req.iface: 
---

# NDIS_TCP_IP_CHECKSUM_OFFLOAD structure



## -description
<p>The NDIS_TCP_IP_CHECKSUM_OFFLOAD structure provides checksum task offload information in the 
  <a href="https://msdn.microsoft.com/library/windows/hardware/ff566599">NDIS_OFFLOAD</a> structure.</p>


## -syntax

````
typedef struct _NDIS_TCP_IP_CHECKSUM_OFFLOAD {
  struct {
    ULONG Encapsulation;
    ULONG IpOptionsSupported  :2;
    ULONG TcpOptionsSupported  :2;
    ULONG TcpChecksum  :2;
    ULONG UdpChecksum  :2;
    ULONG IpChecksum  :2;
  } IPv4Transmit;
  struct {
    ULONG Encapsulation;
    ULONG IpOptionsSupported  :2;
    ULONG TcpOptionsSupported  :2;
    ULONG TcpChecksum  :2;
    ULONG UdpChecksum  :2;
    ULONG IpChecksum  :2;
  } IPv4Receive;
  struct {
    ULONG Encapsulation;
    ULONG IpExtensionHeadersSupported  :2;
    ULONG TcpOptionsSupported  :2;
    ULONG TcpChecksum  :2;
    ULONG UdpChecksum  :2;
  } IPv6Transmit;
  struct {
    ULONG Encapsulation;
    ULONG IpExtensionHeadersSupported  :2;
    ULONG TcpOptionsSupported  :2;
    ULONG TcpChecksum  :2;
    ULONG UdpChecksum  :2;
  } IPv6Receive;
} NDIS_TCP_IP_CHECKSUM_OFFLOAD, *PNDIS_TCP_IP_CHECKSUM_OFFLOAD;
````


## -struct-fields
<dl>

### -field <b>IPv4Transmit</b>

<dd>
<p>A structure within NDIS_TCP_IP_CHECKSUM_OFFLOAD that specifies IPv4 transmit information and that
     contains the following members:
     
      </p>
<dl>

### -field <b>Encapsulation</b>

<dd>
<p>Encapsulation settings for IPv4 transmit. For more information about this member, see the
       following Remarks section.</p>
</dd>

### -field <b>IpOptionsSupported</b>

<dd>
<p>A ULONG value that a miniport driver sets to indicate that a miniport adapter can calculate an
       IP checksum for an IPv4 send packet that contains IP options or to indicate that this capability is
       enabled or disabled.</p>
</dd>

### -field <b>TcpOptionsSupported</b>

<dd>
<p>A ULONG value that a miniport driver sets to indicate that a miniport adapter can calculate a
       TCP checksum for an IPv4 send packet that contains TCP options or to indicate that this capability is
       enabled or disabled.</p>
</dd>

### -field <b>TcpChecksum</b>

<dd>
<p>A ULONG value that a miniport driver sets to indicate that a miniport adapter can calculate a
       TCP checksum for an IPv4 send packet. The TCP/IP transport sets this value to enable this capability
       or to indicate that this capability is enabled or disabled.</p>
</dd>

### -field <b>UdpChecksum</b>

<dd>
<p>A ULONG value that a miniport driver sets to indicate that a miniport adapter can calculate a
       UDP checksum for an IPv4 send packet or to indicate that this capability is enabled or
       disabled.</p>
</dd>

### -field <b>IpChecksum</b>

<dd>
<p>A ULONG value that a miniport driver sets to indicate that a miniport adapter can calculate an
       IP checksum for an IPv4 send packet or to indicate that this capability is enabled or disabled.</p>
</dd>
</dl>
</dd>

### -field <b>IPv4Receive</b>

<dd>
<p>A structure within NDIS_TCP_IP_CHECKSUM_OFFLOAD that specifies IPv4 receive information and that
     contains the following members:
     </p>
<dl>

### -field <b>Encapsulation</b>

<dd>
<p>Encapsulation settings for IPv4 receive. For more information about this member, see the
       following Remarks section.</p>
</dd>

### -field <b>IpOptionsSupported</b>

<dd>
<p>A ULONG value that a miniport driver sets to indicate that a miniport adapter can validate an IP
       checksum for an IPv4 receive packet that contains IP options or to indicate that this capability is
       enabled or disabled.</p>
</dd>

### -field <b>TcpOptionsSupported</b>

<dd>
<p>A ULONG value that a miniport driver sets to indicate that a miniport adapter can calculate a
       TCP checksum for an IPv4 receive packet that contains TCP options or to indicate that this capability
       is enabled or disabled.</p>
</dd>

### -field <b>TcpChecksum</b>

<dd>
<p>A ULONG value that a miniport driver sets to indicate that a miniport adapter can validate the
       TCP checksum for an IPv4 receive packet or to indicate that this capability is enabled or
       disabled.</p>
</dd>

### -field <b>UdpChecksum</b>

<dd>
<p>A ULONG value that a miniport driver sets to indicate that a miniport adapter can validate an
       IPv4 receive packet's UDP checksum or to indicate that this capability is enabled or disabled.</p>
</dd>

### -field <b>IpChecksum</b>

<dd>
<p>A ULONG value that a miniport driver sets to indicate that a miniport adapter can validate an IP
       checksum for an IPv4 receive packet or to indicate that this capability is enabled or disabled.</p>
</dd>
</dl>
</dd>

### -field <b>IPv6Transmit</b>

<dd>
<p>A structure within NDIS_TCP_IP_CHECKSUM_OFFLOAD that specifies IPv6 transmit information and that
     contains the following members:
     </p>
<dl>

### -field <b>Encapsulation</b>

<dd>
<p>Encapsulation settings for IPv6 transmit. For more information about this member, see the
       following Remarks section.</p>
</dd>

### -field <b>IpExtensionHeadersSupported</b>

<dd>
<p>A ULONG value that a miniport driver sets to indicate that the miniport adapter can calculate
       checksums on IPv6 packets that contain extension headers.</p>
</dd>

### -field <b>TcpOptionsSupported</b>

<dd>
<p>A ULONG value that a miniport driver sets to indicate that a miniport adapter can calculate a
       TCP checksum for an IPv6 send packet that contains TCP options or to indicate that this capability is
       enabled or disabled.</p>
</dd>

### -field <b>TcpChecksum</b>

<dd>
<p>A ULONG value that a miniport driver sets to indicate that a miniport adapter can calculate a
       TCP checksum for an IPv6 send packet or to indicate that this capability is enabled or
       disabled.</p>
</dd>

### -field <b>UdpChecksum</b>

<dd>
<p>A ULONG value that a miniport driver sets to indicate that a miniport adapter can calculate a
       UDP checksum for an IPv6 send packet or to indicate that this capability is enabled or
       disabled.</p>
</dd>
</dl>
</dd>

### -field <b>IPv6Receive</b>

<dd>
<p>A structure within NDIS_TCP_IP_CHECKSUM_OFFLOAD that specifies IPv6 receive information and that
     contains the following members:
     </p>
<dl>

### -field <b>Encapsulation</b>

<dd>
<p>Encapsulation settings for IPv6 receive. For more information about this member, see the
       following Remarks section.</p>
</dd>

### -field <b>IpExtensionHeadersSupported</b>

<dd>
<p>A ULONG value that a miniport driver sets to indicate that the miniport adapter can validate
       checksums on IPv6 packets that contain extension headers.</p>
</dd>

### -field <b>TcpOptionsSupported</b>

<dd>
<p>A ULONG value that a miniport driver sets to indicate that a miniport adapter can calculate a
       checksum for an IPv6 receive packet whose TCP header contains TCP options or to indicate that this
       capability is enabled or disabled.</p>
</dd>

### -field <b>TcpChecksum</b>

<dd>
<p>A ULONG value that a miniport driver sets to indicate that a miniport adapter can validate an
       IPv6 receive packet's TCP checksum or to indicate that this capability is enabled or disabled.</p>
</dd>

### -field <b>UdpChecksum</b>

<dd>
<p>A ULONG value that a miniport driver sets to indicate that a miniport adapter can validate a UDP
       checksum for an IPv6 receive packet or to indicate that this capability is enabled or disabled.</p>
</dd>
</dl>
</dd>
</dl>

## -remarks
<p>The NDIS_TCP_IP_CHECKSUM_OFFLOAD structure is used in the 
    <b>Checksum</b> member of the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff566599">NDIS_OFFLOAD</a> structure. The
    NDIS_TCP_IP_CHECKSUM_OFFLOAD structure specifies the current or supported services that a miniport
    adapter provides for calculating IP, TCP, or UDP checksums (or all of them) for send packets and
    validating such checksums for receive packets.</p>

<p>NDIS_OFFLOAD is used in the 
    <a href="https://msdn.microsoft.com/9ce875fc-ed3f-43e9-bfbc-081f02cb1999">
    NDIS_MINIPORT_ADAPTER_OFFLOAD_ATTRIBUTES</a> structure, 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff564832">NDIS_BIND_PARAMETERS</a> structure, 
    <a href="https://msdn.microsoft.com/d46a1e62-9d03-4ab9-86f6-81b06c04d0f6">
    NDIS_FILTER_ATTACH_PARAMETERS</a> structure, 
    <a href="netvista.oid_tcp_offload_current_config">
    OID_TCP_OFFLOAD_CURRENT_CONFIG</a> OID, and the 
    <a href="netvista.ndis_status_task_offload_current_config">
    NDIS_STATUS_TASK_OFFLOAD_CURRENT_CONFIG</a> status indication.</p>

<p>For 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff569805">OID_TCP_OFFLOAD_CURRENT_CONFIG</a>,
    the NDIS_OFFLOAD structure specifies the task offload capabilities that a miniport adapter supports. If
    the current offloads capabilities change, a miniport driver reports the new capabilities in an 
    <a href="netvista.ndis_status_task_offload_current_config">
    NDIS_STATUS_TASK_OFFLOAD_CURRENT_CONFIG</a> status indication.</p>

<p>The 
    <b>Encapsulation</b> members of NDIS_TCP_IP_CHECKSUM_OFFLOAD define the checksum offload encapsulation
    settings for the miniport adapter.</p>

<p>In response to an 
    <a href="netvista.oid_tcp_offload_current_config">
    OID_TCP_OFFLOAD_CURRENT_CONFIG</a> query request, NDIS provides a bitwise OR of the encapsulation
    flags, which indicate the supported encapsulation settings, in each of the 
    <b>Encapsulation</b> members. Miniport drivers must provide Ethernet encapsulation
    (NDIS_ENCAPSULATION_IEEE_802_3). The other types of encapsulation are optional.</p>

<p>For an 
    <a href="netvista.ndis_status_task_offload_current_config">
    NDIS_STATUS_TASK_OFFLOAD_CURRENT_CONFIG</a> status indication, the miniport driver provides a bitwise
    OR of the encapsulation flags, which indicate the current capabilities, in each of the 
    <b>Encapsulation</b> members.</p>

<p>The following flags are defined for the 
    <b>Encapsulation</b> members:</p>

<p></p><dl>
<dt><a id="NDIS_ENCAPSULATION_NOT_SUPPORTED"></a><a id="ndis_encapsulation_not_supported"></a>NDIS_ENCAPSULATION_NOT_SUPPORTED</dt>
<dd>
<p>Specifies that no encapsulation offload is supported.</p>
</dd>
<dt><a id="NDIS_ENCAPSULATION_NULL"></a><a id="ndis_encapsulation_null"></a>NDIS_ENCAPSULATION_NULL</dt>
<dd>
<p>Specifies NULL encapsulation.</p>
</dd>
<dt><a id="NDIS_ENCAPSULATION_IEEE_802_3"></a><a id="ndis_encapsulation_ieee_802_3"></a>NDIS_ENCAPSULATION_IEEE_802_3</dt>
<dd>
<p>Specifies IEEE 802.3 encapsulation.</p>
</dd>
<dt><a id="NDIS_ENCAPSULATION_IEEE_802_3_P_AND_Q"></a><a id="ndis_encapsulation_ieee_802_3_p_and_q"></a>NDIS_ENCAPSULATION_IEEE_802_3_P_AND_Q</dt>
<dd>
<p>Specifies IEEE 802.3p and IEEE 802.3q encapsulation.</p>
</dd>
<dt><a id="NDIS_ENCAPSULATION_IEEE_802_3_P_AND_Q_IN_OOB"></a><a id="ndis_encapsulation_ieee_802_3_p_and_q_in_oob"></a>NDIS_ENCAPSULATION_IEEE_802_3_P_AND_Q_IN_OOB</dt>
<dd>
<p>Specifies that IEEE 802.3p and IEEE 802.3q encapsulation settings are specified in the 
      <b>NetBufferListInfo</b> member of each 
      <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> structure.</p>
</dd>
<dt><a id="NDIS_ENCAPSULATION_IEEE_LLC_SNAP_ROUTED"></a><a id="ndis_encapsulation_ieee_llc_snap_routed"></a>NDIS_ENCAPSULATION_IEEE_LLC_SNAP_ROUTED</dt>
<dd>
<p>Specifies logical link control (LLC) encapsulation for routed protocols, as described in RFC
      1483. This flag is also used to indicate Ethernet LLC/SNAP encapsulation.</p>
</dd>
</dl><p>Specifies that no encapsulation offload is supported.</p>

<p>Specifies NULL encapsulation.</p>

<p>Specifies IEEE 802.3 encapsulation.</p>

<p>Specifies IEEE 802.3p and IEEE 802.3q encapsulation.</p>

<p>Specifies that IEEE 802.3p and IEEE 802.3q encapsulation settings are specified in the 
      <b>NetBufferListInfo</b> member of each 
      <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> structure.</p>

<p>Specifies logical link control (LLC) encapsulation for routed protocols, as described in RFC
      1483. This flag is also used to indicate Ethernet LLC/SNAP encapsulation.</p>

<p>The meaning of the values in the 
    <b>IpOptionsSupported</b>, 
    <b>TcpOptionsSupported</b>, 
    <b>IpExtensionHeadersSupported</b>, 
    <b>TcpChecksum</b>, 
    <b>UdpChecksum</b>, and 
    <b>IpChecksum</b> members of <b>NDIS_TCP_IP_CHECKSUM_OFFLOAD</b> depends on which OID or status indication
    includes the task offload structure: These members can have one of the following values:</p>

<p></p><dl>
<dt><a id="NDIS_OFFLOAD_NOT_SUPPORTED"></a><a id="ndis_offload_not_supported"></a>NDIS_OFFLOAD_NOT_SUPPORTED</dt>
<dd>
<p>In 
      <a href="netvista.oid_tcp_offload_current_config">
      OID_TCP_OFFLOAD_CURRENT_CONFIG</a>, this value specifies that the miniport adapter does not support
      the feature that the member specifies.</p>
</dd>
<dt><a id="NDIS_OFFLOAD_SUPPORTED"></a><a id="ndis_offload_supported"></a>NDIS_OFFLOAD_SUPPORTED</dt>
<dd>
<p>In <a href="https://msdn.microsoft.com/library/windows/hardware/ff569805">OID_TCP_OFFLOAD_CURRENT_CONFIG</a>, this value specifies that the miniport adapter supports the
      feature that the member specifies.</p>
</dd>
<dt><a id="NDIS_OFFLOAD_SET_OFF"></a><a id="ndis_offload_set_off"></a>NDIS_OFFLOAD_SET_OFF</dt>
<dd>
<p>In the 
      <a href="netvista.ndis_status_task_offload_current_config">
      NDIS_STATUS_TASK_OFFLOAD_CURRENT_CONFIG</a> status indication, this value specifies that the feature
      that the member specifies is disabled.</p>
</dd>
<dt><a id="NDIS_OFFLOAD_SET_ON"></a><a id="ndis_offload_set_on"></a>NDIS_OFFLOAD_SET_ON</dt>
<dd>
<p>In the <a href="https://msdn.microsoft.com/library/windows/hardware/ff567424">NDIS_STATUS_TASK_OFFLOAD_CURRENT_CONFIG</a> status indication, this value specifies that the
      feature that the member specifies is enabled.</p>
</dd>
</dl><p>In 
      <a href="netvista.oid_tcp_offload_current_config">
      OID_TCP_OFFLOAD_CURRENT_CONFIG</a>, this value specifies that the miniport adapter does not support
      the feature that the member specifies.</p>

<p>In <a href="https://msdn.microsoft.com/library/windows/hardware/ff569805">OID_TCP_OFFLOAD_CURRENT_CONFIG</a>, this value specifies that the miniport adapter supports the
      feature that the member specifies.</p>

<p>In the 
      <a href="netvista.ndis_status_task_offload_current_config">
      NDIS_STATUS_TASK_OFFLOAD_CURRENT_CONFIG</a> status indication, this value specifies that the feature
      that the member specifies is disabled.</p>

<p>In the <a href="https://msdn.microsoft.com/library/windows/hardware/ff567424">NDIS_STATUS_TASK_OFFLOAD_CURRENT_CONFIG</a> status indication, this value specifies that the
      feature that the member specifies is enabled.</p>

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
<dt>Ntddndis.h (include Ndis.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564832">NDIS_BIND_PARAMETERS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff565481">NDIS_FILTER_ATTACH_PARAMETERS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/9ce875fc-ed3f-43e9-bfbc-081f02cb1999">
   NDIS_MINIPORT_ADAPTER_OFFLOAD_ATTRIBUTES</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff566599">NDIS_OFFLOAD</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff566710">NDIS_OID_REQUEST</a>
</dt>
<dt>
<a href="netvista.ndis_status_task_offload_current_config">
   NDIS_STATUS_TASK_OFFLOAD_CURRENT_CONFIG</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff569805">OID_TCP_OFFLOAD_CURRENT_CONFIG</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NDIS_TCP_IP_CHECKSUM_OFFLOAD structure%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>