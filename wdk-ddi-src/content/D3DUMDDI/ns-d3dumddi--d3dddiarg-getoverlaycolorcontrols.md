---
UID: NS.d3dumddi._D3DDDIARG_GETOVERLAYCOLORCONTROLS
title: D3DDDIARG_GETOVERLAYCOLORCONTROLS
author: windows-driver-content
description: The D3DDDIARG_GETOVERLAYCOLORCONTROLS structure describes the parameters for retrieving an overlay's color-control settings.
old-location: display\d3dddiarg_getoverlaycolorcontrols.htm
ms.assetid: 63d14667-7409-40c8-af03-e4ffedd73e7e
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
req.alt-api: D3DDDIARG_GETOVERLAYCOLORCONTROLS
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
ms.keywords: D3DDDIARG_GETOVERLAYCOLORCONTROLS, D3DDDIARG_GETOVERLAYCOLORCONTROLS
req.iface: 
---

# D3DDDIARG_GETOVERLAYCOLORCONTROLS structure



## -description
<p>The D3DDDIARG_GETOVERLAYCOLORCONTROLS structure describes the parameters for retrieving an overlay's color-control settings. </p>


## -syntax

````
typedef struct _D3DDDIARG_GETOVERLAYCOLORCONTROLS {
  HANDLE                      hOverlay;
  HANDLE                      hResource;
  D3DDDI_OVERLAYCOLORCONTROLS ColorControls;
} D3DDDIARG_GETOVERLAYCOLORCONTROLS;
````


## -struct-fields
<dl>

### -field <b>hOverlay</b>

<dd>
<p>[in] A handle to the overlay that <a href="https://msdn.microsoft.com/23b15bb5-4394-406b-8869-f9d1e4e2b539">GetOverlayColorControls</a> retrieves color-control settings for.</p>
</dd>

### -field <b>hResource</b>

<dd>
<p>[in] A handle to the resource that is associated with the overlay that <b>hOverlay</b> specifies.</p>
</dd>

### -field <b>ColorControls</b>

<dd>
<p>[out] A <a href="https://msdn.microsoft.com/library/windows/hardware/ff544612">D3DDDI_OVERLAYCOLORCONTROLS</a> structure that <a href="https://msdn.microsoft.com/23b15bb5-4394-406b-8869-f9d1e4e2b539">GetOverlayColorControls</a> populates with color-control settings.</p>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544612">D3DDDI_OVERLAYCOLORCONTROLS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/23b15bb5-4394-406b-8869-f9d1e4e2b539">GetOverlayColorControls</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3DDDIARG_GETOVERLAYCOLORCONTROLS structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>