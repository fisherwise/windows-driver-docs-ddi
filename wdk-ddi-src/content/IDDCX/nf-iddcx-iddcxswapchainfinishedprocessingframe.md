---
UID: NF.iddcx.IddCxSwapChainFinishedProcessingFrame
title: IddCxSwapChainFinishedProcessingFrame
author: windows-driver-content
description: An OS callback function the driver calls report all GPU command for processing this frame have been queue.
old-location: display\iddcxswapchainfinishedprocessingframe.htm
ms.assetid: 46c4a592-b3d4-479d-b5db-06202b5be290
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: display
req.header: iddcx.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IddCxSwapChainFinishedProcessingFrame
req.alt-loc: iddcx.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: _Must_inspect_result_
ms.keywords: IddCxSwapChainFinishedProcessingFrame
req.iface: 
---

# IddCxSwapChainFinishedProcessingFrame function



## -description
<p>

                An OS callback function the driver calls report all GPU command for processing this frame have been queue</p>


## -syntax

````
HRESULT IddCxSwapChainFinishedProcessingFrame(
  _In_ IDDCX_SWAPCHAIN SwapChainObject
);
````


## -parameters
<dl>

### -param <i>SwapChainObject</i> [in]

<dd>
<p>The swap-chain object whose current frame is being queried.</p>
</dd>
</dl>

## -returns
<p>
(NTSTATUS) The method returns STATUS_SUCCESS if the operation succeeds. Otherwise, this method may return an appropriate <a href="https://msdn.microsoft.com/7792201b-63bb-4db5-803d-2af02893d505">NTSTATUS</a> error code.
                    </p>

## -remarks
<p>If the driver copies the buffer to a staging surface so it can lock and copy the pixel data to the CPU, then the driver should call this callback once the copy from surface to staging surface has been submitted. If the driver does not call this callback the desktop will not update. It is invalid to call <a href="https://msdn.microsoft.com/library/windows/hardware/mt761929">IddCxSwapChainReleaseAndAcquireBuffer</a> before calling <b>IddCxSwapChainFinishedProcessingFrame</b></p>

<p>If the driver copies the buffer to a staging surface so it can lock and copy the pixel data to the CPU, then the driver should call this callback once the copy from surface to staging surface has been submitted. If the driver does not call this callback the desktop will not update. It is invalid to call <a href="https://msdn.microsoft.com/library/windows/hardware/mt761929">IddCxSwapChainReleaseAndAcquireBuffer</a> before calling <b>IddCxSwapChainFinishedProcessingFrame</b></p>

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
<dt>Iddcx.h</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>_Must_inspect_result_</p>
</td>
</tr>
</table>