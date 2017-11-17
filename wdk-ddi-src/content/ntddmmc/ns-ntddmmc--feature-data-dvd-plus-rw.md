---
UID: NS.ntddmmc._FEATURE_DATA_DVD_PLUS_RW
title: FEATURE_DATA_DVD_PLUS_RW
author: windows-driver-content
description: The FEATURE_DATA_DVD_PLUS_RW structure contains information about the DVD+RW feature.
old-location: storage\feature_data_dvd_plus_rw.htm
ms.assetid: 55cbef36-dea7-4f7c-ac43-fb819b61a858
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: Storage
req.header: ntddmmc.h
req.include-header: Ntddcdrm.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FEATURE_DATA_DVD_PLUS_RW
req.alt-loc: ntddmmc.h
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
ms.keywords: FEATURE_DATA_DVD_PLUS_RW, FEATURE_DATA_DVD_PLUS_RW, *PFEATURE_DATA_DVD_PLUS_RW
req.iface: 
---

# FEATURE_DATA_DVD_PLUS_RW structure



## -description
<p>The FEATURE_DATA_DVD_PLUS_RW structure contains information about the DVD+RW feature. </p>


## -syntax

````
typedef struct _FEATURE_DATA_DVD_PLUS_RW {
  FEATURE_HEADER Header;
  UCHAR          Write  :1;
  UCHAR          Reserved1  :7;
  UCHAR          CloseOnly  :1;
  UCHAR          QuickStart  :1;
  UCHAR          Reserved02  :6;
  UCHAR          Reserved03[2];
} FEATURE_DATA_DVD_PLUS_RW, *PFEATURE_DATA_DVD_PLUS_RW;
````


## -struct-fields
<dl>

### -field <b>Header</b>

<dd>
<p>Contains a <a href="https://msdn.microsoft.com/library/windows/hardware/ff553848">FEATURE_HEADER</a> structure with header information for this feature descriptor. </p>
</dd>

### -field <b>Write</b>

<dd>
<p>Indicates, when set to 1, that the device can do background formatting of DVD+RW discs according to <i>DVD+RW 4.7 Gbytes Basic Format Specifications</i>, and can write to discs that have been formatted in this manner. </p>
</dd>

### -field <b>Reserved1</b>

<dd>
<p>Reserved. </p>
</dd>

### -field <b>CloseOnly</b>

<dd>
<p>Indicates, when set to 1, then the device supports only read compatibility stops. When set to 0, the device supports both forms of background format stop. For more information about background format stops, see the <i>SCSI Multimedia Commands - 4 (MMC-4)</i> specification published by the American National Standards Institute (ANSI).</p>
</dd>

### -field <b>QuickStart</b>

<dd></dd>

### -field <b>Reserved02</b>

<dd></dd>

### -field <b>Reserved03</b>

<dd></dd>
</dl>

## -remarks
<p>This structure holds data for the feature named "DVD+RW" by the <i>SCSI Multimedia - 4 (MMC-4) </i>specification. Devices that support this feature can read a recorded DVD+RW disc that is formatted according to the <i>DVD+RW 4.7 Gbytes Basic Format Specification. </i></p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntddmmc.h (include Ntddcdrm.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553848">FEATURE_HEADER</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553850">FEATURE_NUMBER</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20FEATURE_DATA_DVD_PLUS_RW structure%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>