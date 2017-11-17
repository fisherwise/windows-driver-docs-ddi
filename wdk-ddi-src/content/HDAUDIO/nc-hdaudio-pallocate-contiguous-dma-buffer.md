---
UID: NC.hdaudio.PALLOCATE_CONTIGUOUS_DMA_BUFFER
title: PALLOCATE_CONTIGUOUS_DMA_BUFFER
author: windows-driver-content
description: The AllocateContiguousDmaBuffer routine allocates a DMA buffer that consists of a single, contiguous block of physical memory.The function pointer type for an AllocateContiguousDmaBuffer routine is defined as:
old-location: audio\allocatecontiguousdmabuffer.htm
ms.assetid: 4538ce8e-fccd-4862-b226-a99fe578a5fd
ms.author: windowsdriverdev
ms.date: 10/30/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: audio
req.header: hdaudio.h
req.include-header: Hdaudio.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: AllocateContiguousDmaBuffer
req.alt-loc: hdaudio.h
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
ms.keywords: SM_SetRNIDMgmtInfo_OUT, SM_SetRNIDMgmtInfo_OUT, *PSM_SetRNIDMgmtInfo_OUT
req.iface: 
---

# PALLOCATE_CONTIGUOUS_DMA_BUFFER callback



## -description
<p>The <code>AllocateContiguousDmaBuffer</code> routine allocates a DMA buffer that consists of a single, contiguous block of physical memory.</p>
<p>The function pointer type for an <code>AllocateContiguousDmaBuffer</code> routine is defined as:</p>


## -prototype

````
PALLOCATE_CONTIGUOUS_DMA_BUFFER AllocateContiguousDmaBuffer;

NTSTATUS AllocateContiguousDmaBuffer(
  _In_  PVOID                      context,
  _In_  HANDLE                     handle,
        ULONG                      requestedBufferSize,
  _Out_ PVOID                      *dataBuffer,
  _Out_ PHDAUDIO_BUFFER_DESCRIPTOR *bdl
)
{ ... }
````


## -parameters
<dl>

### -param <i>context</i> [in]

<dd>
<p>Specifies the context value from the <b>Context</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff536416">HDAUDIO_BUS_INTERFACE_BDL</a> structure.</p>
</dd>

### -param <i>handle</i> [in]

<dd>
<p>Handle identifying the DMA engine. This handle value was obtained from a previous call to <a href="https://msdn.microsoft.com/038e52be-04db-41c2-aa19-85bc4eb8bc57">AllocateCaptureDmaEngine</a> or <a href="https://msdn.microsoft.com/fb2a64ca-7e8e-4352-86c6-b9500e535c75">AllocateRenderDmaEngine</a>.</p>
</dd>

### -param <i>requestedBufferSize</i> 

<dd>
<p>Specifies the requested buffer size in bytes.</p>
</dd>

### -param <i>dataBuffer</i> [out]

<dd>
<p>Retrieves the data buffer. This parameter points to a caller-allocated PVOID variable into which the routine writes the system virtual address of the data buffer.</p>
</dd>

### -param <i>bdl</i> [out]

<dd>
<p>Retrieves the buffer descriptor list (BDL). This parameter points to a caller-allocated PVOID variable into which the routine writes the system virtual address of the BDL. The BDL allocation size is exactly one memory page and the BDL begins on a page boundary.</p>
</dd>
</dl>

## -returns
<p><code>AllocateContiguousDmaBuffer</code> returns STATUS_SUCCESS if the call succeeds. Otherwise, the routine returns an appropriate error code. The following table shows some of the possible return status codes.</p><dl>
<dt><b>STATUS_UNSUCCESSFUL</b></dt>
</dl><p>Indicates that the caller is running at an interrupt request level (IRQL) that is too high.</p><dl>
<dt><b>STATUS_INSUFFICIENT_RESOURCES</b></dt>
</dl><p>Indicates that buffer allocation failed.</p><dl>
<dt><b>STATUS_INVALID_HANDLE</b></dt>
</dl><p>Indicates that the handle parameter value is invalid.</p><dl>
<dt><b>STATUS_INVALID_PARAMETER</b></dt>
</dl><p>Indicates that one of the parameter values is incorrect (bad pointer).</p><dl>
<dt><b>STATUS_DEVICE_NOT_READY</b></dt>
</dl><p>Indicates that the hardware programming timed out. If this occurs, the hardware might be in a compromised state.</p><dl>
<dt><b>STATUS_INVALID_DEVICE_REQUEST</b></dt>
</dl><p>Indicates that the stream is not in the reset state or that a buffer is already allocated for the DMA engine.</p>

<p> </p>

