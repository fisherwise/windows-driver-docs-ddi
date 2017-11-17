---
UID: NF.srb.ScsiPortFlushDma
title: ScsiPortFlushDma
author: windows-driver-content
description: The ScsiPortFlushDma routine flushes any data cached in the system DMA controller at the end of a transfer or terminates a system DMA transfer.Note  The SCSI port driver and SCSI miniport driver models may be altered or unavailable in the future.
old-location: storage\scsiportflushdma.htm
ms.assetid: 9cf4286b-1ff7-4113-a2dc-d8813c633dd6
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: Storage
req.header: srb.h
req.include-header: Miniport.h, Scsi.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: ScsiPortFlushDma
req.alt-loc: Scsiport.lib,Scsiport.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Scsiport.lib
req.dll: 
req.irql: 
ms.keywords: ScsiPortFlushDma
req.iface: 
req.product: Windows 10 or later.
---

# ScsiPortFlushDma function



## -description
<p>The <b>ScsiPortFlushDma</b> routine flushes any data cached in the system DMA controller at the end of a transfer or terminates a system DMA transfer.</p>


## -syntax

````
VOID ScsiPortFlushDma(
  _In_ PVOID DeviceExtension
);
````


## -parameters
<dl>

### -param <i>DeviceExtension</i> [in]

<dd>
<p>Pointer to the miniport driver's per-HBA storage area.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>Only miniport drivers of subordinate HBAs that use a system DMA controller call this routine.</p>

<p><b>ScsiPortFlushDma</b> must be called after a subordinate DMA transfer operation is completed but before the SRB is completed or the next call is made to <a href="https://msdn.microsoft.com/library/windows/hardware/ff564649">ScsiPortIoMapTransfer</a> for the current buffer.</p>

<p><b>ScsiPortFlushDma</b> also must be called after <b>ScsiPortIoMapTransfer</b> to cancel a DMA operation, even if no transfer has occurred and the driver's <a href="https://msdn.microsoft.com/library/windows/hardware/ff557291">HwScsiDmaStarted</a> routine has not yet been called.</p>

<p>Only miniport drivers of subordinate HBAs that use a system DMA controller call this routine.</p>

<p><b>ScsiPortFlushDma</b> must be called after a subordinate DMA transfer operation is completed but before the SRB is completed or the next call is made to <a href="https://msdn.microsoft.com/library/windows/hardware/ff564649">ScsiPortIoMapTransfer</a> for the current buffer.</p>

<p><b>ScsiPortFlushDma</b> also must be called after <b>ScsiPortIoMapTransfer</b> to cancel a DMA operation, even if no transfer has occurred and the driver's <a href="https://msdn.microsoft.com/library/windows/hardware/ff557291">HwScsiDmaStarted</a> routine has not yet been called.</p>

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
<dt>Srb.h (include Miniport.h or Scsi.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Scsiport.lib</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff557291">HwScsiDmaStarted</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564649">ScsiPortIoMapTransfer</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20ScsiPortFlushDma routine%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>