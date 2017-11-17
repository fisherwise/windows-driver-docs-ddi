---
UID: NF.wdfdmatransaction.WdfDmaTransactionDmaCompletedFinal
title: WdfDmaTransactionDmaCompletedFinal
author: windows-driver-content
description: The WdfDmaTransactionDmaCompletedFinal method notifies the framework that a device's DMA transfer operation has completed with an underrun condition and supplies the length of the completed transfer.
old-location: wdf\wdfdmatransactiondmacompletedfinal.htm
ms.assetid: de16eaf4-11f0-428b-8833-1d1e6ef78853
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: wdf
req.header: wdfdmatransaction.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 
req.alt-api: WdfDmaTransactionDmaCompletedFinal
req.alt-loc: Wdf01000.sys,Wdf01000.sys.dll
req.ddi-compliance: DriverCreate, KmdfIrql, KmdfIrql2
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Wdf01000.sys (see Framework Library Versioning.)
req.dll: 
req.irql: <=DISPATCH_LEVEL
ms.keywords: WdfDmaTransactionDmaCompletedFinal
req.iface: 
req.product: Windows 10 or later.
---

# WdfDmaTransactionDmaCompletedFinal function



## -description
<p class="CCE_Message">[Applies to KMDF only]</p>
<p>The <b>WdfDmaTransactionDmaCompletedFinal</b> method notifies the framework that a device's DMA transfer operation has completed with an underrun condition and supplies the length of the completed transfer. </p>


## -syntax

````
BOOLEAN WdfDmaTransactionDmaCompletedFinal(
  _In_  WDFDMATRANSACTION DmaTransaction,
  _In_  size_t            FinalTransferredLength,
  _Out_ NTSTATUS          *Status
);
````


## -parameters
<dl>

### -param <i>DmaTransaction</i> [in]

<dd>
<p>A handle to a DMA transaction object that the driver obtained from a previous call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff547027">WdfDmaTransactionCreate</a>.</p>
</dd>

### -param <i>FinalTransferredLength</i> [in]

<dd>
<p>The number of bytes that the device transferred.</p>
</dd>

### -param <i>Status</i> [out]

<dd>
<p>A pointer to a location that receives the status of the DMA transfer. For more information, see the Remarks section for <a href="https://msdn.microsoft.com/library/windows/hardware/ff547039">WdfDmaTransactionDmaCompleted</a>.</p>
</dd>
</dl>

## -returns
<p><b>WdfDmaTransactionDmaCompletedFinal</b> returns <b>FALSE</b> if the driver supplies an invalid input parameter. Otherwise, <b>WdfDmaTransactionDmaCompletedFinal</b> always returns <b>TRUE</b>, which indicates that the framework will not attempt to transfer any more bytes for the DMA transaction that the <i>DmaTransaction</i> parameter specified. </p>

<p>A bug check occurs if the driver supplies an invalid object handle.

</p>

## -remarks
<p>A driver typically calls <b>WdfDmaTransactionDmaCompletedFinal</b> from within its <a href="https://msdn.microsoft.com/d2d505e0-aeac-4871-8c60-d026b2833043">EvtInterruptDpc</a> callback. A driver for a system-mode DMA device might call <b>WdfDmaTransactionDmaCompletedFinal</b> from within an <a href="https://msdn.microsoft.com/C638A505-AAE1-48FC-B06B-F2F161ADC948">EvtDmaTransactionDmaTransferComplete</a> event callback function.</p>

<p>In the  <a href="http://go.microsoft.com/fwlink/p/?linkid=256157">PLX9x5x</a> sample, the driver calls  <b>WdfDmaTransactionDmaCompletedFinal</b> from its <a href="https://msdn.microsoft.com/c01b94b2-aabf-47dd-952a-06e481579614">EvtProgramDma</a> callback function.</p>

<p>The <b>WdfDmaTransactionDmaCompletedFinal</b> method behaves the same as <a href="https://msdn.microsoft.com/library/windows/hardware/ff547039">WdfDmaTransactionDmaCompleted</a>, except that drivers typically call <b>WdfDmaTransactionDmaCompletedFinal</b> if the hardware reports an underrun condition. An underrun condition means that the hardware could not transfer all of the bytes that were specified for the last DMA transfer. A call to <b>WdfDmaTransactionDmaCompletedFinal</b> stops the framework from starting any more DMA transfers for the specified DMA transaction.</p>

<p>When your driver calls <b>WdfDmaTransactionDmaCompletedFinal</b>, the driver supplies the number of bytes that were transferred. The return value is always <b>TRUE</b>, because the framework will not attempt to transfer any more bytes for the specified transaction. </p>

<p>For more information about completing DMA transfers, see <a href="NULL">Completing a DMA Transfer</a>. </p>

<p>The following code example notifies the framework that a device's DMA transfer operation has completed with an underrun condition.</p>

<p>A driver typically calls <b>WdfDmaTransactionDmaCompletedFinal</b> from within its <a href="https://msdn.microsoft.com/d2d505e0-aeac-4871-8c60-d026b2833043">EvtInterruptDpc</a> callback. A driver for a system-mode DMA device might call <b>WdfDmaTransactionDmaCompletedFinal</b> from within an <a href="https://msdn.microsoft.com/C638A505-AAE1-48FC-B06B-F2F161ADC948">EvtDmaTransactionDmaTransferComplete</a> event callback function.</p>

<p>In the  <a href="http://go.microsoft.com/fwlink/p/?linkid=256157">PLX9x5x</a> sample, the driver calls  <b>WdfDmaTransactionDmaCompletedFinal</b> from its <a href="https://msdn.microsoft.com/c01b94b2-aabf-47dd-952a-06e481579614">EvtProgramDma</a> callback function.</p>

<p>The <b>WdfDmaTransactionDmaCompletedFinal</b> method behaves the same as <a href="https://msdn.microsoft.com/library/windows/hardware/ff547039">WdfDmaTransactionDmaCompleted</a>, except that drivers typically call <b>WdfDmaTransactionDmaCompletedFinal</b> if the hardware reports an underrun condition. An underrun condition means that the hardware could not transfer all of the bytes that were specified for the last DMA transfer. A call to <b>WdfDmaTransactionDmaCompletedFinal</b> stops the framework from starting any more DMA transfers for the specified DMA transaction.</p>

<p>When your driver calls <b>WdfDmaTransactionDmaCompletedFinal</b>, the driver supplies the number of bytes that were transferred. The return value is always <b>TRUE</b>, because the framework will not attempt to transfer any more bytes for the specified transaction. </p>

<p>For more information about completing DMA transfers, see <a href="NULL">Completing a DMA Transfer</a>. </p>

<p>The following code example notifies the framework that a device's DMA transfer operation has completed with an underrun condition.</p>

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
<p>Minimum KMDF version</p>
</th>
<td width="70%">
<p>1.0</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdfdmatransaction.h (include Wdf.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Wdf01000.sys (see <a href="wdf.framework_library_versioning">Framework Library Versioning</a>.)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&lt;=DISPATCH_LEVEL</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544957">DriverCreate</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff548167">KmdfIrql</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975091">KmdfIrql2</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547027">WdfDmaTransactionCreate</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547039">WdfDmaTransactionDmaCompleted</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547052">WdfDmaTransactionDmaCompletedWithLength</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WdfDmaTransactionDmaCompletedFinal method%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>