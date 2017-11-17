---
UID: NS.d3dkmddi._DXGK_MONITORSOURCEMODESET_INTERFACE
title: DXGK_MONITORSOURCEMODESET_INTERFACE
author: windows-driver-content
description: The DXGK_MONITORSOURCEMODESET_INTERFACE structure contains pointers to functions that belong to the Monitor Source Mode Set interface, which is implemented by the video present network (VidPN) manager.
old-location: display\dxgk_monitorsourcemodeset_interface.htm
ms.assetid: ceab36a0-3be1-41d8-82c0-8393f93e5f42
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
req.alt-api: DXGK_MONITORSOURCEMODESET_INTERFACE
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
ms.keywords: DXGK_MONITORSOURCEMODESET_INTERFACE, DXGK_MONITORSOURCEMODESET_INTERFACE
req.iface: 
---

# DXGK_MONITORSOURCEMODESET_INTERFACE structure



## -description
<p>The DXGK_MONITORSOURCEMODESET_INTERFACE structure contains pointers to functions that belong to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff568435">Monitor Source Mode Set interface</a>, which is implemented by the video present network (VidPN) manager.</p>


## -syntax

````
typedef struct _DXGK_MONITORSOURCEMODESET_INTERFACE {
  DXGKDDI_MONITORSOURCEMODESET_GETNUMMODES              pfnGetNumModes;
  DXGKDDI_MONITORSOURCEMODESET_ACQUIREPREFERREDMODEINFO pfnAcquirePreferredModeInfo;
  DXGKDDI_MONITORSOURCEMODESET_ACQUIREFIRSTMODEINFO     pfnAcquireFirstModeInfo;
  DXGKDDI_MONITORSOURCEMODESET_ACQUIRENEXTMODEINFO      pfnAcquireNextModeInfo;
  DXGKDDI_MONITORSOURCEMODESET_CREATENEWMODEINFO        pfnCreateNewModeInfo;
  DXGKDDI_MONITORSOURCEMODESET_ADDMODE                  pfnAddMode;
  DXGKDDI_MONITORSOURCEMODESET_RELEASEMODEINFO          pfnReleaseModeInfo;
} DXGK_MONITORSOURCEMODESET_INTERFACE;
````


## -struct-fields
<dl>

### -field <b>pfnGetNumModes</b>

<dd>
<p>A pointer to the <a href="https://msdn.microsoft.com/58daf5be-45c5-493b-9d51-ef48bb123dce">pfnGetNumModes</a> function.</p>
</dd>

### -field <b>pfnAcquirePreferredModeInfo</b>

<dd>
<p>A pointer to the <a href="https://msdn.microsoft.com/80d3d199-42ad-4f21-8122-05dfad37016d">pfnAcquirePreferredModeInfo</a> function.</p>
</dd>

### -field <b>pfnAcquireFirstModeInfo</b>

<dd>
<p>A pointer to the <a href="https://msdn.microsoft.com/d448c3f4-7adb-4ceb-8c42-8cba3d2cfeae">pfnAcquireFirstModeInfo</a> function.</p>
</dd>

### -field <b>pfnAcquireNextModeInfo</b>

<dd>
<p>A pointer to the <a href="https://msdn.microsoft.com/55c629c5-1d73-40dd-a5aa-73ddcc5236b5">pfnAcquireNextModeInfo</a> function.</p>
</dd>

### -field <b>pfnCreateNewModeInfo</b>

<dd>
<p>A pointer to the <a href="https://msdn.microsoft.com/314b345c-a40b-418d-a2d8-c7b42e5fd27d">pfnCreateNewModeInfo</a> function.</p>
</dd>

### -field <b>pfnAddMode</b>

<dd>
<p>A pointer to the <a href="https://msdn.microsoft.com/88fe5a2d-d140-4ebc-846d-acea39b8bc73">pfnAddMode</a> function.</p>
</dd>

### -field <b>pfnReleaseModeInfo</b>

<dd>
<p>A pointer to the <a href="https://msdn.microsoft.com/2c82ec09-e858-4efc-a1c0-a3792e0b5ddf">pfnReleaseModeInfo</a> function.</p>
</dd>
</dl>

## -remarks
<p>The display miniport driver calls the <a href="https://msdn.microsoft.com/a64197c0-a61f-4989-9b68-4e06b1a69fd4">pfnAcquireMonitorSourceModeSet</a> function of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff568433">Monitor interface</a> to obtain a handle to a monitor source mode set object and a pointer to a DXGK_MONITORSOURCEMODESET_INTERFACE structure. The structure contains pointers to functions that the display miniport driver can call to inspect and alter the monitor source mode set object.</p>

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
<a href="https://msdn.microsoft.com/a64197c0-a61f-4989-9b68-4e06b1a69fd4">pfnAcquireMonitorSourceModeSet</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546133">D3DKMDT_MONITOR_SOURCE_MODE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562073">DXGK_VIDPNSOURCEMODESET_INTERFACE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562082">DXGK_VIDPNTARGETMODESET_INTERFACE</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20DXGK_MONITORSOURCEMODESET_INTERFACE structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>