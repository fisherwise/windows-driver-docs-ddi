---
UID: NS.mfapi.tagHistogramBlobHeader
title: tagHistogramBlobHeader
author: windows-driver-content
description: The HistogramBlobHeader structure describes the blob size and the number of histograms in the blob for the MF_CAPTURE_METADATA_HISTOGRAM attribute.
old-location: stream\histogramblobheader.htm
ms.assetid: E72DEFAB-1176-47AA-B6FC-35346D63CBD9
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
req.alt-api: HistogramBlobHeader
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
ms.keywords: tagHistogramBlobHeader, HistogramBlobHeader
req.iface: 
---

# tagHistogramBlobHeader structure



## -description
<p>The <b>HistogramBlobHeader</b> structure describes the blob size and the number of histograms in the blob for the <b>MF_CAPTURE_METADATA_HISTOGRAM</b> attribute.</p>


## -syntax

````
typedef struct tagHistogramBlobHeader {
  ULONG Size;
  ULONG Histograms;
} HistogramBlobHeader;
````


## -struct-fields
<dl>

### -field <b>Size</b>

<dd>
<p>Size of the entire histogram blob in bytes.</p>
</dd>

### -field <b>Histograms</b>

<dd>
<p>Number of histograms in the blob. Each histogram is identified by a <a href="https://msdn.microsoft.com/library/windows/hardware/dn927649">HistogramHeader</a>.</p>
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
<dt>Mfapi.h</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/dn927647">HistogramDataHeader</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/dn927648">HistogramGrid</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [stream\stream]:%20HistogramBlobHeader structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>