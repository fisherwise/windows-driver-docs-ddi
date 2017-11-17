---
UID: NS.ksmedia.tagKS_DATAFORMAT_VIDEOINFOHEADER
title: tagKS_DATAFORMAT_VIDEOINFOHEADER
author: windows-driver-content
description: The KS_DATAFORMAT_VIDEOINFOHEADER structure describes a video stream that does not include bob or weave settings.
old-location: stream\ks_dataformat_videoinfoheader.htm
ms.assetid: 60a04887-d696-42b2-95af-cce1c0bc102b
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: stream
req.header: ksmedia.h
req.include-header: Ksmedia.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: KS_DATAFORMAT_VIDEOINFOHEADER
req.alt-loc: ksmedia.h
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
ms.keywords: tagKS_DATAFORMAT_VIDEOINFOHEADER, KS_DATAFORMAT_VIDEOINFOHEADER, *PKS_DATAFORMAT_VIDEOINFOHEADER
req.iface: 
---

# tagKS_DATAFORMAT_VIDEOINFOHEADER structure



## -description
<p>The KS_DATAFORMAT_VIDEOINFOHEADER structure describes a video stream that does not include bob or weave settings.</p>


## -syntax

````
typedef struct tagKS_DATAFORMAT_VIDEOINFOHEADER {
  KSDATAFORMAT       DataFormat;
  KS_VIDEOINFOHEADER VideoInfoHeader;
} KS_DATAFORMAT_VIDEOINFOHEADER, *PKS_DATAFORMAT_VIDEOINFOHEADER;
````


## -struct-fields
<dl>

### -field <b>DataFormat</b>

<dd>
<p>Specifies the data format.</p>
</dd>

### -field <b>VideoInfoHeader</b>

<dd>
<p>Specifies the details of the video stream.</p>
</dd>
</dl>

## -remarks
<p>This format is used for most capture output streams.</p>

<p>Minidrivers that must specify a data format that contains settings for bob or weave must use the <a href="https://msdn.microsoft.com/library/windows/hardware/ff567335">KS_DATAFORMAT_VIDEOINFOHEADER2</a> structure.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ksmedia.h (include Ksmedia.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567335">KS_DATAFORMAT_VIDEOINFOHEADER2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561656">KSDATAFORMAT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567700">KS_VIDEOINFOHEADER</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [stream\stream]:%20KS_DATAFORMAT_VIDEOINFOHEADER structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>