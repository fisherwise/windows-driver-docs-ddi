---
UID: NS.nfccx._NFC_CX_RF_DISCOVERY_CONFIG
title: NFC_CX_RF_DISCOVERY_CONFIG
author: windows-driver-content
description: The NFC_CX_RF_DISCOVERY_CONFIG structure contains RF discovery configuration settings. Discovery configuration should be completed during initialization after calling NfcDxDeviceInitialize, otherwise an error is returned.
old-location: nfpdrivers\nfc_cx_rf_discovery_config.htm
ms.assetid: 4EF45183-335C-40FC-8693-BF3D17B18DF2
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: nfpdrivers
req.header: nfccx.h
req.include-header: Ncidef.h
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: None supported
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NFC_CX_RF_DISCOVERY_CONFIG
req.alt-loc: nfccx.h
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
ms.keywords: NFC_CX_RF_DISCOVERY_CONFIG, NFC_CX_RF_DISCOVERY_CONFIG, *PNFC_CX_RF_DISCOVERY_CONFIG
req.iface: 
---

# NFC_CX_RF_DISCOVERY_CONFIG structure



## -description
<p>The <b>NFC_CX_RF_DISCOVERY_CONFIG</b> structure contains RF discovery configuration settings. Discovery configuration should be completed during initialization after calling <a href="https://msdn.microsoft.com/1E1AC024-D628-4E31-80EF-8E929B8449FE">NfcDxDeviceInitialize</a>, otherwise an error is returned.</p>


## -syntax

````
typedef struct _NFC_CX_RF_DISCOVERY_CONFIG {
  ULONG  Size;
  USHORT TotalDuration;
  ULONG  PollConfig;
  UCHAR  NfcIPMode;
  UCHAR  NfcIPTgtMode;
  UCHAR  NfcCEMode;
  UCHAR  BailoutConfig;
} NFC_CX_RF_DISCOVERY_CONFIG, *PNFC_CX_RF_DISCOVERY_CONFIG;
````


## -struct-fields
<dl>

### -field <b>Size</b>

<dd>
<p> Size of this structure in bytes.</p>
</dd>

### -field <b>TotalDuration</b>

<dd>
<p> Total duration of the single discovery period in milliseconds. Default is 300 milliseconds.</p>
<p>This member corresponds to TOTAL_DURATION specified in the NCI specification. Values can be between 0 to 0xFFFF.  Use an appropriate value that factors into account both the discovery latency as well as power consumption.</p>
</dd>

### -field <b>PollConfig</b>

<dd>
<p>Combination of <a href="https://msdn.microsoft.com/library/windows/hardware/dn905560">NFC_CX_POLL_MODE_CONFIG</a> values. </p>
<p>This member enables configuration of poll mode settings. The default enables polling for passive poll NFC-A, passive poll NFC-B, and passive poll NFC-F (212 and 424k). Its recommended that NFC clients configure additional active modes if they are supported.</p>
</dd>

### -field <b>NfcIPMode</b>

<dd>
<p> Combination of <a href="https://msdn.microsoft.com/library/windows/hardware/dn905547">NFC_CX_NFCIP_MODE_CONFIG</a> values.</p>
<p>This member enables configuration of NFC-IP initiator mode settings. The value corresponds to combination of NFC_CX_NFCIP_MODE_CONFIG enum. The default enables polling for passive poll NFC-A and passive poll NFC-F (212 and 424k) phases.</p>
</dd>

### -field <b>NfcIPTgtMode</b>

<dd>
<p> Combination of <a href="https://msdn.microsoft.com/library/windows/hardware/dn905548">NFC_CX_NFCIP_TGT_MODE_CONFIG</a> values.</p>
<p>This member enables configuration of NFC-IP target mode settings. The default enables passive listen NFC-A and passive listen NFC-F phases.</p>
</dd>

### -field <b>NfcCEMode</b>

<dd>
<p> Combination of <a href="https://msdn.microsoft.com/library/windows/hardware/dn905539">NFC_CX_CE_MODE_CONFIG</a> values. </p>
<p>This member enables configuration of NFC-CE mode settings. The default enables passive listen NFC-A, passive listen NFC-B, and passive listen NFC-F phases.</p>
</dd>

### -field <b>BailoutConfig</b>

<dd>
<p>Combination of <a href="https://msdn.microsoft.com/library/windows/hardware/dn905549">NFC_CX_POLL_BAILOUT_CONFIG</a> values. Default is disabled.</p>
<p>This member enables configuration of PA_BAIL_OUT and PB_BAIL_OUT as described in the NCI specification. </p>
</dd>
</dl>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 10</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>None supported</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Nfccx.h (include Ncidef.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt><a href="http://go.microsoft.com/fwlink/p/?LinkID=785320">Near field communication (NFC) design guide</a></dt>
<dt><a href="https://msdn.microsoft.com/windows/hardware/drivers/nfc/nfc-class-extension-">NFC class extension design guide</a></dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [nfpdrivers\nfpdrivers]:%20NFC_CX_RF_DISCOVERY_CONFIG structure%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>