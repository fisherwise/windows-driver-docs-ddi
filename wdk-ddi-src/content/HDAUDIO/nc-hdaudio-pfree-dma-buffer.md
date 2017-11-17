---
UID: NC.hdaudio.PFREE_DMA_BUFFER
title: PFREE_DMA_BUFFER
author: windows-driver-content
description: The FreeDmaBuffer routine frees a DMA buffer that was previously allocated by a call to AllocateDmaBuffer.The function pointer type for a FreeDmaBuffer routine is defined as:
old-location: audio\freedmabuffer.htm
ms.assetid: 658e32d2-40e2-4479-8212-df7140fe6b74
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
req.alt-api: FreeDmaBuffer
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

# PFREE_DMA_BUFFER callback



## -description
<p>The <code>FreeDmaBuffer</code> routine frees a DMA buffer that was previously allocated by a call to <b>AllocateDmaBuffer</b>.</p>
<p>The function pointer type for a <code>FreeDmaBuffer</code> routine is defined as:</p>


## -prototype

````
PFREE_DMA_BUFFER FreeDmaBuffer;

NTSTATUS FreeDmaBuffer(
  _In_ PVOID  context,
  _In_ HANDLE handle
)
{ ... }
````


## -parameters
<dl>

### -param <i>context</i> [in]

<dd>
<p>Specifies the context value from the <b>Context</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff536413">HDAUDIO_BUS_INTERFACE</a> or the <a href="https://msdn.microsoft.com/library/windows/hardware/ff536418">HDAUDIO_BUS_INTERFACE_V2</a> structure.</p>
</dd>

### -param <i>handle</i> [in]

<dd>
<p>Handle identifying the DMA engine. This handle value was obtained from a previous call to <a href="https://msdn.microsoft.com/038e52be-04db-41c2-aa19-85bc4eb8bc57">AllocateCaptureDmaEngine</a> or <a href="https://msdn.microsoft.com/fb2a64ca-7e8e-4352-86c6-b9500e535c75">AllocateRenderDmaEngine</a>.</p>
</dd>
</dl>

## -returns
<p><code>FreeDmaBuffer</code> returns STATUS_SUCCESS if the call succeeds. Otherwise, the routine returns an appropriate error code. The following table shows some of the possible return status codes.</p><dl>
<dt><b>STATUS_UNSUCCESSFUL</b></dt>
</dl><p>Indicates that the caller is running at an IRQL that is too high.</p><dl>
<dt><b>STATUS_INVALID_HANDLE</b></dt>
</dl><p>Indicates that the handle parameter value is invalid.</p><dl>
<dt><b>STATUS_INVALID_DEVICE_REQUEST</b></dt>
</dl><p>Indicates that the stream is not in the reset state or that no buffer is currently allocated for the DMA engine.</p>

<p> </p>

## -remarks
<p>The <code>FreeDmaBuffer</code> routine is used in conjunction with the <a href="https://msdn.microsoft.com/44fd988a-24b3-4587-88d9-30585800ffbf">AllocateDmaBuffer</a> routine. These two routines are available only in the HDAUDIO_BUS_INTERFACE version of the HD Audio DDI. This DDI does not include the <a href="https://msdn.microsoft.com/4538ce8e-fccd-4862-b226-a99fe578a5fd">AllocateContiguousDmaBuffer</a>, <a href="https://msdn.microsoft.com/2760579b-9922-4709-a049-a73f3abd5043">SetupDmaEngineWithBdl</a>, and <a href="https://msdn.microsoft.com/7aaf98cc-8a94-44e6-9fef-76e00db17405">FreeContiguousDmaBuffer</a> routines, which are never used in conjunction with <b>AllocateDmaBuffer</b> and <code>FreeDmaBuffer</code>. Unlike <b>SetupDmaEngineWithBdl</b>, which configures the DMA engine to use a previously allocated DMA buffer, <b>AllocateDmaBuffer</b> both allocates a DMA buffer and configures the DMA engine to use the buffer.</p>

<p>The routine fails and returns error code STATUS_INVALID_DEVICE_REQUEST in either of the following circumstances:</p>

<p>The client calls <code>FreeDmaBuffer</code> when no buffer is currently allocated for the DMA engine.</p>

<p>The stream is in a state other than reset.</p>

<p>The <code>FreeDmaBuffer</code> routine is used in conjunction with the <a href="https://msdn.microsoft.com/44fd988a-24b3-4587-88d9-30585800ffbf">AllocateDmaBuffer</a> routine. These two routines are available only in the HDAUDIO_BUS_INTERFACE version of the HD Audio DDI. This DDI does not include the <a href="https://msdn.microsoft.com/4538ce8e-fccd-4862-b226-a99fe578a5fd">AllocateContiguousDmaBuffer</a>, <a href="https://msdn.microsoft.com/2760579b-9922-4709-a049-a73f3abd5043">SetupDmaEngineWithBdl</a>, and <a href="https://msdn.microsoft.com/7aaf98cc-8a94-44e6-9fef-76e00db17405">FreeContiguousDmaBuffer</a> routines, which are never used in conjunction with <b>AllocateDmaBuffer</b> and <code>FreeDmaBuffer</code>. Unlike <b>SetupDmaEngineWithBdl</b>, which configures the DMA engine to use a previously allocated DMA buffer, <b>AllocateDmaBuffer</b> both allocates a DMA buffer and configures the DMA engine to use the buffer.</p>

<p>The routine fails and returns error code STATUS_INVALID_DEVICE_REQUEST in either of the following circumstances:</p>

<p>The client calls <code>FreeDmaBuffer</code> when no buffer is currently allocated for the DMA engine.</p>

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
<a href="https://msdn.microsoft.com/44fd988a-24b3-4587-88d9-30585800ffbf">AllocateDmaBuffer</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536413">HDAUDIO_BUS_INTERFACE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536418">HDAUDIO_BUS_INTERFACE_V2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/2760579b-9922-4709-a049-a73f3abd5043">SetupDmaEngineWithBdl</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [audio\audio]:%20PFREE_DMA_BUFFER callback function%20 RELEASE:%20(10/30/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>