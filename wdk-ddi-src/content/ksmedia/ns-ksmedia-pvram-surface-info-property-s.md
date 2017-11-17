---
UID: NS.ksmedia.PVRAM_SURFACE_INFO_PROPERTY_S
title: PVRAM_SURFACE_INFO_PROPERTY_S
author: windows-driver-content
description: The VRAM_SURFACE_INFO_PROPERTY_S structure describes property items in the KSPROPSETID_VramCapture property set.
old-location: stream\vram_surface_info_property_s.htm
ms.assetid: 9bb24ca3-2684-4873-8136-c560f3374310
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
req.alt-api: VRAM_SURFACE_INFO_PROPERTY_S
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
ms.keywords: PVRAM_SURFACE_INFO_PROPERTY_S, VRAM_SURFACE_INFO_PROPERTY_S, *PVRAM_SURFACE_INFO_PROPERTY_S
req.iface: 
---

# PVRAM_SURFACE_INFO_PROPERTY_S structure



## -description
<p>The VRAM_SURFACE_INFO_PROPERTY_S structure describes property items in the KSPROPSETID_VramCapture property set.</p>


## -syntax

````
typedef struct {
  KSPROPERTY         Property;
  PVRAM_SURFACE_INFO pVramSurfaceInfo;
} VRAM_SURFACE_INFO_PROPERTY_S, *PVRAM_SURFACE_INFO_PROPERTY_S;
````


## -struct-fields
<dl>

### -field <b>Property</b>

<dd>
<p>This member specifies an initialized <a href="https://msdn.microsoft.com/library/windows/hardware/ff564262">KSPROPERTY</a> structure that describes the property set, property ID, and request type.</p>
</dd>

### -field <b>pVramSurfaceInfo</b>

<dd>
<p>This member specifies a pointer to a structure of type <a href="https://msdn.microsoft.com/library/windows/hardware/ff568783">VRAM_SURFACE_INFO</a>.</p>
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
<dt>Ksmedia.h (include Ksmedia.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564262">KSPROPERTY</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff568783">VRAM_SURFACE_INFO</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [stream\stream]:%20VRAM_SURFACE_INFO_PROPERTY_S structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>