---
UID: NS.d3d12umddi.D3D12DDICB_DEALLOCATE_0022
title: D3D12DDICB_DEALLOCATE_0022
author: windows-driver-content
description: Specifies values for use with a deallocation callback function.
old-location: display\d3d12ddicb_deallocate_0022.htm
ms.assetid: 977868D1-02E1-4460-9194-2079B986045E
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3d12umddi.h
req.include-header: D3d12umddi.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3D12DDICB_DEALLOCATE_0022
req.alt-loc: D3d12umddi.h
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
ms.keywords: D3D12DDICB_DEALLOCATE_0022, D3D12DDICB_DEALLOCATE_0022
req.iface: 
---

# D3D12DDICB_DEALLOCATE_0022 structure



## -description
<p>Specifies values for use with a deallocation callback function. </p>


## -syntax

````
typedef struct D3D12DDICB_DEALLOCATE_0022 {
  HANDLE                         hResource;
  UINT                           NumAllocations;
  const D3DKMT_HANDLE            *HandleList;
  D3D12DDI_DEALLOCATE_FLAGS_0022 Flags;
} D3D12DDICB_DEALLOCATE_0022;
````


## -struct-fields
<dl>

### -field <b>hResource</b>

<dd>
<p>The handle of a resource.</p>
</dd>

### -field <b>NumAllocations</b>

<dd></dd>

### -field <b>HandleList</b>

<dd>
<p>A pointer to a list of kernel handles.</p>
</dd>

### -field <b>Flags</b>

<dd>
<p>Flags to use for deallocation, as specified in the <a href="https://msdn.microsoft.com/17E3C01A-0716-4B3C-B4B3-72B055FB40EA">D3D12DDI_DEALLOCATE_FLAGS_0022</a> enumeration.</p>
</dd>
</dl>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>D3d12umddi.h (include D3d12umddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/17E3C01A-0716-4B3C-B4B3-72B055FB40EA">D3D12DDI_DEALLOCATE_FLAGS_0022</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3D12DDICB_DEALLOCATE_0022 structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>