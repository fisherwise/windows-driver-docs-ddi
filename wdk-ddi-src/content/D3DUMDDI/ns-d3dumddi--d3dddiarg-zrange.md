---
UID: NS.d3dumddi._D3DDDIARG_ZRANGE
title: D3DDDIARG_ZRANGE
author: windows-driver-content
description: The D3DDDIARG_ZRANGE structure specifies z-range minimum and maximum values.
old-location: display\d3dddiarg_zrange.htm
ms.assetid: 710683e7-f628-4baa-b485-75b481812b97
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3dumddi.h
req.include-header: D3dumddi.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3DDDIARG_ZRANGE
req.alt-loc: d3dumddi.h
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
ms.keywords: D3DDDIARG_ZRANGE, D3DDDIARG_ZRANGE
req.iface: 
---

# D3DDDIARG_ZRANGE structure



## -description
<p>The D3DDDIARG_ZRANGE structure specifies z-range minimum and maximum values.</p>


## -syntax

````
typedef struct _D3DDDIARG_ZRANGE {
  FLOAT MinZ;
  FLOAT MaxZ;
} D3DDDIARG_ZRANGE;
````


## -struct-fields
<dl>

### -field <b>MinZ</b>

<dd>
<p>[in] A FLOAT value that indicates the minimum z value for the range. </p>
</dd>

### -field <b>MaxZ</b>

<dd>
<p>[in] A FLOAT value that indicates the maximum z value for the range. </p>
</dd>
</dl>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Available in Windows Vista and later versions of the Windows operating systems.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>D3dumddi.h (include D3dumddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/29ccde7c-801c-4e90-bc39-8581f262cc65">SetZRange</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3DDDIARG_ZRANGE structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>