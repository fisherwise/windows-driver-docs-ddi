---
UID: NS.wwan._WWAN_TDSCDMA_MRL_INFO
title: WWAN_TDSCDMA_MRL_INFO
author: windows-driver-content
description: The WWAN_TDSCDMA_MRL_INFO structure represents information about a neighboring TDSCDMA cell.
old-location: netvista\wwan_tdscdma_mrl_info.htm
ms.assetid: 4EA0AE24-E4B0-49E0-8C50-44F6890C5C52
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: netvista
req.header: wwan.h
req.include-header: Wwan.h
req.target-type: Windows
req.target-min-winverclnt: Windows 10, version 1709
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: WWAN_TDSCDMA_MRL_INFO
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
ms.keywords: WWAN_TDSCDMA_MRL_INFO, WWAN_TDSCDMA_MRL_INFO, *PWWAN_TDSCDMA_MRL_INFO
req.iface: 
req.product: Windows 10 or later.
---

# WWAN_TDSCDMA_MRL_INFO structure



## -description
<p>The <b>WWAN_TDSCDMA_MRL_INFO</b> structure represents information about a neighboring TDSCDMA cell.</p>


## -syntax

````
typedef struct _WWAN_TDSCDMA_MRL_INFO {
  ULONG ProviderIdOffset;
  ULONG ProviderIdSize;
  ULONG LocationAreaCode;
  ULONG CellId;
  ULONG UARFCN;
  ULONG CellParameterID;
  ULONG TimingAdvance;
  ULONG RSCP;
  ULONG PathLoss;
  BYTE  Data[ANYSIZE_ARRAY];
} WWAN_TDSCDMA_MRL_INFO, *PWWAN_TDSCDMA_MRL_INFO;
````


## -struct-fields
<dl>

### -field <b>ProviderIdOffset</b>

<dd>
<p>The offset in bytes, calculated from the beginning of this structure, to a numeric (0-9) string called <i>ProviderId</i> that represents the network provider identity. This string is a concatenation of a three-digit Mobile Country Code (MCC) and a two or three-digit Mobile Network Code (MNC). This member can be NULL when no <i>ProviderId</i> information is returned.</p>
</dd>

### -field <b>ProviderIdSize</b>

<dd>
<p>The size, in bytes, used for <i>ProviderId</i>.</p>
</dd>

### -field <b>LocationAreaCode</b>

<dd>
<p>The Location Area Code (0-65535). Use 0xFFFFFFFF when this information is not available.</p>
</dd>

### -field <b>CellId</b>

<dd>
<p>The Cell ID (0-268435455). Use 0xFFFFFFFF when this information is not available.</p>
</dd>

### -field <b>UARFCN</b>

<dd>
<p>The UTRA Absolute Radio Frequency Channel Number for the serving cell (0-16383). Use 0xFFFFFFFF when this information is not available.</p>
</dd>

### -field <b>CellParameterID</b>

<dd>
<p>The Cell Parameter ID (0-127). Use 0xFFFFFFFF when this information is not available.</p>
</dd>

### -field <b>TimingAdvance</b>

<dd>
<p>The Timing Advance (0-1023). This member is the same value for all timeslots. Use 0xFFFFFFFF when this information is not available.</p>
</dd>

### -field <b>RSCP</b>

<dd>
<p>The Received Signal Code Power of the serving cell. The range is -120 to -25, in units of 1dBm in Q8 L3 filtered. Use 0xFFFFFFFF when this information is not available.</p>
</dd>

### -field <b>PathLoss</b>

<dd>
<p>The path loss of the serving cell (46-158). Use 0xFFFFFFFF when this information is not available.</p>
</dd>

### -field <b>Data[ANYSIZE_ARRAY]</b>

<dd>
<p>The data buffer containing <i>ProviderId</i>.</p>
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
<p>Windows 10, version 1709</p>
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
<a href="https://msdn.microsoft.com/66460B28-C2B4-4F05-A133-31A753AF9489">WWAN_BASE_STATIONS_INFO</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/D919EF5E-502C-4983-AFC5-F3F6E6CC8C3B">WWAN_TDSCDMA_MRL</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/5D0DD219-8D81-4F72-B327-119A45CC35B4">WWAN_TDSCDMA_SERVING_CELL_INFO</a>
</dt>
<dt>
<a href="https://docs.microsoft.com/windows-hardware/drivers/network/mb-base-stations-information-query-support">MB base stations information query support</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20WWAN_TDSCDMA_MRL_INFO structure%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>