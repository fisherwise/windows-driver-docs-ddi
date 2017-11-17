---
UID: NC.d3dkmddi.DXGKDDI_CONTROLINTERRUPT2
title: DXGKDDI_CONTROLINTERRUPT2
author: windows-driver-content
description: The DxgkDdi_ControlInterrupt2 function enables or disables the given interrupt type on the graphics hardware.
old-location: display\dxgkddicontrolinterrupt2.htm
ms.assetid: 0C09CAB1-3DFC-4340-8FF2-99CAF7F13156
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmddi.h
req.include-header: D3dkmddi.h
req.target-type: Desktop
req.target-min-winverclnt: Available in Windows 10 and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DxgkDdi_ControlInterrupt2
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
ms.keywords: DD_MULTISAMPLEQUALITYLEVELSDATA, DD_MULTISAMPLEQUALITYLEVELSDATA
req.iface: 
---

# DXGKDDI_CONTROLINTERRUPT2 callback



## -description
<p>The <i>DxgkDdi_ControlInterrupt2</i> function enables or disables the given interrupt type on the graphics hardware.</p>


## -prototype

````
DXGKDDI_CONTROLINTERRUPT2 DxgkDdi_ControlInterrupt2;

NTSTATUS APIENTRY* DxgkDdi_ControlInterrupt2(
  _In_ const HANDLE                    hAdapter,
  _In_ const DXGKARG_CONTROLINTERRUPT2 InterruptControl
)
{ ... }
````


## -parameters
<dl>

### -param <i>hAdapter</i> [in]

<dd>
<p>[in] A handle to the adapter object for the graphics processing unit (GPU). The driver returned this handle in the <i>MiniportDeviceContext</i> parameter from a call to its <a href="https://msdn.microsoft.com/5fd4046f-54c3-4dfc-8d51-0d9ebcde0bea">DxgkDdiAddDevice</a> function.</p>
</dd>

### -param <i>InterruptControl</i> [in]

<dd>
<p>[in] A <a href="https://msdn.microsoft.com/library/windows/hardware/mt654042">DXGKARG_CONTROLINTERRUPT2</a>-type value that supplies the interrupt type, as well as the VSYNC state.</p>
</dd>
</dl>

## -returns
<p><i>DxgkDdi_ControlInterrupt2</i> returns one of the following values:</p><dl>
<dt><b>STATUS_SUCCESS</b></dt>
</dl><p>The interrupt type was successfully enabled or disabled on the graphics hardware.</p><dl>
<dt><b>STATUS_NOT_IMPLEMENTED</b></dt>
</dl><p>
<a href="https://msdn.microsoft.com/library/windows/hardware/mt667971">DxgkDdi_ControlInterrupt2</a> does not support enabling or disabling the specified interrupt type.</p>

<p> </p>

## -remarks


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
<p>Available in Windows 10 and later versions of the Windows operating systems.</p>
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
<p>PASSIVE_LEVEL</p>
</td>
</tr>
</table>