---
UID: NS.d3dkmthk._D3DKMT_CREATECONTEXTVIRTUAL
title: D3DKMT_CREATECONTEXTVIRTUAL
author: windows-driver-content
description: D3DKMT_CREATECONTEXTVIRTUAL is used with D3DKMTCreateContextVirtual to create a kernel mode device context that supports virtual addressing.
old-location: display\d3dkmt_createcontextvirtual.htm
ms.assetid: C9707F47-75DF-4CDE-B88B-24323FC8C94B
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmthk.h
req.include-header: D3dkmthk.h
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3DKMT_CREATECONTEXTVIRTUAL
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
ms.keywords: D3DKMT_CREATECONTEXTVIRTUAL, D3DKMT_CREATECONTEXTVIRTUAL
req.iface: 
---

# D3DKMT_CREATECONTEXTVIRTUAL structure



## -description
<p><b>D3DKMT_CREATECONTEXTVIRTUAL</b> is used with <a href="https://msdn.microsoft.com/library/windows/hardware/dn906770">D3DKMTCreateContextVirtual</a> to create a kernel mode device context that supports virtual addressing.

</p>


## -syntax

````
typedef struct _D3DKMT_CREATECONTEXTVIRTUAL {
  D3DKMT_HANDLE             hDevice;
  UINT                      NodeOrdinal;
  UINT                      EngineAffinity;
  D3DDDI_CREATECONTEXTFLAGS Flags;
  VOID                      *pPrivateDriverData;
  UINT                      PrivateDriverDataSize;
  D3DKMT_CLIENTHINT         ClientHint;
  D3DKMT_HANDLE             hContext;
} D3DKMT_CREATECONTEXTVIRTUAL;
````


## -struct-fields
<dl>

### -field <b>hDevice</b>

<dd>
<p>[in] A handle to the device.</p>
</dd>

### -field <b>NodeOrdinal</b>

<dd>
<p>[in] The zero-based index for the node that the context is scheduled on.</p>
</dd>

### -field <b>EngineAffinity</b>

<dd>
<p>[in] The zero-based index for the engine, within the node that <b>NodeOrdinal</b> specifies, that the context can run in.</p>
</dd>

### -field <b>Flags</b>

<dd>
<p>[in] A <a href="https://msdn.microsoft.com/library/windows/hardware/ff544502">D3DDDI_CREATECONTEXTFLAGS</a> structure that indicates, in bit-field flags, how to create the context. </p>
</dd>

### -field <b>pPrivateDriverData</b>

<dd>
<p>[in] A pointer to private data that is passed to a display miniport driver.</p>
</dd>

### -field <b>PrivateDriverDataSize</b>

<dd>
<p>[in] The size, in bytes, of the private data that <b>pPrivateDriverData</b> points to.</p>
</dd>

### -field <b>ClientHint</b>

<dd>
<p>[in] A hint describing which graphics subsystem is creating the context.</p>
</dd>

### -field <b>hContext</b>

<dd>
<p>[out] A handle to the context that the <a href="https://msdn.microsoft.com/library/windows/hardware/dn906770">D3DKMTCreateContextVirtual</a> function creates. </p>
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
<p>Windows 10</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>Windows Server 2016</p>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/dn906770">D3DKMTCreateContextVirtual</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544502">D3DDDI_CREATECONTEXTFLAGS</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3DKMT_CREATECONTEXTVIRTUAL structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>