## -remarks
<p>The <code>AllocateContiguousDmaBuffer</code> routine is used in conjunction with the <a href="https://msdn.microsoft.com/2760579b-9922-4709-a049-a73f3abd5043">SetupDmaEngineWithBdl</a> and <a href="https://msdn.microsoft.com/7aaf98cc-8a94-44e6-9fef-76e00db17405">FreeContiguousDmaBuffer</a> routines. These three routines are available only in the HDAUDIO_BUS_INTERFACE_BDL version of the HD Audio DDI. This DDI does not include the <a href="https://msdn.microsoft.com/44fd988a-24b3-4587-88d9-30585800ffbf">AllocateDmaBuffer</a> and <a href="https://msdn.microsoft.com/658e32d2-40e2-4479-8212-df7140fe6b74">FreeDmaBuffer</a> routines, which are never used in conjunction with <code>AllocateContiguousDmaBuffer</code>, <b>SetupDmaEngineWithBdl</b>, and <b>FreeContiguousDmaBuffer</b>. Unlike <b>SetupDmaEngineWithBdl</b>, which configures the DMA engine to use a previously allocated DMA buffer, <code>AllocateDmaBuffer</code> both allocates a DMA buffer and configures the DMA engine to use the buffer. For more information, see <a href="https://msdn.microsoft.com/e24071d3-9021-40c0-907a-91ada8a1306b">Differences between the Two DDI Versions</a>.</p>

<p><code>AllocateContiguousDmaBuffer</code> allocates a data buffer for the specified DMA engine. It also allocates a page of memory for the BDL. Depending on the host processor architecture, a typical page size might be 4,096 or 8,192 bytes. The data buffer consists of a single, contiguous block of physical memory.</p>

<p>The handle parameter specifies the DMA engine that is to use the data buffer and BDL. The routine allocates storage that meets the DMA engine's size, alignment, and position requirements.</p>

<p>The storage that the routine allocates for the data buffer and BDL is uninitialized. The function driver is responsible for filling in the BDL before submitting it to the <b>SetupDmaEngineWithBdl</b> routine. The function driver is also responsible for programming the codec to manage the data transfers and to recognize the stream identifier.</p>

<p>To generate IOC interrupts at precise intervals, the function driver might be required to divide the data buffer allocation into several fragments of a particular size. Each fragment is described by a BDL entry. The fragment size can be adjusted to tune the interrupt rate. According to the Intel High Definition Audio Specification (see the <a href="http://go.microsoft.com/fwlink/p/?linkid=42508">Intel HD Audio</a> website), each fragment must begin on a 128-byte boundary, although no such alignment requirement applies to the length of the fragment. Thus, a gap might exist between the end of one fragment and the beginning of the next. When calling <b>SetupDmaEngineWithBdl</b>, the function driver must specify a value for the <i>bufferSize</i> parameter that represents the sum of the sizes of the individual fragments that the BDL entries describe. This size will be less than or equal to the number of bytes specified in the <code>AllocateContiguousDmaBuffer</code> routine's <i>requestedBufferSize</i> parameter.</p>

<p>During the lifetime of a DMA engine handle, <code>AllocateContiguousDmaBuffer</code> can be called successively to allocate new DMA buffers. However, before calling <code>AllocateContiguousDmaBuffer</code>, any previously allocated DMA buffer must first be freed by calling <b>FreeContiguousDmaBuffer</b>.</p>

<p>During calls to <code>AllocateContiguousDmaBuffer</code>, <b>SetupDmaEngineWithBdl</b>, and <b>FreeContiguousDmaBuffer</b>, the DMA engine must be in the reset stream state. The DMA engine is in the reset state immediately following the call to Allocate<i>Xxx</i>DmaEngine. To change the DMA engine to the run state, call <a href="https://msdn.microsoft.com/05cfb827-e143-4d77-b378-e02dd381e429">SetDmaEngineState</a>.</p>

<p>This routine fails and returns error code STATUS_INVALID_DEVICE_REQUEST in either of the following circumstances:</p>

<p>Any previously allocated DMA buffer has not been freed (by calling <b>FreeContiguousDmaBuffer</b>).</p>

<p>The stream is in a state other than reset.</p>

