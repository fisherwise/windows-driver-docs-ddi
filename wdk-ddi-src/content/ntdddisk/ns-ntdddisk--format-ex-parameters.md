---
UID: NS.ntdddisk._FORMAT_EX_PARAMETERS
title: FORMAT_EX_PARAMETERS
author: windows-driver-content
description: The FORMAT_EX_PARAMETERS structure is used in conjunction with the IOCTL_DISK_FORMAT_TRACKS_EX request to format the specified set of contiguous tracks on the disk.
old-location: storage\format_ex_parameters.htm
ms.assetid: 0c87a0b8-f355-48a4-a119-11e047e159d0
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: Storage
req.header: ntdddisk.h
req.include-header: Ntdddisk.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FORMAT_EX_PARAMETERS
req.alt-loc: ntdddisk.h
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
ms.keywords: FORMAT_EX_PARAMETERS, FORMAT_EX_PARAMETERS, *PFORMAT_EX_PARAMETERS
req.iface: 
---

# FORMAT_EX_PARAMETERS structure



## -description
<p>The FORMAT_EX_PARAMETERS structure is used in conjunction with the <a href="https://msdn.microsoft.com/library/windows/hardware/ff559448">IOCTL_DISK_FORMAT_TRACKS_EX</a> request to format the specified set of contiguous tracks on the disk. </p>


## -syntax

````
typedef struct _FORMAT_EX_PARAMETERS {
  MEDIA_TYPE MediaType;
  ULONG      StartCylinderNumber;
  ULONG      EndCylinderNumber;
  ULONG      StartHeadNumber;
  ULONG      EndHeadNumber;
  USHORT     FormatGapLength;
  USHORT     SectorsPerTrack;
  USHORT     SectorNumber[1];
} FORMAT_EX_PARAMETERS, *PFORMAT_EX_PARAMETERS;
````


## -struct-fields
<dl>

### -field <b>MediaType</b>

<dd>
<p>Indicates format information, such as the disk size and the number of bytes per sector. For a list of the values that can be assigned to this member, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff562216">MEDIA_TYPE</a>. </p>
</dd>

### -field <b>StartCylinderNumber</b>

<dd>
<p>Indicates the number of the cylinder where the formatting should begin. </p>
</dd>

### -field <b>EndCylinderNumber</b>

<dd>
<p>Indicates the number of the cylinder where the formatting should end. </p>
</dd>

### -field <b>StartHeadNumber</b>

<dd>
<p>Indicates the number of the head where the formatting should begin. </p>
</dd>

### -field <b>EndHeadNumber</b>

<dd>
<p>Indicates the number of the head where the formatting should end. </p>
</dd>

### -field <b>FormatGapLength</b>

<dd>
<p>Indicates the length in bytes of a format gap. </p>
</dd>

### -field <b>SectorsPerTrack</b>

<dd>
<p>Indicates the number of sectors per track. </p>
</dd>

### -field <b>SectorNumber</b>

<dd>
<p>Contains an array whose first element indicates the number of the sector where the formatting should begin. </p>
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
<dt>Ntdddisk.h (include Ntdddisk.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff559448">IOCTL_DISK_FORMAT_TRACKS_EX</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff559447">IOCTL_DISK_FORMAT_TRACKS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553878">FORMAT_PARAMETERS</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20FORMAT_EX_PARAMETERS structure%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>