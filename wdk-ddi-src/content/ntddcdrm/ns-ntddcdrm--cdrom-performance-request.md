---
UID: NS.ntddcdrm._CDROM_PERFORMANCE_REQUEST
title: CDROM_PERFORMANCE_REQUEST
author: windows-driver-content
description: The CDROM_PERFORMANCE_REQUEST structure is used as an input parameter to the IOCTL_CDROM_GET_PERFORMANCE I/O control request and describes the performance data requested.
old-location: storage\cdrom_performance_request.htm
ms.assetid: E43D2F2C-B5A1-4724-AEBC-F4B6A85EA846
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: Storage
req.header: ntddcdrm.h
req.include-header: Ntddcdrm.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: CDROM_PERFORMANCE_REQUEST
req.alt-loc: Ntddcdrm.h
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
ms.keywords: CDROM_PERFORMANCE_REQUEST, CDROM_PERFORMANCE_REQUEST, *PCDROM_PERFORMANCE_REQUEST
req.iface: 
---

# CDROM_PERFORMANCE_REQUEST structure



## -description
<p>The <b>CDROM_PERFORMANCE_REQUEST</b> structure is used as an input parameter to the <a href="https://msdn.microsoft.com/library/windows/hardware/gg441242">IOCTL_CDROM_GET_PERFORMANCE</a> I/O control request and describes the performance data requested.</p>


## -syntax

````
typedef struct _CDROM_PERFORMANCE_REQUEST {
  CDROM_PERFORMANCE_REQUEST_TYPE       RequestType;
  CDROM_PERFORMANCE_TYPE               PerformanceType;
  CDROM_PERFORMANCE_EXCEPTION_TYPE     Exceptions;
  CDROM_PERFORMANCE_TOLERANCE_TYPE     Tolerance;
  ULONG                                StartingLba;
} CDROM_PERFORMANCE_REQUEST, *PCDROM_PERFORMANCE_REQUEST;
````


## -struct-fields
<dl>

### -field <b>RequestType</b>

<dd>
<p>The <a href="https://msdn.microsoft.com/library/windows/hardware/gg441234">CDROM_PERFORMANCE_REQUEST_TYPE</a> enumeration specifies the request type, <b>CdromPerformanceRequest</b>, or <b>CdromWriteSpeedRequest</b>.</p>
</dd>

### -field <b>PerformanceType</b>

<dd>
<p>The <a href="https://msdn.microsoft.com/library/windows/hardware/gg441236">CDROM_PERFORMANCE_TYPE</a> enumeration specifies the type of performance data.</p>
</dd>

### -field <b>Exceptions</b>

<dd>
<p>The <a href="https://msdn.microsoft.com/library/windows/hardware/gg441231">CDROM_PERFORMANCE_EXCEPTION_TYPE</a>    enumeration specifies the type of exception. </p>
</dd>

### -field <b>Tolerance</b>

<dd>
<p>The <a href="https://msdn.microsoft.com/library/windows/hardware/gg441235">CDROM_PERFORMANCE_TOLERANCE_TYPE</a> enumeration specifies the performance tolerance for the nominal performance and the time tolerance (seek delay) for the exception list.</p>
</dd>

### -field <b>StartingLba</b>

<dd>
<p>The starting logical block address field.</p>
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
<dt>Ntddcdrm.h (include Ntddcdrm.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/gg441242">IOCTL_CDROM_GET_PERFORMANCE</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20CDROM_PERFORMANCE_REQUEST structure%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>