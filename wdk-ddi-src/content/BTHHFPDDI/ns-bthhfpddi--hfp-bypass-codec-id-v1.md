---
UID: NS.bthhfpddi._HFP_BYPASS_CODEC_ID_V1
title: HFP_BYPASS_CODEC_ID_V1
author: windows-driver-content
description: The HFP_BYPASS_CODEC_ID_V1 structure defines version 1 of the supported codec ID structure.
old-location: audio\hfp_bypass_codec_id_v1.htm
ms.assetid: FB618271-A1E9-4F47-97DC-F4ACAA01028C
ms.author: windowsdriverdev
ms.date: 10/30/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: audio
req.header: bthhfpddi.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: HFP_BYPASS_CODEC_ID_V1
req.alt-loc: Bthhfpddi.h
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
ms.keywords: HFP_BYPASS_CODEC_ID_V1, HFP_BYPASS_CODEC_ID_V1, *PHFP_BYPASS_CODEC_ID_V1
req.iface: 
---

# HFP_BYPASS_CODEC_ID_V1 structure



## -description
<p>The HFP_BYPASS_CODEC_ID_V1 structure defines version 1 of the supported codec ID structure.</p>


## -syntax

````
typedef struct _HFP_BYPASS_CODEC_ID_V1 {
  UCHAR CodecId;
} HFP_BYPASS_CODEC_ID_V1, *PHFP_BYPASS_CODEC_ID_V1;
````


## -struct-fields
<dl>

### -field <b>CodecId</b>

<dd>
<p>The codec ID can be any of the values in the following table.</p>
<table>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
<tr>
<td>0</td>
<td>Undefined codec</td>
</tr>
<tr>
<td>1</td>
<td>CVSD codec (narrow band) </td>
</tr>
<tr>
<td>2</td>
<td>mSBC codec (wide band speech)</td>
</tr>
</table>
<p> </p>
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
<p>Windows Server 2016</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Bthhfpddi.h</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/dn798964">HFP_BYPASS_CODEC_ID_VERSION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/dn798965">IOCTL_BTHHFP_DEVICE_GET_CODEC_ID</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [audio\audio]:%20HFP_BYPASS_CODEC_ID_V1 structure%20 RELEASE:%20(10/30/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>