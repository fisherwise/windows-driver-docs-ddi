---
UID: NF.portcls.IPortWaveRTStream.AllocateContiguousPagesForMdl
title: IPortWaveRTStream::AllocateContiguousPagesForMdl
author: windows-driver-content
description: The AllocateContiguousPagesForMdl method allocates a list of contiguous, nonpaged, physical memory pages and returns a pointer to a memory descriptor list (MDL) that describes them.
old-location: audio\iportwavertstream_allocatecontiguouspagesformdl.htm
ms.assetid: 976f7e83-9b2a-4e1b-ab76-76d8e9711bff
ms.author: windowsdriverdev
ms.date: 10/30/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: audio
req.header: portcls.h
req.include-header: 
req.target-type: Universal
req.target-min-winverclnt: Available in Windows Vista and later Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IPortWaveRTStream.AllocateContiguousPagesForMdl
req.alt-loc: Portcls.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: Passive level
ms.keywords: IPortWaveRTStream, AllocateContiguousPagesForMdl, IPortWaveRTStream::AllocateContiguousPagesForMdl
req.iface: IPortWaveRTStream
---

# IPortWaveRTStream::AllocateContiguousPagesForMdl method



## -description
<p>The <code>AllocateContiguousPagesForMdl</code> method allocates a list of contiguous, nonpaged, physical memory pages and returns a pointer to a memory descriptor list (<a href="https://msdn.microsoft.com/library/windows/hardware/ff554414">MDL</a>) that describes them.</p>


## -syntax

````
PMDL AllocateContiguousPagesForMdl(
  [in] PHYSICAL_ADDRESS LowAddress,
  [in] PHYSICAL_ADDRESS HighAddress,
  [in] SIZE_T           TotalBytes
);
````


## -parameters
<dl>

### -param <i>LowAddress</i> [in]

<dd>
<p>Specifies the low end of the address range from which the storage for the MDL can be allocated.</p>
</dd>

### -param <i>HighAddress</i> [in]

<dd>
<p>Specifies the high end of the address range from which the storage for the MDL can be allocated.</p>
</dd>

### -param <i>TotalBytes</i> [in]

<dd>
<p>Specifies the total number of bytes to allocate for the MDL. This method always allocates an integral number of memory pages.</p>
</dd>
</dl>

## -returns
<p><code>AllocateContiguousPagesForMdl</code> returns a pointer to an MDL (PMDL) that describes a list of physical memory pages. If the method is unable to allocate the requested buffer, it returns <b>NULL</b>.</p>

## -remarks
<p>The driver calls this method to allocate a block of physically contiguous memory pages. All of the physical memory pages in the MDL fall within the address range specified by the <i>LowAddress</i> and <i>HighAddress</i> parameters. If sufficient memory is available, the memory allocation is the requested size rounded up to the next page; otherwise, the call fails.</p>

<p>After a system has been running for some time, the system's pool of nonpaged memory tends to become fragmented, which increases the probability that a request to allocate a large block of contiguous physical memory will fail. If the DMA controller of the audio device does not require the physical memory pages to be contiguous, the driver must call <a href="https://msdn.microsoft.com/library/windows/hardware/ff536925">IPortWaveRTStream::AllocatePagesForMdl</a> instead. Unlike <code>AllocateContiguousPagesForMdl</code>, the <b>AllocatePagesForMdl</b> method is not affected by memory fragmentation.</p>

<p>The <code>AllocateContiguousPagesforMdl</code> method allocates memory pages that are locked (nonpaged) but unmapped. If the miniport driver requires software access to this memory, the miniport driver must make a subsequent call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff536932">IPortWaveRTStream::MapAllocatedPages</a> to map the pages into kernel-mode address space.</p>

<p>The driver calls this method to allocate a block of physically contiguous memory pages. All of the physical memory pages in the MDL fall within the address range specified by the <i>LowAddress</i> and <i>HighAddress</i> parameters. If sufficient memory is available, the memory allocation is the requested size rounded up to the next page; otherwise, the call fails.</p>

<p>After a system has been running for some time, the system's pool of nonpaged memory tends to become fragmented, which increases the probability that a request to allocate a large block of contiguous physical memory will fail. If the DMA controller of the audio device does not require the physical memory pages to be contiguous, the driver must call <a href="https://msdn.microsoft.com/library/windows/hardware/ff536925">IPortWaveRTStream::AllocatePagesForMdl</a> instead. Unlike <code>AllocateContiguousPagesForMdl</code>, the <b>AllocatePagesForMdl</b> method is not affected by memory fragmentation.</p>

<p>The <code>AllocateContiguousPagesforMdl</code> method allocates memory pages that are locked (nonpaged) but unmapped. If the miniport driver requires software access to this memory, the miniport driver must make a subsequent call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff536932">IPortWaveRTStream::MapAllocatedPages</a> to map the pages into kernel-mode address space.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt><a href="http://go.microsoft.com/fwlink/p/?linkid=531356" target="_blank">Universal</a></dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Available in Windows Vista and later Windows operating systems.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Portcls.h</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>Passive level</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536925">IPortWaveRTStream::AllocatePagesForMdl</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536932">IPortWaveRTStream::MapAllocatedPages</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [audio\audio]:%20IPortWaveRTStream::AllocateContiguousPagesForMdl method%20 RELEASE:%20(10/30/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>