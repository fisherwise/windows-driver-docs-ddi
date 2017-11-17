---
UID: NS.dxgiddi.DXGI_DDI_MODE_DESC
title: DXGI_DDI_MODE_DESC
author: windows-driver-content
description: The DXGI_DDI_MODE_DESC structure describes a display mode.
old-location: display\dxgi_ddi_mode_desc.htm
ms.assetid: 9924f914-2812-4953-85d1-9c777404418b
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: dxgiddi.h
req.include-header: D3d10umddi.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DXGI_DDI_MODE_DESC
req.alt-loc: dxgiddi.h
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
ms.keywords: DXGI_DDI_MODE_DESC, DXGI_DDI_MODE_DESC
req.iface: 
---

# DXGI_DDI_MODE_DESC structure



## -description
<p>The DXGI_DDI_MODE_DESC structure describes a display mode.</p>


## -syntax

````
typedef struct DXGI_DDI_MODE_DESC {
  UINT                         Width;
  UINT                         Height;
  DXGI_FORMAT                  Format;
  DXGI_DDI_RATIONAL            RefreshRate;
  DXGI_DDI_MODE_SCANLINE_ORDER ScanlineOrdering;
  DXGI_DDI_MODE_ROTATION       Rotation;
  DXGI_DDI_MODE_SCALING        Scaling;
} DXGI_DDI_MODE_DESC;
````


## -struct-fields
<dl>

### -field <b>Width</b>

<dd>
<p>[out] The screen width of the display mode, in pixels.</p>
</dd>

### -field <b>Height</b>

<dd>
<p>[out] The screen height of the display mode, in pixels.</p>
</dd>

### -field <b>Format</b>

<dd>
<p>[out] A DXGI_FORMAT-typed value that indicates the pixel format of the display mode.</p>
</dd>

### -field <b>RefreshRate</b>

<dd>
<p>[out] A <a href="https://msdn.microsoft.com/library/windows/hardware/ff557516">DXGI_DDI_RATIONAL</a> structure that indicates the refresh rate of the display mode.</p>
</dd>

### -field <b>ScanlineOrdering</b>

<dd>
<p>[out] A <a href="https://msdn.microsoft.com/library/windows/hardware/ff557507">DXGI_DDI_MODE_SCANLINE_ORDER</a>-typed value that indicates how scan lines are ordered in the display mode.</p>
</dd>

### -field <b>Rotation</b>

<dd>
<p>[out] A <a href="https://msdn.microsoft.com/library/windows/hardware/ff557502">DXGI_DDI_MODE_ROTATION</a>-typed value that identifies the orientation of the display mode.</p>
</dd>

### -field <b>Scaling</b>

<dd>
<p>[out] A <a href="https://msdn.microsoft.com/library/windows/hardware/ff557505">DXGI_DDI_MODE_SCALING</a>-typed value that identifies the scaling of the display mode.</p>
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
<dt>Dxgiddi.h (include D3d10umddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff557502">DXGI_DDI_MODE_ROTATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff557505">DXGI_DDI_MODE_SCALING</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff557507">DXGI_DDI_MODE_SCANLINE_ORDER</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff557511">DXGI_DDI_PRIMARY_DESC</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff557516">DXGI_DDI_RATIONAL</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20DXGI_DDI_MODE_DESC structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>