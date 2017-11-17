---
UID: NC.d3dkmddi.DXGKCB_NOTIFY_INTERRUPT
title: DXGKCB_NOTIFY_INTERRUPT
author: windows-driver-content
description: The DxgkCbNotifyInterrupt function informs the graphics processing unit (GPU) scheduler about a graphics hardware update at interrupt-service-routine (ISR) time.
old-location: display\dxgkcbnotifyinterrupt.htm
ms.assetid: 7968d26d-0195-463d-8954-e7ebef4f9dea
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmddi.h
req.include-header: D3dkmddi.h
req.target-type: Desktop
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DxgkCbNotifyInterrupt
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
req.irql: See Remarks section.
ms.keywords: DD_MULTISAMPLEQUALITYLEVELSDATA, DD_MULTISAMPLEQUALITYLEVELSDATA
req.iface: 
---

# DXGKCB_NOTIFY_INTERRUPT callback



## -description
<p>The <b>DxgkCbNotifyInterrupt</b> function informs the graphics processing unit (GPU) scheduler about a graphics hardware update at interrupt-service-routine (ISR) time.</p>


## -prototype

````
DXGKCB_NOTIFY_INTERRUPT DxgkCbNotifyInterrupt;

VOID APIENTRY DxgkCbNotifyInterrupt(
  _In_    const HANDLE                          hAdapter,
  _Inout_ const DXGKARGCB_NOTIFY_INTERRUPT_DATA *pData
)
{ ... }
````


## -parameters
<dl>

### -param <i>hAdapter</i> [in]

<dd>
<p>[in] A handle to the adapter object for the GPU. A driver receives the handle from the <b>DeviceHandle</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff560942">DXGKRNL_INTERFACE</a> structure in a call to its <a href="https://msdn.microsoft.com/ffacbb39-2581-4207-841d-28ce57fbc64d">DxgkDdiStartDevice</a> function.</p>
</dd>

### -param <i>pData</i> [in, out]

<dd>
<p>[in] A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff557538">DXGKARGCB_NOTIFY_INTERRUPT_DATA</a> structure that describes notification information.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>A display miniport driver calls the <b>DxgkCbNotifyInterrupt</b> function to report a graphics hardware interrupt that the <a href="https://msdn.microsoft.com/library/windows/hardware/ff561136">DXGK_INTERRUPT_TYPE</a> enumeration type defines. Typically, <b>DxgkCbNotifyInterrupt</b> is called from the display miniport driver's <a href="https://msdn.microsoft.com/eacfd42d-405c-4c23-8978-0f373a393e10">DxgkDdiInterruptRoutine</a> function (ISR), which is called when graphics hardware interrupts occur. The <b>DxgkCbNotifyInterrupt</b> function informs the GPU scheduler about an update to a fence through a direct memory access (DMA) stream to the graphics hardware. </p>

<p>If the display miniport driver uses multiple interrupt handlers that correspond to multiple IRQLs, the driver must not call <b>DxgkCbNotifyInterrupt</b> in a reentrant fashion. Therefore, in this case, the display miniport driver should always call <b>DxgkCbNotifyInterrupt</b> from a fixed level of the interrupt handler. </p>

<p>Similarly, if message-signaled interrupts are used, the display miniport driver can call <b>DxgkCbNotifyInterrupt</b> from an interrupt handler that corresponds to a fixed message number. The driver must report the message number that is used for notification in the <b>InterruptMessageNumber</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff561062">DXGK_DRIVERCAPS</a> structure, when the DXGKQAITYPE_DRIVERCAPS enumeration value is specified in the <b>Type</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff557621">DXGKARG_QUERYADAPTERINFO</a> structure in a call to the driver's <a href="https://msdn.microsoft.com/f2f4c54c-7413-48e5-a165-d71f35642b6c">DxgkDdiQueryAdapterInfo</a> function.</p>

<p>After the display miniport driver calls <b>DxgkCbNotifyInterrupt</b> but before the driver exits its ISR, the driver must queue a deferred procedure call (DPC) by using the <a href="https://msdn.microsoft.com/c8c26675-8b87-4818-ad51-4e0a341965d0">DxgkCbQueueDpc</a> function. This DPC must be queued because the GPU scheduler must also be notified, when the driver's DPC callback routine calls the <a href="https://msdn.microsoft.com/3df3f7d4-3721-46f5-b9e3-19bd3d870292">DxgkCbNotifyDpc</a> function, about the same event at DPC time. A certain amount of processing that is related to graphics hardware events can be only performed by the operating system at DPC time. </p>

