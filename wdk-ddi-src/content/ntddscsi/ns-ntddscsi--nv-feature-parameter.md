---
UID: NS.ntddscsi._NV_FEATURE_PARAMETER
title: NV_FEATURE_PARAMETER
author: windows-driver-content
description: The NV_FEATURE_PARAMETER structure is used in conjunction with the IOCTL_SCSI_MINIPORT_NVCACHE request to get NV Cache Manager feature support information from the device.
old-location: storage\nv_feature_parameter.htm
ms.assetid: 06b07b50-577c-4762-aea6-38bd1ada8973
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: Storage
req.header: ntddscsi.h
req.include-header: Ntddscsi.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NV_FEATURE_PARAMETER
req.alt-loc: ntddscsi.h
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
ms.keywords: NV_FEATURE_PARAMETER, NV_FEATURE_PARAMETER, *PNV_FEATURE_PARAMETER
req.iface: 
---

# NV_FEATURE_PARAMETER structure



## -description
<p>The NV_FEATURE_PARAMETER structure is used in conjunction with the <a href="https://msdn.microsoft.com/library/windows/hardware/ff560517">IOCTL_SCSI_MINIPORT_NVCACHE</a> request to get NV Cache Manager feature support information from the device. The NV Cache Manager feature parameters structure is returned by the miniport driver upon the successful return from the NRB_NVCACHE_INFO function, as requested in the Function field of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff563241">NVCACHE_REQUEST_BLOCK</a> structure.</p>
<p>The values in these fields come from the IDENTIFY DEVICE command in section 7.16 of the <a href="http://go.microsoft.com/fwlink/p/?linkid=74996">ATA8-ACS specification</a>.</p>


## -syntax

````
typedef struct _NV_FEATURE_PARAMETER {
  USHORT NVPowerModeEnabled;
  USHORT NVParameterReserv1;
  USHORT NVCmdEnabled;
  USHORT NVParameterReserv2;
  USHORT NVPowerModeVer;
  USHORT NVCmdVer;
  ULONG  NVSize;
  USHORT NVReadSpeed;
  USHORT NVWrtSpeed;
  ULONG  DeviceSpinUpTime;
} NV_FEATURE_PARAMETER, *PNV_FEATURE_PARAMETER;
````


## -struct-fields
<dl>

### -field <b>NVPowerModeEnabled</b>

<dd>
<p>Taken from word 214, bit 0 of the IDENTIFY DEVICE data, a value of one means the NV Cache Power Mode feature set is enabled.</p>
</dd>

### -field <b>NVParameterReserv1</b>

<dd>
<p>Reserved for future use.</p>
</dd>

### -field <b>NVCmdEnabled</b>

<dd>
<p>Taken from word 214, bit 4 of the IDENTIFY DEVICE data, a value of one means the NV Cache feature set is enabled.</p>
</dd>

### -field <b>NVParameterReserv2</b>

<dd>
<p>Reserved for future use.</p>
</dd>

### -field <b>NVPowerModeVer</b>

<dd>
<p>Taken from word 214, bits 8 through 11 of the IDENTIFY DEVICE data, this field contains the NV Cache Power Mode feature set version.</p>
</dd>

### -field <b>NVCmdVer</b>

<dd>
<p>Taken from word 214, bits 12 through 15 of the IDENTIFY DEVICE data, this field contains the NV Cache feature set version.</p>
</dd>

### -field <b>NVSize</b>

<dd>
<p>Taken from words 215 and 216 of the IDENTIFY DEVICE data, this field contains the NV Cache Size, in logical blocks.</p>
</dd>

### -field <b>NVReadSpeed</b>

<dd>
<p>Taken from word 217 of the IDENTIFY DEVICE data, this field contains the NV Cache Read Transfer Speed, in megabytes per second (MB/s).</p>
</dd>

### -field <b>NVWrtSpeed</b>

<dd>
<p>Taken from word 218 of the IDENTIFY DEVICE data, this field contains the NV Cache Write Transfer Speed, in megabytes per second (MB/s).</p>
</dd>

### -field <b>DeviceSpinUpTime</b>

<dd>
<p>Taken from word 219, bits 0 through 7 of the IDENTIFY DEVICE data, this field contains the device's estimated time to spin up, in seconds.</p>
</dd>
</dl>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntddscsi.h (include Ntddscsi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563241">NVCACHE_REQUEST_BLOCK</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20NV_FEATURE_PARAMETER structure%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>