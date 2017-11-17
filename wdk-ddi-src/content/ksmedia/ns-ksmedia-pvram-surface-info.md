---
UID: NS.ksmedia.PVRAM_SURFACE_INFO
title: PVRAM_SURFACE_INFO
author: windows-driver-content
description: The VRAM_SURFACE_INFO structure describes a region of system or display memory into which an AVStream minidriver captures audio or video data.
old-location: stream\vram_surface_info.htm
ms.assetid: 6fce78f7-a23e-4651-b6d8-b3d5387ccc27
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
req.alt-api: VRAM_SURFACE_INFO
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
ms.keywords: PVRAM_SURFACE_INFO, VRAM_SURFACE_INFO, *PVRAM_SURFACE_INFO
req.iface: 
---

# PVRAM_SURFACE_INFO structure



## -description
<p>The VRAM_SURFACE_INFO structure describes a region of system or display memory into which an AVStream minidriver captures audio or video data.</p>


## -syntax

````
typedef struct {
  UINT_PTR  hSurface;
  LONGLONG  VramPhysicalAddress;
  DWORD     cbCaptured;
  DWORD     dwWidth;
  DWORD     dwHeight;
  DWORD     dwLinearSize;
  LONG      lPitch;
  ULONGLONG ullReserved[16];
} VRAM_SURFACE_INFO, *PVRAM_SURFACE_INFO;
````


## -struct-fields
<dl>

### -field <b>hSurface</b>

<dd>
<p>A pointer to a kernel-mode handle that identifies the VRAM surface.</p>
</dd>

### -field <b>VramPhysicalAddress</b>

<dd>
<p>This member contains the physical address of the surface in display memory. The minidriver fills in this member in the handler for <a href="https://msdn.microsoft.com/library/windows/hardware/ff565177">KSPROPERTY_MAP_CAPTURE_HANDLE_TO_VRAM_ADDRESS</a>.</p>
</dd>

### -field <b>cbCaptured</b>

<dd>
<p>This member specifies the number of bytes copied into the VRAM surface. The minidriver sets this value.</p>
</dd>

### -field <b>dwWidth</b>

<dd>
<p>This member specifies the width of the video data in pixels. The minidriver sets this value.</p>
</dd>

### -field <b>dwHeight</b>

<dd>
<p>This member specifies the height of the video data, in pixels. The minidriver sets this value.</p>
</dd>

### -field <b>dwLinearSize</b>

<dd>
<p>This member specifies the linear size, in bytes, of a nonrectangular surface. The minidriver sets this value.</p>
</dd>

### -field <b>lPitch</b>

<dd>
<p>This member specifies the pitch of the surface; that is, the distance, in bytes, to the start of the next line. This is also known as the <i>stride</i> of the surface. The minidriver sets this value.</p>
</dd>

### -field <b>ullReserved</b>

<dd>
<p>The minidriver can use this member to store information about the surface as it handles a <a href="https://msdn.microsoft.com/library/windows/hardware/ff565177">KSPROPERTY_MAP_CAPTURE_HANDLE_TO_VRAM_ADDRESS</a> request. Use caution, however; this structure does not persist across <a href="https://msdn.microsoft.com/library/windows/hardware/ff556351">AVStrMiniPinProcess</a> calls.</p>
</dd>
</dl>

## -remarks
<p>When the minidriver receives VRAM_SURFACE_INFO through a <a href="https://msdn.microsoft.com/library/windows/hardware/ff565177">KSPROPERTY_MAP_CAPTURE_HANDLE_TO_VRAM_ADDRESS</a> property call, the members following <b>VramPhysicalAddress</b> in the member list (except for <b>ullReserved</b>) are zeroed out. The capture driver can store capture-related private data in these members.</p>

<p>AVStream then stores this information in the stream header and returns it to the minidriver in the <a href="https://msdn.microsoft.com/library/windows/hardware/ff556351">AVStrMiniPinProcess</a> callback function.</p>

<p>The data in these members persists for the lifetime of the stream header. When all clones are deleted or the leading edge is advanced, this data is no longer accessible.</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff556351">AVStrMiniPinProcess</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff565177">KSPROPERTY_MAP_CAPTURE_HANDLE_TO_VRAM_ADDRESS</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [stream\stream]:%20VRAM_SURFACE_INFO structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>