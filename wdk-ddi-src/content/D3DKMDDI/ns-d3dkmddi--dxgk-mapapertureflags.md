---
UID: NS.d3dkmddi._DXGK_MAPAPERTUREFLAGS
title: DXGK_MAPAPERTUREFLAGS
author: windows-driver-content
description: The DXGK_MAPAPERTUREFLAGS structure identifies the type of map-aperture-segment operation to set up in a call to the DxgkDdiBuildPagingBuffer function.
old-location: display\dxgk_mapapertureflags.htm
ms.assetid: c6a6f98f-a4e3-47ed-b9e9-7303c824612d
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmddi.h
req.include-header: D3dkmddi.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DXGK_MAPAPERTUREFLAGS
req.alt-loc: d3dkmddi.h
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
ms.keywords: DXGK_MAPAPERTUREFLAGS, DXGK_MAPAPERTUREFLAGS
req.iface: 
---

# DXGK_MAPAPERTUREFLAGS structure



## -description
<p>The DXGK_MAPAPERTUREFLAGS structure identifies the type of map-aperture-segment operation to set up in a call to the <a href="https://msdn.microsoft.com/d315ff53-4a9f-46a3-ad74-d65a5eb72de1">DxgkDdiBuildPagingBuffer</a> function. </p>


## -syntax

````
typedef struct _DXGK_MAPAPERTUREFLAGS {
  union {
    struct {
      UINT CacheCoherent  :1;
      UINT Reserved  :31;
    };
    UINT Value;
  };
} DXGK_MAPAPERTUREFLAGS;
````


## -struct-fields
<dl>

### -field <b>CacheCoherent</b>

<dd>
<p>[in] A UINT value that specifies whether cache coherency is required for pages that are mapped in a call to <a href="https://msdn.microsoft.com/d315ff53-4a9f-46a3-ad74-d65a5eb72de1">DxgkDdiBuildPagingBuffer</a>. If this member is set, the driver must ensure that cache coherency is enforced on the pages that are mapped. If this member is not set, cache coherency is not required for the pages that are mapped. </p>
<p>Setting this member is equivalent to setting the first bit of the 32-bit <b>Value</b> member (0x00000001).</p>
</dd>

### -field <b>Reserved</b>

<dd>
<p>[in] This member is reserved and should be set to zero. Setting this member to zero is equivalent to setting the remaining 31 bits (0xFFFFFFFE) of the 32-bit <b>Value</b> member to zeros.</p>
</dd>

### -field <b>Value</b>

<dd>
<p>[in] A member in the union that DXGK_MAPAPERTUREFLAGS contains that can hold a 32-bit value that identifies the type of map-aperture-segment-operation.</p>
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
<dt>D3dkmddi.h (include D3dkmddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff557540">DXGKARG_BUILDPAGINGBUFFER</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/d315ff53-4a9f-46a3-ad74-d65a5eb72de1">DxgkDdiBuildPagingBuffer</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20DXGK_MAPAPERTUREFLAGS structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>