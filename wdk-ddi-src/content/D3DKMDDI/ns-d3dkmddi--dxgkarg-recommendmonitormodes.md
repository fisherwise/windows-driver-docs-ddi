---
UID: NS.d3dkmddi._DXGKARG_RECOMMENDMONITORMODES
title: DXGKARG_RECOMMENDMONITORMODES
author: windows-driver-content
description: The DXGKARG_RECOMMENDMONITORMODES structure contains arguments for the DxgkDdiRecommendMonitorModes function.
old-location: display\dxgkarg_recommendmonitormodes.htm
ms.assetid: 283f398e-4162-4c46-847b-834f8f303052
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
req.alt-api: DXGKARG_RECOMMENDMONITORMODES
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
ms.keywords: DXGKARG_RECOMMENDMONITORMODES, DXGKARG_RECOMMENDMONITORMODES
req.iface: 
---

# DXGKARG_RECOMMENDMONITORMODES structure



## -description
<p>The DXGKARG_RECOMMENDMONITORMODES structure contains arguments for the <a href="https://msdn.microsoft.com/1fa29ab6-1faa-4be6-ae87-4cac9057471d">DxgkDdiRecommendMonitorModes</a> function. </p>


## -syntax

````
typedef struct _DXGKARG_RECOMMENDMONITORMODES {
  D3DDDI_VIDEO_PRESENT_TARGET_ID            VideoPresentTargetId;
  D3DKMDT_HMONITORSOURCEMODESET             hMonitorSourceModeSet;
  const DXGK_MONITORSOURCEMODESET_INTERFACE *pMonitorSourceModeSetInterface;
} DXGKARG_RECOMMENDMONITORMODES;
````


## -struct-fields
<dl>

### -field <b>VideoPresentTargetId</b>

<dd>
<p>An integer that identifies a video present target on the display adapter.</p>
</dd>

### -field <b>hMonitorSourceModeSet</b>

<dd>
<p>A handle to a monitor source mode set object. This set contains a list of modes that are supported by the monitor that is connected to the video present target identified by <i>VideoPresentTargetId</i>.</p>
</dd>

### -field <b>pMonitorSourceModeSetInterface</b>

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff561921">DXGK_MONITORSOURCEMODESET_INTERFACE</a> structure. The structure contains pointers to functions that the display miniport driver can use to inspect, and possibly add modes to, the monitor source mode set.</p>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561921">DXGK_MONITORSOURCEMODESET_INTERFACE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/1fa29ab6-1faa-4be6-ae87-4cac9057471d">DxgkDdiRecommendMonitorModes</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20DXGKARG_RECOMMENDMONITORMODES structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>