---
UID: NE.d3dkmdt._D3DKMDT_MODE_PREFERENCE
title: D3DKMDT_MODE_PREFERENCE
author: windows-driver-content
description: The D3DKMDT_MODE_PREFERENCE enumeration is used to indicate whether a particular mode is one of the modes preferred by the monitor connected to a given video present target.
old-location: display\d3dkmdt_mode_preference.htm
ms.assetid: 5d18431d-ca35-4757-8bbe-9397abd31568
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmdt.h
req.include-header: D3dkmdt.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3DKMDT_MODE_PREFERENCE
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
req.irql: PASSIVE_LEVEL
ms.keywords: DXGK_CHECK_MULTIPLANE_OVERLAY_SUPPORT_RETURN_INFO, DXGK_CHECK_MULTIPLANE_OVERLAY_SUPPORT_RETURN_INFO
req.iface: 
---

# D3DKMDT_MODE_PREFERENCE enumeration



## -description
<p>The D3DKMDT_MODE_PREFERENCE enumeration is used to indicate whether a particular mode is one of the modes preferred by the monitor connected to a given video present target.</p>


## -syntax

````
typedef enum _D3DKMDT_MODE_PREFERENCE { 
  D3DKMDT_MP_UNINITIALIZED  = 0,
  D3DKMDT_MP_PREFERRED      = 1,
  D3DKMDT_MP_NOTPREFERRED   = 2
} D3DKMDT_MODE_PREFERENCE;
````


## -enum-fields
<dl>

### -field <a id="D3DKMDT_MP_UNINITIALIZED"></a><a id="d3dkmdt_mp_uninitialized"></a><b>D3DKMDT_MP_UNINITIALIZED</b>

<dd>
<p>Indicates that a variable of type D3DKMDT_MODE_PREFERENCE has not yet been assigned a meaningful value.</p>
</dd>

### -field <a id="D3DKMDT_MP_PREFERRED"></a><a id="d3dkmdt_mp_preferred"></a><b>D3DKMDT_MP_PREFERRED</b>

<dd>
<p>Indicates that the mode is preferred by the monitor.</p>
</dd>

### -field <a id="D3DKMDT_MP_NOTPREFERRED"></a><a id="d3dkmdt_mp_notpreferred"></a><b>D3DKMDT_MP_NOTPREFERRED</b>

<dd>
<p>Indicates that the mode is not preferred by the monitor.</p>
</dd>
</dl>

## -remarks
<p>The <b>Info</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff546133">D3DKMDT_MONITOR_SOURCE_MODE</a> structure and the <b>SignalInfo</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff546729">D3DKMDT_VIDPN_TARGET_MODE</a> structure are <a href="https://msdn.microsoft.com/38d0a655-265b-46e0-8af3-de6757025588">D3DKMDT_VIDEO_SIGNAL_MODE</a> structures. The <b>ModePreference</b> member of the D3DKMDT_VIDEO_SIGNAL_MODE structure is a D3DKMDT_MODE_PREFERENCE value.</p>

<p>The <b>Info</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff546133">D3DKMDT_MONITOR_SOURCE_MODE</a> structure and the <b>SignalInfo</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff546729">D3DKMDT_VIDPN_TARGET_MODE</a> structure are <a href="https://msdn.microsoft.com/38d0a655-265b-46e0-8af3-de6757025588">D3DKMDT_VIDEO_SIGNAL_MODE</a> structures. The <b>ModePreference</b> member of the D3DKMDT_VIDEO_SIGNAL_MODE structure is a D3DKMDT_MODE_PREFERENCE value.</p>

<p>The <b>Info</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff546133">D3DKMDT_MONITOR_SOURCE_MODE</a> structure and the <b>SignalInfo</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff546729">D3DKMDT_VIDPN_TARGET_MODE</a> structure are <a href="https://msdn.microsoft.com/38d0a655-265b-46e0-8af3-de6757025588">D3DKMDT_VIDEO_SIGNAL_MODE</a> structures. The <b>ModePreference</b> member of the D3DKMDT_VIDEO_SIGNAL_MODE structure is a D3DKMDT_MODE_PREFERENCE value.</p>

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
<dt>D3dkmdt.h (include D3dkmdt.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/6dda82bd-1a43-4ffe-b398-a9f8cee6d1c1">DxgkDdiEnumVidPnCofuncModality</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3DKMDT_MODE_PREFERENCE enumeration%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>