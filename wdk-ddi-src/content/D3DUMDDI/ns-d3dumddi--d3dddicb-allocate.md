---
UID: NS.d3dumddi._D3DDDICB_ALLOCATE
title: D3DDDICB_ALLOCATE
author: windows-driver-content
description: The D3DDDICB_ALLOCATE structure contains information for allocating memory.
old-location: display\d3dddicb_allocate.htm
ms.assetid: 76ebc960-ff63-40eb-842b-acdb549ecdaa
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
req.alt-api: D3DDDICB_ALLOCATE
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
ms.keywords: D3DDDICB_ALLOCATE, D3DDDICB_ALLOCATE
req.iface: 
---

# D3DDDICB_ALLOCATE structure



## -description
<p>The D3DDDICB_ALLOCATE structure contains information for allocating memory.</p>


## -syntax

````
typedef struct _D3DDDICB_ALLOCATE {
  const VOID            *pPrivateDriverData;
  UINT                  PrivateDriverDataSize;
  HANDLE                hResource;
  D3DKMT_HANDLE         hKMResource;
  UINT                  NumAllocations;
#if (D3D_UMD_INTERFACE_VERSION >= D3D_UMD_INTERFACE_VERSION_WIN7)
  union {
    D3DDDI_ALLOCATIONINFO  *pAllocationInfo;
    D3DDDI_ALLOCATIONINFO2 *pAllocationInfo2;
  };
#else 
  D3DDDI_ALLOCATIONINFO *pAllocationInfo;
} D3DDDICB_ALLOCATE;
````


## -struct-fields
<dl>

### -field <b>pPrivateDriverData</b>

<dd>
<p>[in] A pointer to private data, which is passed to the display miniport driver. This data is per resource and not per allocation. If allocations are attached to an existing resource, the current data should overwrite the former data.</p>
</dd>

### -field <b>PrivateDriverDataSize</b>

<dd>
<p>[in] The size, in bytes, of the private data that is pointed to by <b>pPrivateDriverData</b>.</p>
</dd>

### -field <b>hResource</b>

<dd>
<p>[in] A handle to the resource that is associated with the allocations. </p>
<p>When the user-mode display driver calls the <a href="https://msdn.microsoft.com/a61e6c6a-3992-429c-ad8c-5f1a61dc7b8b">pfnAllocateCb</a> function, the driver should assign the value that was received from the <b>hResource</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff542963">D3DDDIARG_CREATERESOURCE</a> structure in a call to <a href="https://msdn.microsoft.com/5b74c989-1a62-4415-a19a-dd0ba2fcff83">CreateResource</a>, or the <b>hRTResource</b> parameter in a call to <a href="https://msdn.microsoft.com/c21839f0-8302-49f9-a2b4-4009fbd2d88c">CreateResource(D3D10)</a> or <a href="https://msdn.microsoft.com/2dff9d2e-c497-422f-824b-a7101904fd67">CreateResource(D3D11)</a>. It should assign the value to associate the allocations with the resource, or assign <b>NULL</b> to associate the allocations with the device. The driver must assign a non-<b>NULL</b> value for allocations that are created in response to shared resources. Shared resources might result from <b>CreateResource</b> calls with the <b>SharedResource</b> bit-field flag set in the <b>Flags</b> member of D3DDDIARG_CREATERESOURCE. They might also result from <b>CreateResource(D3D10)</b> or <b>CreateResource(D3D11)</b> calls, with the D3D10_DDI_RESOURCE_MISC_SHARED value set in the <b>MiscFlags</b> member of either <a href="https://msdn.microsoft.com/library/windows/hardware/ff541697">D3D10DDIARG_CREATERESOURCE</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff542062">D3D11DDIARG_CREATERESOURCE</a>.</p>
<p>The Microsoft Direct3D runtime should use this handle in driver calls to identify the resource.</p>
</dd>

### -field <b>hKMResource</b>

<dd>
<p>[out] A D3DKMT_HANDLE data type that represents a kernel-mode handle to the resource that is associated with the allocations.</p>
<p>The Direct3D runtime creates and returns a kernel-mode resource handle only if the user-mode display driver sets the <b>hResource</b> member of D3DDDICB_ALLOCATE to the user-mode runtime resource handle that was received from the <b>hResource</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff542963">D3DDDIARG_CREATERESOURCE</a> structure. This handle is received in a call to <a href="https://msdn.microsoft.com/5b74c989-1a62-4415-a19a-dd0ba2fcff83">CreateResource</a>, or from the <i>hResource</i> parameter in a call to either <a href="https://msdn.microsoft.com/c21839f0-8302-49f9-a2b4-4009fbd2d88c">CreateResource(D3D10)</a> or <a href="https://msdn.microsoft.com/2dff9d2e-c497-422f-824b-a7101904fd67">CreateResource(D3D11)</a>. </p>
<p>The Direct3D runtime generates a unique handle and passes it back to the user-mode display driver. The user-mode display driver can insert the kernel-mode resource handle in the command stream for subsequent use by the display miniport driver.</p>
</dd>

### -field <b>NumAllocations</b>

<dd>
<p>[in] The number of elements in the array at <b>pAllocationInfo</b>, which represents the number of allocations to allocate.</p>
</dd>

### -field <b>pAllocationInfo</b>

<dd>
<p>[in] An array of <a href="https://msdn.microsoft.com/library/windows/hardware/ff544364">D3DDDI_ALLOCATIONINFO</a> structures that describe the allocations to allocate.</p>
</dd>

### -field <b>pAllocationInfo2</b>

<dd>
<p>[in] This member is reserved and should be set to zero.</p>
<p>This member is available beginning with Windows 7.</p>
</dd>

### -field <b>pAllocationInfo</b>

<dd>
<p>[in] An array of <a href="https://msdn.microsoft.com/library/windows/hardware/ff544364">D3DDDI_ALLOCATIONINFO</a> structures that describe the allocations to allocate.</p>
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
<a href="https://msdn.microsoft.com/5b74c989-1a62-4415-a19a-dd0ba2fcff83">CreateResource</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/c21839f0-8302-49f9-a2b4-4009fbd2d88c">CreateResource(D3D10)</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/2dff9d2e-c497-422f-824b-a7101904fd67">CreateResource(D3D11)</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544364">D3DDDI_ALLOCATIONINFO</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541697">D3D10DDIARG_CREATERESOURCE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542062">D3D11DDIARG_CREATERESOURCE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542963">D3DDDIARG_CREATERESOURCE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/a61e6c6a-3992-429c-ad8c-5f1a61dc7b8b">pfnAllocateCb</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3DDDICB_ALLOCATE structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>