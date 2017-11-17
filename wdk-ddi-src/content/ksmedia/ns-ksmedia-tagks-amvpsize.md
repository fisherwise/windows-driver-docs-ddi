---
UID: NS.ksmedia.tagKS_AMVPSIZE
title: tagKS_AMVPSIZE
author: windows-driver-content
description: The KS_AMVPSIZE structure is used to describe the dimension of a video port (width by height).
old-location: stream\ks_amvpsize.htm
ms.assetid: 31430419-8f83-4f46-b398-841895f415d5
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
req.alt-api: KS_AMVPSIZE
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
ms.keywords: tagKS_AMVPSIZE, KS_AMVPSIZE, *PKS_AMVPSIZE
req.iface: 
---

# tagKS_AMVPSIZE structure



## -description
<p>The KS_AMVPSIZE structure is used to describe the dimension of a video port (width by height).</p>


## -syntax

````
typedef struct tagKS_AMVPSIZE {
  DWORD dwWidth;
  DWORD dwHeight;
} KS_AMVPSIZE, *PKS_AMVPSIZE;
````


## -struct-fields
<dl>

### -field <b>dwWidth</b>

<dd>
<p>Specifies the width of the video port, in pixels.</p>
</dd>

### -field <b>dwHeight</b>

<dd>
<p>Specifies the height of the video port, in pixels.</p>
</dd>
</dl>

## -remarks
<p>This structure is used by the <a href="https://msdn.microsoft.com/library/windows/hardware/ff566502">KSPROPERTY_VPCONFIG_SCALEFACTOR</a> property.</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff566502">KSPROPERTY_VPCONFIG_SCALEFACTOR</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [stream\stream]:%20KS_AMVPSIZE structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>