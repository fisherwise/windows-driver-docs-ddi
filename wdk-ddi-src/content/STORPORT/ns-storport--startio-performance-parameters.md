---
UID: NS.storport._STARTIO_PERFORMANCE_PARAMETERS
title: STARTIO_PERFORMANCE_PARAMETERS
author: windows-driver-content
description: The STARTIO_PERFORMANCE_PARAMETERS structure describes the performance parameters that are returned to the miniport driver by the StorPortGetStartIoPerfParams routine.
old-location: storage\startio_performance_parameters.htm
ms.assetid: 984a8584-ebdd-4e93-868b-1537a3615c1b
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: Storage
req.header: storport.h
req.include-header: Storport.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: STARTIO_PERFORMANCE_PARAMETERS
req.alt-loc: storport.h
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
ms.keywords: STARTIO_PERFORMANCE_PARAMETERS, STARTIO_PERFORMANCE_PARAMETERS, *PSTARTIO_PERFORMANCE_PARAMETERS
req.iface: 
req.product: Windows 10 or later.
---

# STARTIO_PERFORMANCE_PARAMETERS structure



## -description
<p>The <b>STARTIO_PERFORMANCE_PARAMETERS</b> structure describes the performance parameters that are returned to the miniport driver by the <a href="https://msdn.microsoft.com/library/windows/hardware/ff567099">StorPortGetStartIoPerfParams</a> routine.</p>


## -syntax

````
typedef struct _STARTIO_PERFORMANCE_PARAMETERS {
  ULONG Version;
  ULONG Size;
  ULONG MessageNumber;
  ULONG ChannelNumber;
} STARTIO_PERFORMANCE_PARAMETERS, *PSTARTIO_PERFORMANCE_PARAMETERS;
````


## -struct-fields
<dl>

### -field <b>Version</b>

<dd>
<p>The version number of the structure. This member is valid starting with Windows 8.</p>
</dd>

### -field <b>Size</b>

<dd>
<p>The size of the structure.</p>
</dd>

### -field <b>MessageNumber</b>

<dd>
<p>The offset in the device's MSI-X table for the optimal MSI-X message with which to interrupt. If the device does not support MSI-X messages, this member will be zero.</p>
</dd>

### -field <b>ChannelNumber</b>

<dd>
<p>Denotes the concurrent channel in which Storport is passing the I/O. If the miniport driver did not set up concurrent channels, this member will be zero.</p>
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
<dt>Storport.h (include Storport.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567099">StorPortGetStartIoPerfParams</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20STARTIO_PERFORMANCE_PARAMETERS structure%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>