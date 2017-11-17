---
UID: NS.d3dumddi.D3DDDIARG_UPDATESUBRESOURCEUP
title: D3DDDIARG_UPDATESUBRESOURCEUP
author: windows-driver-content
description: Describes info that's used to update a destination subresource region from a source system-memory region. Used by Windows Display Driver Model (WDDM) 1.3 and later user-mode display drivers.
old-location: display\d3dddiarg_updatesubresourceup.htm
ms.assetid: 27BE493F-8F70-4FBF-AA58-D6ACB27BFC2D
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3dumddi.h
req.include-header: D3d10umddi.h
req.target-type: Windows
req.target-min-winverclnt: Windows 8.1
req.target-min-winversvr: Windows Server 2012 R2
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3DDDIARG_UPDATESUBRESOURCEUP
req.alt-loc: D3dumddi.h
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
ms.keywords: D3DDDIARG_UPDATESUBRESOURCEUP, D3DDDIARG_UPDATESUBRESOURCEUP
req.iface: 
---

# D3DDDIARG_UPDATESUBRESOURCEUP structure



## -description
<p>Describes info that's used to update a destination subresource region from a source system-memory region. Used by Windows Display Driver Model (WDDM) 1.3 and later user-mode display drivers.</p>


## -syntax

````
typedef struct D3DDDIARG_UPDATESUBRESOURCEUP {
  HANDLE              hResource;
  UINT                SubResourceIndex;
  D3DDDIBOX           DstBox;
  const VOID          *pSysMemUP;
  UINT                RowPitch;
  UINT                DepthPitch;
  D3DDDIARG_COPYFLAGS Flags;
} D3DDDIARG_UPDATESUBRESOURCEUP;
````


## -struct-fields
<dl>

### -field <b>hResource</b>

<dd>
<p>A handle to the destination resource to copy to.</p>
</dd>

### -field <b>SubResourceIndex</b>

<dd>
<p>The index of the destination subresource to which data is to be copied.</p>
</dd>

### -field <b>DstBox</b>

<dd>
<p>A destination region, of type  <a href="https://msdn.microsoft.com/library/windows/hardware/hh451148">D3DDDIBOX</a>, of the subresource to which data is to be copied. If <b>Flags</b>-&gt;<a href="https://msdn.microsoft.com/DA114D60-60EE-4D1D-B42C-A84CE54C8B95">BoxValid</a> is not set, the entire subresource must be updated.</p>
</dd>

### -field <b>pSysMemUP</b>

<dd>
<p>A pointer to the beginning address of the source data that the <a href="https://msdn.microsoft.com/5AF55FED-6FD6-41BE-A743-1E9D0EA51C9C">pfnUpdateSubresourceUP</a> function copies to update the destination subresouce.</p>
</dd>

### -field <b>RowPitch</b>

<dd>
<p>The offset, in bytes, to move to the next row of source data.</p>
</dd>

### -field <b>DepthPitch</b>

<dd>
<p>The offset, in bytes, to move to the next depth slice of source data.</p>
</dd>

### -field <b>Flags</b>

<dd>
<p>A <a href="https://msdn.microsoft.com/library/windows/hardware/dn449151">D3DDDIARG_COPYFLAGS</a> structure that specifies additional characteristics of the subresource update operation.</p>
</dd>
</dl>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 8.1</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>Windows Server 2012 R2</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>D3dumddi.h (include D3d10umddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/dn449151">D3DDDIARG_COPYFLAGS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh451148">D3DDDIBOX</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/5AF55FED-6FD6-41BE-A743-1E9D0EA51C9C">pfnUpdateSubresourceUP</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3DDDIARG_UPDATESUBRESOURCEUP structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>