---
UID: NS.d3dkmthk._D3DKMT_DEVICE_ESCAPE
title: D3DKMT_DEVICE_ESCAPE
author: windows-driver-content
description: Do not use the D3DKMT_DEVICE_ESCAPE structure or D3DKMT_DEVICEESCAPE_TYPE enumeration. They are for testing purposes only. The D3DKMT_DEVICE_ESCAPE structure describes how to control the display device in a call to the D3DKMTEscape function.
old-location: display\d3dkmt_device_escape.htm
ms.assetid: 274bdd80-e898-42c7-8adc-8eae4e895b5f
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmthk.h
req.include-header: D3dkmthk.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3DKMT_DEVICE_ESCAPE
req.alt-loc: d3dkmthk.h
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
ms.keywords: D3DKMT_DEVICE_ESCAPE, D3DKMT_DEVICE_ESCAPE
req.iface: 
---

# D3DKMT_DEVICE_ESCAPE structure



## -description
<p>
   Do not use the D3DKMT_DEVICE_ESCAPE structure or D3DKMT_DEVICEESCAPE_TYPE enumeration. They are for testing purposes only.
   </p>
<p>The D3DKMT_DEVICE_ESCAPE structure describes how to control the display device in a call to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff546940">D3DKMTEscape</a> function.</p>


## -syntax

````
typedef struct _D3DKMT_DEVICE_ESCAPE {
  D3DKMT_DEVICEESCAPE_TYPE Type;
  union {
    struct {
      D3DKMT_HANDLE                  hPrimaryAllocation;
      D3DDDI_VIDEO_PRESENT_SOURCE_ID VidPnSourceId;
    } VidPnFromAllocation;
  };
} D3DKMT_DEVICE_ESCAPE;
````


## -struct-fields
<dl>

### -field <b>Type</b>

<dd></dd>

### -field <b>VidPnFromAllocation</b>

<dd>
<dl>

### -field <b>hPrimaryAllocation</b>

<dd>
<p>[in] The primary allocation handle.</p>
</dd>

### -field <b>VidPnSourceId</b>

<dd>
<p>[out] The VidPN source ID of the primary allocation.</p>
</dd>
</dl>
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
<dt>D3dkmthk.h (include D3dkmthk.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547970">D3DKMT_ESCAPE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546940">D3DKMTEscape</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3DKMT_DEVICE_ESCAPE structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>