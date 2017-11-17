---
UID: NS.d3dkmddi._DXGKARG_PRESENT
title: DXGKARG_PRESENT
author: windows-driver-content
description: The DXGKARG_PRESENT structure describes a source-to-primary copy operation.
old-location: display\dxgkarg_present.htm
ms.assetid: 1bf91677-fa9e-4738-b8ea-efce90a52859
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
req.alt-api: DXGKARG_PRESENT
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
ms.keywords: DXGKARG_PRESENT, DXGKARG_PRESENT
req.iface: 
---

# DXGKARG_PRESENT structure



## -description
<p>The DXGKARG_PRESENT structure describes a source-to-primary copy operation.</p>


## -syntax

````
typedef struct _DXGKARG_PRESENT {
  VOID                     *pDmaBuffer;
  UINT                     DmaSize;
  VOID                     *pDmaBufferPrivateData;
  UINT                     DmaBufferPrivateDataSize;
#if (DXGKDDI_INTERFACE_VERSION >= DXGKDDI_INTERFACE_VERSION_WIN7)
  union {
    DXGK_ALLOCATIONLIST               *pAllocationList;
    DXGK_PRESENTALLOCATIONINFO        *pAllocationInfo;
#if (DXGKDDI_INTERFACE_VERSION >= DXGKDDI_INTERFACE_VERSION_WIN8)
    DXGK_PRESENTMULTIPLANEOVERLAYINFO *pPresentMultiPlaneOverlayInfo;
#endif 
  };
  D3DDDI_PATCHLOCATIONLIST *pPatchLocationListOut;
  UINT                     PatchLocationListOutSize;
#else 
  DXGK_ALLOCATIONLIST      *pAllocationList;
  D3DDDI_PATCHLOCATIONLIST *pPatchLocationListOut;
  UINT                     PatchLocationListOutSize;
#endif 
  UINT                     MultipassOffset;
  UINT                     Color;
  RECT                     DstRect;
  RECT                     SrcRect;
  UINT                     SubRectCnt;
  const RECT               *pDstSubRects;
  D3DDDI_FLIPINTERVAL_TYPE FlipInterval;
  DXGK_PRESENTFLAGS        Flags;
  UINT                     DmaBufferSegmentId;
  PHYSICAL_ADDRESS         DmaBufferPhysicalAddress;
#if (DXGKDDI_INTERFACE_VERSION >= DXGKDDI_INTERFACE_VERSION_WDDM1_3)
  UINT                     Reserved;
#endif 
#if (DXGKDDI_INTERFACE_VERSION >= DXGKDDI_INTERFACE_VERSION_WDDM2_0)
  D3DGPU_VIRTUAL_ADDRESS   DmaBufferGpuVirtualAddress;
  UINT                     NumSrcAllocations;
  UINT                     NumDstAllocations;
  UINT                     PrivateDriverDataSize;
  PVOID                    pPrivateDriverData;
#endif 
} DXGKARG_PRESENT;
````


## -struct-fields
<dl>

### -field <b>pDmaBuffer</b>

<dd>
<p>[out] A pointer to the start of the DMA buffer, which is aligned on 4 KB. This buffer can be sent through DMA to the graphics hardware. Before the display miniport driver returns from the <a href="https://msdn.microsoft.com/1a46b129-1e78-44e6-a609-59eab206692b">DxgkDdiPresent</a> function, the driver should set <b>pDmaBuffer</b> to the next empty byte that follows the last byte that the driver wrote to, or the driver should point to the location (one byte beyond the buffer space) if no more space is available. This location would have been correct if the buffer was large enough.</p>
</dd>

### -field <b>DmaSize</b>

<dd>
<p>[in] The size, in bytes, of the DMA buffer that <b>pDmaBuffer</b> points to.</p>
</dd>

### -field <b>pDmaBufferPrivateData</b>

<dd>
<p>[in] A pointer to a driver-resident private data structure that is associated with the DMA buffer that <b>pDmaBuffer</b> points to.</p>
</dd>

### -field <b>DmaBufferPrivateDataSize</b>

<dd>
<p>[in] The number of bytes that remain in the private data structure that <b>pDmaBufferPrivateData</b> points to for the current operation.</p>
</dd>

### -field <b>pAllocationList</b>

<dd>
<p>[in] An array of <a href="https://msdn.microsoft.com/library/windows/hardware/ff560975">DXGK_ALLOCATIONLIST</a> structures that describe the source, destination, or both for the copy operation. The driver accesses the source allocation handle through the <b>hDeviceSpecificAllocation</b> member of the <b>pAllocationList</b>[DXGK_PRESENT_SOURCE_INDEX] element (that is, element 1). The driver accesses the destination allocation handle through the <b>hDeviceSpecificAllocation</b> member of the <b>pAllocationList</b>[DXGK_PRESENT_DESTINATION_INDEX] element (that is, element 2). </p>
<p>The handles that are specified in the elements of the allocation list are the device-specific handles that the driver's <a href="https://msdn.microsoft.com/551154d7-950d-40e5-810b-8d803c1731ca">DxgkDdiOpenAllocation</a> function returned when the allocations were opened. If a source or destination is not present for the operation, the <b>hDeviceSpecificAllocation</b> member of the respective element is <b>NULL</b>.</p>
<div class="alert"><b>Note</b>    The <b>hDeviceSpecificAllocation</b> member of the first element in the allocation list (element 0) is always <b>NULL</b>.</div>
<div> </div>
<p>This member is available beginning with Windows 7.</p>
</dd>

