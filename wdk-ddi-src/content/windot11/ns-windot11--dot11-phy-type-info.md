---
UID: NS.windot11._DOT11_PHY_TYPE_INFO
title: DOT11_PHY_TYPE_INFO
author: windows-driver-content
description: Important  The Native 802.11 Wireless LAN interface is deprecated in Windows 10 and later.
old-location: netvista\dot11_phy_type_info.htm
ms.assetid: 9b0cbcc4-e38a-4266-afc5-8b2755d79f4c
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: netvista
req.header: windot11.h
req.include-header: Ndis.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating
   systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DOT11_PHY_TYPE_INFO
req.alt-loc: windot11.h
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
ms.keywords: DOT11_PHY_TYPE_INFO, DOT11_PHY_TYPE_INFO, *PDOT11_PHY_TYPE_INFO
req.iface: 
req.product: Windows 10 or later.
---

# DOT11_PHY_TYPE_INFO structure



## -description

## -syntax

````
typedef struct _DOT11_PHY_TYPE_INFO {
  union {
    DOT11_PHY_TYPE dot11PhyType;
    ULONG          uPhyId;
  };
  BOOLEAN             bUseParameters;
  ULONG               uProbeDelay;
  ULONG               uMinChannelTime;
  ULONG               uMaxChannelTime;
  CH_DESCRIPTION_TYPE ChDescriptionType;
  ULONG               uChannelListSize;
  UCHAR               ucChannelListBuffer[1];
} DOT11_PHY_TYPE_INFO, *PDOT11_PHY_TYPE_INFO;
````


## -struct-fields
<dl>

### -field <b>dot11PhyType</b>

<dd>
<p>The type of PHY that the 802.11 station will use for the scan. The PHY type is defined by the 
       <a href="https://msdn.microsoft.com/library/windows/hardware/ff548741">DOT11_PHY_TYPE</a> enumeration. 
       <div class="alert"><b>Note</b>  The miniport driver must ignore this member if it is operating in Extensible
       Station (ExtSTA) mode.</div>
<div> </div>
</p>
</dd>

### -field <b>uPhyId</b>

<dd>
<p>The identifier (ID) of the PHY that the 802.11 station will use for the scan. The PHY ID is the
       index within the list of supported PHYs returned by the driver through a query of 
       <a href="netvista.oid_dot11_supported_phy_types">
       OID_DOT11_SUPPORTED_PHY_TYPES</a>.</p>
<div class="alert"><b>Note</b>  The miniport driver must ignore this member if it is operating in ExtSTA
       mode.</div>
<div> </div>
</dd>

### -field <b>bUseParameters</b>

<dd>
<p>If this member is <b>TRUE</b>, the 802.11 station uses the other members of this structure to configure
     the PHY for the scan operation.
     </p>
<p>If this member is <b>FALSE</b>, the 802.11 station configures the PHY using its own settings for the scan
     operation.</p>
<p>
<div class="alert"><b>Note</b>  If the miniport driver is operating in ExtSTA mode, the operating system will
      always set this member to <b>FALSE</b>.</div>
<div> </div>
</p>
</dd>

### -field <b>uProbeDelay</b>

<dd>
<p>The amount of time, in microseconds, that the 802.11 station must wait before transmitting an
     802.11 Probe Request frame during active scanning.</p>
</dd>

### -field <b>uMinChannelTime</b>

<dd>
<p>The minimum amount of time, in 802.11 time units (TU), that the 802.11 station spends on each
     channel when scanning. One TU is 1024 microseconds.
     </p>
<p>This member must be greater than or equal to 
     <b>uProbeDelay</b> .</p>
</dd>

### -field <b>uMaxChannelTime</b>

<dd>
<p>The maximum amount of time, in 802.11 time units (TU), that the 802.11 station spends on each
     channel when scanning.
     </p>
<p>This member must be greater than or equal to 
     <b>uProbeDelay</b> .</p>
</dd>

### -field <b>ChDescriptionType</b>

<dd>
<p>This member specifies the method used to interpret the entries in the 
     <b>ucChannelListBuffer</b> array. The data type for this member is the CH_DESCRIPTION_TYPE enumeration,
     which declares the following values:
     </p>
<p></p>
<dl>

### -field <a id="ch_description_type_logical________"></a><a id="CH_DESCRIPTION_TYPE_LOGICAL________"></a>ch_description_type_logical
       

<dd>
<p>The channel entry is defined by a logical channel number to conform with the IEEE 802.11
       standard.</p>
</dd>

### -field <a id="ch_description_type_center_frequency________"></a><a id="CH_DESCRIPTION_TYPE_CENTER_FREQUENCY________"></a>ch_description_type_center_frequency
       

<dd>
<p>The channel entry is defined, in units of megahertz (MHz), by a channel center frequency.</p>
</dd>
</dl>
</dd>

### -field <b>uChannelListSize</b>

<dd>
<p>The length, in bytes, of the 
     <b>ucChannelListBuffer</b> array. Each entry in this array is formatted as a ULONG data type.</p>
</dd>

### -field <b>ucChannelListBuffer</b>

<dd>
<p>An array containing channel descriptions for the PHY type specified in the 
     <b>dot11PhyType</b> member.</p>
</dd>
</dl>

## -remarks
<p>The 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff548767">DOT11_SCAN_REQUEST_V2</a> structure, which
    accompanies a set request of 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff569413">OID_DOT11_SCAN_REQUEST</a>, contains an
    array of zero or more DOT11_PHY_TYPE_INFO entries.</p>

<p>For more information about the scan operations performed by a Native 802.11 miniport driver, see 
    <a href="netvista.native_802_11_scan_operations">Native 802.11 Scan
    Operations</a>.</p>

<p>For more information about the ExtSTA operation mode, see 
    <a href="netvista.extensible_station_operation_mode">Extensible Station Operation
    Mode</a>.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Available in Windows Vista and later versions of the Windows operating
   systems.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Windot11.h (include Ndis.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548767">DOT11_SCAN_REQUEST_V2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff569413">OID_DOT11_SCAN_REQUEST</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20DOT11_PHY_TYPE_INFO structure%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>