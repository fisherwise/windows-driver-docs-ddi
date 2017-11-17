---
UID: NS.d3dkmdt._D3DKMDT_SHAREDPRIMARYSURFACEDATA
title: D3DKMDT_SHAREDPRIMARYSURFACEDATA
author: windows-driver-content
description: The D3DKMDT_SHAREDPRIMARYSURFACEDATA structure describes a shared primary surface.
old-location: display\d3dkmdt_sharedprimarysurfacedata.htm
ms.assetid: edf59add-0155-4619-9c7c-fdb63b954f85
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmdt.h
req.include-header: D3dkmddi.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3DKMDT_SHAREDPRIMARYSURFACEDATA
req.alt-loc: d3dkmdt.h
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
ms.keywords: D3DKMDT_SHAREDPRIMARYSURFACEDATA, D3DKMDT_SHAREDPRIMARYSURFACEDATA
req.iface: 
---

# D3DKMDT_SHAREDPRIMARYSURFACEDATA structure



## -description
<p>The D3DKMDT_SHAREDPRIMARYSURFACEDATA structure describes a shared primary surface.</p>


## -syntax

````
typedef struct _D3DKMDT_SHAREDPRIMARYSURFACEDATA {
  UINT                           Width;
  UINT                           Height;
  D3DDDIFORMAT                   Format;
  D3DDDI_RATIONAL                RefreshRate;
  D3DDDI_VIDEO_PRESENT_SOURCE_ID VidPnSourceId;
} D3DKMDT_SHAREDPRIMARYSURFACEDATA;
````


## -struct-fields
<dl>

### -field <b>Width</b>

<dd>
<p>[in] The width of the surface, in pixels. The driver returns the width value.</p>
</dd>

### -field <b>Height</b>

<dd>
<p>[in] The height of the surface, in pixels. The driver returns the height value.</p>
</dd>

### -field <b>Format</b>

<dd>
<p>[in] A <a href="https://msdn.microsoft.com/library/windows/hardware/ff544312">D3DDDIFORMAT</a>-typed value that indicates the pixel format of the surface. The driver returns the format value.</p>
</dd>

### -field <b>RefreshRate</b>

<dd>
<p>[in] A <a href="https://msdn.microsoft.com/library/windows/hardware/ff544641">D3DDDI_RATIONAL</a> structure that indicates the refresh rate that the shared primary surface was created with.</p>
</dd>

### -field <b>VidPnSourceId</b>

<dd>
<p>[in] The zero-based identification number of the video present source in a path of a video present network (VidPN) topology that the surface is located on. </p>
</dd>
</dl>

## -remarks
<p>Multiple processes can lock a shared primary surface. The video memory manager pins the standard allocation for the shared primary surface in video memory so the digital-to-analog converter (DAC) is guaranteed to always scan-out the appropriate data.</p>

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
<dt>D3dkmdt.h (include D3dkmddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544641">D3DDDI_RATIONAL</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544312">D3DDDIFORMAT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546589">D3DKMDT_STANDARDALLOCATION_TYPE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff557598">DXGKARG_GETSTANDARDALLOCATIONDRIVERDATA</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3DKMDT_SHAREDPRIMARYSURFACEDATA structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>