---
UID: NS.d3dkmddi._DXGKARG_PREEMPTCOMMAND
title: DXGKARG_PREEMPTCOMMAND
author: windows-driver-content
description: The DXGKARG_PREEMPTCOMMAND structure describes a command that a display miniport driver must use to preempt a direct memory access (DMA) buffer that the DxgkDdiSubmitCommand function previously submitted to the hardware command execution unit.
old-location: display\dxgkarg_preemptcommand.htm
ms.assetid: de8f8bee-44e9-4a6a-bb36-a43a66afe188
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
req.alt-api: DXGKARG_PREEMPTCOMMAND
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
ms.keywords: DXGKARG_PREEMPTCOMMAND, DXGKARG_PREEMPTCOMMAND
req.iface: 
---

# DXGKARG_PREEMPTCOMMAND structure



## -description
<p>The DXGKARG_PREEMPTCOMMAND structure describes a command that a display miniport driver must use to preempt a direct memory access (DMA) buffer that the <a href="https://msdn.microsoft.com/de1925ab-e444-4cf6-acd9-8fdab26afcec">DxgkDdiSubmitCommand</a> function previously submitted to the hardware command execution unit.</p>


## -syntax

````
typedef struct _DXGKARG_PREEMPTCOMMAND {
  UINT                     PreemptionFenceId;
  UINT                     NodeOrdinal;
  UINT                     EngineOrdinal;
  DXGK_PREEMPTCOMMANDFLAGS Flags;
} DXGKARG_PREEMPTCOMMAND;
````


## -struct-fields
<dl>

### -field <b>PreemptionFenceId</b>

<dd>
<p>[in] A unique identifier that the display miniport driver must patch into the fence command at the end of the DMA buffer to preempt the previously submitted DMA buffer. The display miniport driver uses the identifier in a call to the <a href="https://msdn.microsoft.com/3df3f7d4-3721-46f5-b9e3-19bd3d870292">DxgkCbNotifyDpc</a> function to inform the graphics processing unit (GPU) scheduler about the preemption at deferred-procedure-call (DPC) time.</p>
</dd>

### -field <b>NodeOrdinal</b>

<dd>
<p>[in] The index of the node for the preemption request. </p>
</dd>

### -field <b>EngineOrdinal</b>

<dd>
<p>[in] The index of the engine for the preemption request.</p>
</dd>

### -field <b>Flags</b>

<dd>
<p>[in] A <a href="https://msdn.microsoft.com/library/windows/hardware/ff561997">DXGK_PREEMPTCOMMANDFLAGS</a> structure with a reserved member or a 32-bit value. No flags are currently defined for this structure.</p>
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
<dt>D3dkmddi.h (include D3dkmddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561997">DXGK_PREEMPTCOMMANDFLAGS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/3df3f7d4-3721-46f5-b9e3-19bd3d870292">DxgkCbNotifyDpc</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/7968d26d-0195-463d-8954-e7ebef4f9dea">DxgkCbNotifyInterrupt</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/a7027735-0ec4-4fad-81fb-1c3aca4ebf2d">DxgkDdiCreateDevice</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/de1925ab-e444-4cf6-acd9-8fdab26afcec">DxgkDdiSubmitCommand</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/8cea02d4-f25e-4ff4-8c9e-aa360a764c4b">DxgkDdiPreemptCommand</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20DXGKARG_PREEMPTCOMMAND structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>