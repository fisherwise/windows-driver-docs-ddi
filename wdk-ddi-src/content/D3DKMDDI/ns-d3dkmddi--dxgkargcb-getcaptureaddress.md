---
UID: NS.d3dkmddi._DXGKARGCB_GETCAPTUREADDRESS
title: DXGKARGCB_GETCAPTUREADDRESS
author: windows-driver-content
description: The DXGKARGCB_GETCAPTUREADDRESS structure describes parameters for retrieving information about a capture buffer that is associated with an allocation.
old-location: display\dxgkargcb_getcaptureaddress.htm
ms.assetid: 95f1bbf4-06d8-48b7-a983-bf0b65ec2da3
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
req.alt-api: DXGKARGCB_GETCAPTUREADDRESS
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
ms.keywords: DXGKARGCB_GETCAPTUREADDRESS, DXGKARGCB_GETCAPTUREADDRESS
req.iface: 
---

# DXGKARGCB_GETCAPTUREADDRESS structure



## -description
<p>The DXGKARGCB_GETCAPTUREADDRESS structure describes parameters for retrieving information about a capture buffer that is associated with an allocation.</p>


## -syntax

````
typedef struct _DXGKARGCB_GETCAPTUREADDRESS {
  D3DKMT_HANDLE    hAllocation;
  UINT             SegmentId;
  PHYSICAL_ADDRESS PhysicalAddress;
} DXGKARGCB_GETCAPTUREADDRESS;
````


## -struct-fields
<dl>

### -field <b>hAllocation</b>

<dd>
<p>[in] A handle to the allocation that is associated with the capture buffer to retrieve information on. </p>
</dd>

### -field <b>SegmentId</b>

<dd>
<p>[out] The identifier of the segment for the capture buffer. The allocation that is associated with the capture buffer is currently paged in this segment.</p>
</dd>

### -field <b>PhysicalAddress</b>

<dd>
<p>[out] The physical address of the capture buffer.</p>
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
<a href="https://msdn.microsoft.com/f87a5a5f-20d3-48cb-93f0-114eafe7238b">DxgkCbGetCaptureAddress</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20DXGKARGCB_GETCAPTUREADDRESS structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>