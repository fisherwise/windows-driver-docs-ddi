---
UID: NS.ntddstor._DEVICE_SEEK_PENALTY_DESCRIPTOR
title: DEVICE_SEEK_PENALTY_DESCRIPTOR
author: windows-driver-content
description: The DEVICE_SEEK_PENALTY_DESCRIPTOR structure is used in conjunction with the IOCTL_STORAGE_QUERY_PROPERTY request to retrieve the seek penalty descriptor data for a device.
old-location: storage\device_seek_penalty_descriptor.htm
ms.assetid: c12b66a4-fdb5-40d3-a767-c15477391179
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: Storage
req.header: ntddstor.h
req.include-header: Ntddstor.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DEVICE_SEEK_PENALTY_DESCRIPTOR
req.alt-loc: ntddstor.h
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
ms.keywords: DEVICE_SEEK_PENALTY_DESCRIPTOR, DEVICE_SEEK_PENALTY_DESCRIPTOR, *PDEVICE_SEEK_PENALTY_DESCRIPTOR
req.iface: 
---

# DEVICE_SEEK_PENALTY_DESCRIPTOR structure



## -description
<p>The DEVICE_SEEK_PENALTY_DESCRIPTOR structure is used in conjunction with the <a href="https://msdn.microsoft.com/library/windows/hardware/ff560590">IOCTL_STORAGE_QUERY_PROPERTY</a> request to retrieve the seek penalty descriptor data for a device.</p>


## -syntax

````
typedef struct _DEVICE_SEEK_PENALTY_DESCRIPTOR {
  ULONG   Version;
  ULONG   Size;
  BOOLEAN IncursSeekPenalty;
} DEVICE_SEEK_PENALTY_DESCRIPTOR, *PDEVICE_SEEK_PENALTY_DESCRIPTOR;
````


## -struct-fields
<dl>

### -field <b>Version</b>

<dd>
<p>Contains the size of the structure DEVICE_SEEK_PENALTY_DESCRIPTOR. The value of this member will change as members are added to the structure.</p>
</dd>

### -field <b>Size</b>

<dd>
<p>Specifies the total size of the descriptor, in bytes.</p>
</dd>

### -field <b>IncursSeekPenalty</b>

<dd>
<p>Specifies whether the device incurs a seek penalty.</p>
</dd>
</dl>

## -remarks
<p>Storage class drivers issue a device-control request with the I/O control code  <a href="https://msdn.microsoft.com/library/windows/hardware/ff560590">IOCTL_STORAGE_QUERY_PROPERTY</a> to retrieve this structure, which contains seek penalty information for data transfer operations. The structure can be retrieved either from the device object for the bus or from an FDO, which forwards the request to the underlying bus.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntddstor.h (include Ntddstor.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff560590">IOCTL_STORAGE_QUERY_PROPERTY</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20DEVICE_SEEK_PENALTY_DESCRIPTOR structure%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>