<p>If the display miniport driver determines that more than one interrupt was triggered in hardware and the driver must call <b>DxgkCbNotifyInterrupt</b> for each interrupt to report the interrupt to the operating system, the driver should report DMA-type interrupts before a CRTC-type interrupt. For more information about interrupt types, see the <a href="https://msdn.microsoft.com/library/windows/hardware/ff561136">DXGK_INTERRUPT_TYPE</a> reference page.</p>

<p>Callers of <b>DxgkCbNotifyInterrupt</b> run at interrupt level (that is, DIRQL, which is some IRQL between DISPATCH_LEVEL and PROFILE_LEVEL, not inclusive).</p>

<p>The following code example shows software engine code that monitors a software queue and notifies the GPU scheduler about packet completion.</p>

<p>A display miniport driver calls the <b>DxgkCbNotifyInterrupt</b> function to report a graphics hardware interrupt that the <a href="https://msdn.microsoft.com/library/windows/hardware/ff561136">DXGK_INTERRUPT_TYPE</a> enumeration type defines. Typically, <b>DxgkCbNotifyInterrupt</b> is called from the display miniport driver's <a href="https://msdn.microsoft.com/eacfd42d-405c-4c23-8978-0f373a393e10">DxgkDdiInterruptRoutine</a> function (ISR), which is called when graphics hardware interrupts occur. The <b>DxgkCbNotifyInterrupt</b> function informs the GPU scheduler about an update to a fence through a direct memory access (DMA) stream to the graphics hardware. </p>

<p>If the display miniport driver uses multiple interrupt handlers that correspond to multiple IRQLs, the driver must not call <b>DxgkCbNotifyInterrupt</b> in a reentrant fashion. Therefore, in this case, the display miniport driver should always call <b>DxgkCbNotifyInterrupt</b> from a fixed level of the interrupt handler. </p>

<p>Similarly, if message-signaled interrupts are used, the display miniport driver can call <b>DxgkCbNotifyInterrupt</b> from an interrupt handler that corresponds to a fixed message number. The driver must report the message number that is used for notification in the <b>InterruptMessageNumber</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff561062">DXGK_DRIVERCAPS</a> structure, when the DXGKQAITYPE_DRIVERCAPS enumeration value is specified in the <b>Type</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff557621">DXGKARG_QUERYADAPTERINFO</a> structure in a call to the driver's <a href="https://msdn.microsoft.com/f2f4c54c-7413-48e5-a165-d71f35642b6c">DxgkDdiQueryAdapterInfo</a> function.</p>

<p>After the display miniport driver calls <b>DxgkCbNotifyInterrupt</b> but before the driver exits its ISR, the driver must queue a deferred procedure call (DPC) by using the <a href="https://msdn.microsoft.com/c8c26675-8b87-4818-ad51-4e0a341965d0">DxgkCbQueueDpc</a> function. This DPC must be queued because the GPU scheduler must also be notified, when the driver's DPC callback routine calls the <a href="https://msdn.microsoft.com/3df3f7d4-3721-46f5-b9e3-19bd3d870292">DxgkCbNotifyDpc</a> function, about the same event at DPC time. A certain amount of processing that is related to graphics hardware events can be only performed by the operating system at DPC time. </p>

<p>If the display miniport driver determines that more than one interrupt was triggered in hardware and the driver must call <b>DxgkCbNotifyInterrupt</b> for each interrupt to report the interrupt to the operating system, the driver should report DMA-type interrupts before a CRTC-type interrupt. For more information about interrupt types, see the <a href="https://msdn.microsoft.com/library/windows/hardware/ff561136">DXGK_INTERRUPT_TYPE</a> reference page.</p>

<p>Callers of <b>DxgkCbNotifyInterrupt</b> run at interrupt level (that is, DIRQL, which is some IRQL between DISPATCH_LEVEL and PROFILE_LEVEL, not inclusive).</p>

<p>The following code example shows software engine code that monitors a software queue and notifies the GPU scheduler about packet completion.</p>

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
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>See Remarks section.</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561136">DXGK_INTERRUPT_TYPE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff557621">DXGKARG_QUERYADAPTERINFO</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff557538">DXGKARGCB_NOTIFY_INTERRUPT_DATA</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/3df3f7d4-3721-46f5-b9e3-19bd3d870292">DxgkCbNotifyDpc</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/c8c26675-8b87-4818-ad51-4e0a341965d0">DxgkCbQueueDpc</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/eacfd42d-405c-4c23-8978-0f373a393e10">DxgkDdiInterruptRoutine</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/f2f4c54c-7413-48e5-a165-d71f35642b6c">DxgkDdiQueryAdapterInfo</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/ffacbb39-2581-4207-841d-28ce57fbc64d">DxgkDdiStartDevice</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff560942">DXGKRNL_INTERFACE</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20DXGKCB_NOTIFY_INTERRUPT callback function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>