### -field <b>pAllocationInfo</b>

<dd>
<p>[in] Reserved for system use. The display miniport driver should ignore this member.</p>
<p>This member is available beginning with Windows 7.</p>
</dd>

### -field <b>pPresentMultiPlaneOverlayInfo</b>

<dd>
<p>[in] A pointer to a structure of type <a href="https://msdn.microsoft.com/library/windows/hardware/hh780311">DXGK_PRESENTMULTIPLANEOVERLAYINFO</a> that specifies info on a VidPN input and an overlay plane to display.</p>
<p>Supported starting with Windows 8.</p>
</dd>

### -field <b>pPatchLocationListOut</b>

<dd>
<p>[in/out] An array of <a href="https://msdn.microsoft.com/library/windows/hardware/ff544630">D3DDDI_PATCHLOCATIONLIST</a> structures for the patch-location list that the display miniport driver fills. Before the driver returns from a call to its <a href="https://msdn.microsoft.com/1a46b129-1e78-44e6-a609-59eab206692b">DxgkDdiPresent</a> function, the driver must set <b>pPatchLocationListOut</b> to the next D3DDDI_PATCHLOCATIONLIST element that follows the last D3DDDI_PATCHLOCATIONLIST element that the driver updated.</p>
</dd>

### -field <b>PatchLocationListOutSize</b>

<dd>
<p>[in] The number of elements in the patch-location list that <b>pPatchLocationListOut</b> specifies. The display miniport driver is not required to fill all of the elements in the entire list; the driver must use only elements that are necessary to describe the patch location within the DMA buffer.</p>
</dd>

### -field <b>pAllocationList</b>

<dd>
<p>[in] An array of <a href="https://msdn.microsoft.com/library/windows/hardware/ff560975">DXGK_ALLOCATIONLIST</a> structures that describe the source, destination, or both for the copy operation. The driver accesses the source allocation handle through the <b>hDeviceSpecificAllocation</b> member of the <b>pAllocationList</b>[DXGK_PRESENT_SOURCE_INDEX] element (that is, element 1). The driver accesses the destination allocation handle through the <b>hDeviceSpecificAllocation</b> member of the <b>pAllocationList</b>[DXGK_PRESENT_DESTINATION_INDEX] element (that is, element 2). </p>
<p>The handles that are specified in the elements of the allocation list are the device-specific handles that the driver's <a href="https://msdn.microsoft.com/551154d7-950d-40e5-810b-8d803c1731ca">DxgkDdiOpenAllocation</a> function returned when the allocations were opened. If a source or destination is not present for the operation, the <b>hDeviceSpecificAllocation</b> member of the respective element is <b>NULL</b>.</p>
<div class="alert"><b>Note</b>    The <b>hDeviceSpecificAllocation</b> member of the first element in the allocation list (element 0) is always <b>NULL</b>.</div>
<div> </div>
</dd>

### -field <b>pPatchLocationListOut</b>

<dd>
<p>[in/out] An array of <a href="https://msdn.microsoft.com/library/windows/hardware/ff544630">D3DDDI_PATCHLOCATIONLIST</a> structures for the patch-location list that the display miniport driver fills. Before the driver returns from a call to its <a href="https://msdn.microsoft.com/1a46b129-1e78-44e6-a609-59eab206692b">DxgkDdiPresent</a> function, the driver must set <b>pPatchLocationListOut</b> to the next D3DDDI_PATCHLOCATIONLIST element that follows the last D3DDDI_PATCHLOCATIONLIST element that the driver updated.</p>
</dd>

### -field <b>PatchLocationListOutSize</b>

<dd>
<p>[in] The number of elements in the patch-location list that <b>pPatchLocationListOut</b> specifies. The display miniport driver is not required to fill all of the elements in the entire list; the driver must use only elements that are necessary to describe the patch location within the DMA buffer.</p>
</dd>

### -field <b>MultipassOffset</b>

<dd>
<p>[in/out] A UINT value that specifies the progress of the copying operation if the display miniport driver's <a href="https://msdn.microsoft.com/1a46b129-1e78-44e6-a609-59eab206692b">DxgkDdiPresent</a> function must return STATUS_GRAPHICS_INSUFFICIENT_DMA_BUFFER to obtain a new DMA buffer. When the driver's <i>DxgkDdiPresent</i>function is first called with a new <a href="https://msdn.microsoft.com/library/windows/hardware/ff569234">RECT</a> list, <b>MultipassOffset</b> is initialized to zero. Before the driver returns from the <i>DxgkDdiPresent </i>call, the driver sets <b>MultipassOffset</b> to show copy progress for subsequent <i>DxgkDdiPresent </i>calls with the same command buffer. The Microsoft DirectX graphics kernel subsystem does not change the value further. </p>
</dd>

