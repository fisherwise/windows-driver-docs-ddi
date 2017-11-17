---
UID: NS.mfapi.tagHistogramHeader
title: tagHistogramHeader
author: windows-driver-content
description: The HistogramHeader structure describes the blob format for MF_CAPTURE_METADATA_HISTOGRAM.
old-location: stream\histogramheader.htm
ms.assetid: C41EC25A-98EF-4C35-9E5A-954C80B29DA6
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: stream
req.header: mfapi.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: HistogramHeader
req.alt-loc: mfapi.h
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
ms.keywords: tagHistogramHeader, HistogramHeader
req.iface: 
---

# tagHistogramHeader structure



## -description
<p>The <b>HistogramHeader</b>  structure describes the blob format for <b>MF_CAPTURE_METADATA_HISTOGRAM</b>.</p>


## -syntax

````
typedef struct tagHistogramHeader {
  ULONG         Size;
  ULONG         Bins;
  ULONG         FourCC;
  ULONG         ChannelMasks;
  HistogramGrid Grid;
} HistogramHeader;
````


## -struct-fields
<dl>

### -field <b>Size</b>

<dd>
<p>Size of this header + (<a href="https://msdn.microsoft.com/library/windows/hardware/dn927647">HistogramDataHeader</a> + histogram data following) * number of channels available.</p>
</dd>

### -field <b>Bins</b>

<dd>
<p>Number of bins in the histogram.</p>
</dd>

### -field <b>FourCC</b>

<dd>
<p>Color space that the histogram is collected from</p>
</dd>

### -field <b>ChannelMasks</b>

<dd>
<p>Masks of the color channels that the histogram is collected for.</p>
</dd>

### -field <b>Grid</b>

<dd>
<p>Grid that the histogram is collected from.</p>
</dd>
</dl>

## -remarks
<p>The <b>MF_CAPTURE_METADATA_HISTOGRAM</b> attribute contains a  histogram when a preview frame is captured.</p>

<p>For the <b>ChannelMasks</b> field, the following bitmasks indicate the available channels in the histogram:</p>

<p>Each blob can contain multiple histograms collected from different regions or different color spaces of the same frame. Each histogram in the blob is identified by its own <b>HistogramHeader</b>. Each histogram has its own region and sensor output size associated. For full frame histogram, the region will match the sensor output size specified in <a href="https://msdn.microsoft.com/library/windows/hardware/dn927648">HistogramGrid</a>.</p>

<p>Histogram data for all available channels are grouped under one histogram. Histogram data for each channel is identified by a <a href="https://msdn.microsoft.com/library/windows/hardware/dn927647">HistogramDataHeader</a> immediate above the data. <b>ChannelMasks</b> indicate how many and what channels are having the histogram data, which is the bitwise OR of the supported <b>MF_HISTOGRAM_CHANNEL_*</b> bitmasks as defined above. <b>ChannelMask</b> indicates what channel the data is for, which is identified by any one of the <b>MF_HISTOGRAM_CHANNEL_*</b> bitmasks.</p>

<p>Histogram data is an array of <b>ULONG</b> with each entry representing the number of pixels falling under a set of tonal values as categorized by the bin.  The data in the array should start from bin 0 to bin N-1, where N is the number of bins in the histogram, for example, <b>HistogramBlobHeader.Bins</b>.</p>

<p>For Windows 10, if <a href="https://msdn.microsoft.com/library/windows/hardware/dn917945">KSPROPERTY_CAMERACONTROL_EXTENDED_HISTOGRAM</a> is supported, at minimum a full frame histogram with Y channel must be provided which should be the first histogram in the histogram blob.
Note that <a href="https://msdn.microsoft.com/library/windows/hardware/dn927646">HistogramBlobHeader</a>, <b>HistogramHeader</b>, <a href="https://msdn.microsoft.com/library/windows/hardware/dn927647">HistogramDataHeader</a> and Histogram data only describe the blob format for the <b>MF_CAPTURE_METADATA_HISTOGRAM</b> attribute.  The metadata item structure for the histogram (<a href="https://msdn.microsoft.com/library/windows/hardware/dn925184">KSCAMERA_METADATA_ITEMHEADER</a> + all histogram metadata payload) is up to driver and must be 8-byte aligned.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Mfapi.h</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/dn927646">HistogramBlobHeader</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/dn927647">HistogramDataHeader</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/dn927648">HistogramGrid</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [stream\stream]:%20HistogramHeader structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>