<p>The <code>AllocateContiguousDmaBuffer</code> routine is used in conjunction with the <a href="https://msdn.microsoft.com/2760579b-9922-4709-a049-a73f3abd5043">SetupDmaEngineWithBdl</a> and <a href="https://msdn.microsoft.com/7aaf98cc-8a94-44e6-9fef-76e00db17405">FreeContiguousDmaBuffer</a> routines. These three routines are available only in the HDAUDIO_BUS_INTERFACE_BDL version of the HD Audio DDI. This DDI does not include the <a href="https://msdn.microsoft.com/44fd988a-24b3-4587-88d9-30585800ffbf">AllocateDmaBuffer</a> and <a href="https://msdn.microsoft.com/658e32d2-40e2-4479-8212-df7140fe6b74">FreeDmaBuffer</a> routines, which are never used in conjunction with <code>AllocateContiguousDmaBuffer</code>, <b>SetupDmaEngineWithBdl</b>, and <b>FreeContiguousDmaBuffer</b>. Unlike <b>SetupDmaEngineWithBdl</b>, which configures the DMA engine to use a previously allocated DMA buffer, <code>AllocateDmaBuffer</code> both allocates a DMA buffer and configures the DMA engine to use the buffer. For more information, see <a href="https://msdn.microsoft.com/e24071d3-9021-40c0-907a-91ada8a1306b">Differences between the Two DDI Versions</a>.</p>

<p><code>AllocateContiguousDmaBuffer</code> allocates a data buffer for the specified DMA engine. It also allocates a page of memory for the BDL. Depending on the host processor architecture, a typical page size might be 4,096 or 8,192 bytes. The data buffer consists of a single, contiguous block of physical memory.</p>

<p>The handle parameter specifies the DMA engine that is to use the data buffer and BDL. The routine allocates storage that meets the DMA engine's size, alignment, and position requirements.</p>

<p>The storage that the routine allocates for the data buffer and BDL is uninitialized. The function driver is responsible for filling in the BDL before submitting it to the <b>SetupDmaEngineWithBdl</b> routine. The function driver is also responsible for programming the codec to manage the data transfers and to recognize the stream identifier.</p>

<p>To generate IOC interrupts at precise intervals, the function driver might be required to divide the data buffer allocation into several fragments of a particular size. Each fragment is described by a BDL entry. The fragment size can be adjusted to tune the interrupt rate. According to the Intel High Definition Audio Specification (see the <a href="http://go.microsoft.com/fwlink/p/?linkid=42508">Intel HD Audio</a> website), each fragment must begin on a 128-byte boundary, although no such alignment requirement applies to the length of the fragment. Thus, a gap might exist between the end of one fragment and the beginning of the next. When calling <b>SetupDmaEngineWithBdl</b>, the function driver must specify a value for the <i>bufferSize</i> parameter that represents the sum of the sizes of the individual fragments that the BDL entries describe. This size will be less than or equal to the number of bytes specified in the <code>AllocateContiguousDmaBuffer</code> routine's <i>requestedBufferSize</i> parameter.</p>

<p>During the lifetime of a DMA engine handle, <code>AllocateContiguousDmaBuffer</code> can be called successively to allocate new DMA buffers. However, before calling <code>AllocateContiguousDmaBuffer</code>, any previously allocated DMA buffer must first be freed by calling <b>FreeContiguousDmaBuffer</b>.</p>

<p>During calls to <code>AllocateContiguousDmaBuffer</code>, <b>SetupDmaEngineWithBdl</b>, and <b>FreeContiguousDmaBuffer</b>, the DMA engine must be in the reset stream state. The DMA engine is in the reset state immediately following the call to Allocate<i>Xxx</i>DmaEngine. To change the DMA engine to the run state, call <a href="https://msdn.microsoft.com/05cfb827-e143-4d77-b378-e02dd381e429">SetDmaEngineState</a>.</p>

<p>This routine fails and returns error code STATUS_INVALID_DEVICE_REQUEST in either of the following circumstances:</p>

<p>Any previously allocated DMA buffer has not been freed (by calling <b>FreeContiguousDmaBuffer</b>).</p>

<p>The stream is in a state other than reset.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt>Desktop</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Hdaudio.h (include Hdaudio.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>PASSIVE_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536416">HDAUDIO_BUS_INTERFACE_BDL</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/038e52be-04db-41c2-aa19-85bc4eb8bc57">AllocateCaptureDmaEngine</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/fb2a64ca-7e8e-4352-86c6-b9500e535c75">AllocateRenderDmaEngine</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/2760579b-9922-4709-a049-a73f3abd5043">SetupDmaEngineWithBdl</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/7aaf98cc-8a94-44e6-9fef-76e00db17405">FreeContiguousDmaBuffer</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/44fd988a-24b3-4587-88d9-30585800ffbf">AllocateDmaBuffer</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/658e32d2-40e2-4479-8212-df7140fe6b74">FreeDmaBuffer</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/05cfb827-e143-4d77-b378-e02dd381e429">SetDmaEngineState</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [audio\audio]:%20PALLOCATE_CONTIGUOUS_DMA_BUFFER callback function%20 RELEASE:%20(10/30/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>