### -field <b>Color</b>

<dd>
<p>[in] The A8R8G8B8 color in either a color-fill operation, which is specified by the <b>ColorFill</b> bit-field flag set in the <b>Flags</b> member, or a color-key operation, which is specified by either the <b>SrcColorKey</b> or <b>DstColorKey</b> bit-field flag. Note that only one of the <b>ColorFill</b>, <b>SrcColorKey</b>, and <b>DstColorKey</b> bit-field flags is set at any time.</p>
<p>If the primary format is palettized RGB, <b>Color</b> contains the palette index rather than the D3DDDIFMT_A8R8G8B8 value from the <a href="https://msdn.microsoft.com/library/windows/hardware/ff544312">D3DDDIFORMAT</a> enumeration type. </p>
</dd>

### -field <b>DstRect</b>

<dd>
<p>[in] A <a href="https://msdn.microsoft.com/library/windows/hardware/ff569234">RECT</a> structure for the destination rectangle that is used to calculate the stretch factor.</p>
</dd>

### -field <b>SrcRect</b>

<dd>
<p>[in] A RECT structure for the source rectangle that is used to calculate the stretch factor.</p>
</dd>

### -field <b>SubRectCnt</b>

<dd>
<p>[in] The number of destination sub-rectangles in the array that <b>pDstSubRects</b> specifies.</p>
</dd>

### -field <b>pDstSubRects</b>

<dd>
<p>[in] An array of RECT structures for the list of destination sub-rectangles that the <i>DxgkDdiPresent </i>function copies to.</p>
</dd>

### -field <b>FlipInterval</b>

<dd>
<p>[in] A <a href="https://msdn.microsoft.com/library/windows/hardware/ff544549">D3DDDI_FLIPINTERVAL_TYPE</a>-typed value that indicates the flip interval (that is, if the flip occurs after zero, one, two, three, or four vertical syncs). </p>
</dd>

### -field <b>Flags</b>

<dd>
<p>[in] A <a href="https://msdn.microsoft.com/library/windows/hardware/ff562005">DXGK_PRESENTFLAGS</a> structure that identifies, in bit-field flags, the type of present operation to perform. Note that the <b>ColorFill</b>, <b>SrcColorKey</b>, and <b>DstColorKey</b> bit-field flags in <b>Flags</b> are mutually exclusive.</p>
</dd>

### -field <b>DmaBufferSegmentId</b>

<dd>
<p>[in] The identifier of the memory segment that the DMA buffer was paged in. If the identifier is zero, the DMA buffer is not correctly paged in.</p>
</dd>

### -field <b>DmaBufferPhysicalAddress</b>

<dd>
<p>[in] A <b>PHYSICAL_ADDRESS</b> data type (which is defined as <b>LARGE_INTEGER</b>) that indicates the physical address where the DMA buffer was paged in. If the physical address is zero, the DMA buffer is not correctly paged in.</p>
</dd>

### -field <b>Reserved</b>

<dd>
<p>[in] Reserved for system use. The driver should ignore this member.</p>
</dd>

### -field <b>DmaBufferGpuVirtualAddress</b>

<dd></dd>

### -field <b>NumSrcAllocations</b>

<dd></dd>

### -field <b>NumDstAllocations</b>

<dd></dd>

### -field <b>PrivateDriverDataSize</b>

<dd></dd>

### -field <b>pPrivateDriverData</b>

<dd></dd>
</dl>

## -remarks
<p>The ratio of the source and destination rectangular areas that the <b>SrcRect</b> and <b>DstRect</b> members specify is used to compute a stretch factor. The driver can factor in the stretch-factor calculation when it performs the copy operation. </p>

<p>The driver is not required to perform any clipping. The Microsoft DirectX graphics kernel subsystem preclips the list of destination sub-rectangles that the <b>pDstSubRects</b> member specifies  to the coordinates of the destination rectangle that the <b>DstRect</b> member specifies and to the screen (primary). Note that if a list of destination sub-rectangles is supplied in <b>pDstSubRects</b>, the driver should use only <b>SrcRect</b> and <b>DstRect</b> to compute the stretch factor and should use the coordinates of the destination sub-rectangles for the actual copy operation. </p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544549">D3DDDI_FLIPINTERVAL_TYPE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544630">D3DDDI_PATCHLOCATIONLIST</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff560975">DXGK_ALLOCATIONLIST</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562005">DXGK_PRESENTFLAGS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh780311">DXGK_PRESENTMULTIPLANEOVERLAYINFO</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/1a46b129-1e78-44e6-a609-59eab206692b">DxgkDdiPresent</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff569234">RECT</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20DXGKARG_PRESENT structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>