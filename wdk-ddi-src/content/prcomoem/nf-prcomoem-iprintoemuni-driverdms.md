---
UID: NF.prcomoem.IPrintOemUni.DriverDMS
title: IPrintOemUni::DriverDMS
author: windows-driver-content
description: The IPrintOemUni::DriverDMS method allows a rendering plug-in for Unidrv to indicate that it uses a device-managed drawing surface.
old-location: print\iprintoemuni_driverdms.htm
ms.assetid: b62e6752-0804-41c4-84f4-49ad145acaf3
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: print
req.header: prcomoem.h
req.include-header: Prcomoem.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IPrintOemUni.DriverDMS
req.alt-loc: prcomoem.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: 
ms.keywords: IPrintOemUni, DriverDMS, IPrintOemUni::DriverDMS
req.iface: IPrintOemUni
req.product: Windows 10 or later.
---

# IPrintOemUni::DriverDMS method



## -description
<p>The <code>IPrintOemUni::DriverDMS</code> method allows a rendering plug-in for <a href="wdkgloss.u#wdkgloss.unidrv#wdkgloss.unidrv"><i>Unidrv</i></a> to indicate that it uses a device-managed drawing surface.</p>


## -syntax

````
HRESULT DriverDMS(
   PVOID  pDevObj,
   PVOID  pBuffer,
   DWORD  cbSize,
   PDWORD pcbNeeded
);
````


## -parameters
<dl>

### -param <i>pDevObj</i> 

<dd>
<p>Caller-supplied pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff547573">DEVOBJ</a> structure.</p>
</dd>

### -param <i>pBuffer</i> 

<dd>
<p>Caller-supplied pointer to a buffer to receive method-specified flags. (See the following Remarks section.)</p>
</dd>

### -param <i>cbSize</i> 

<dd>
<p>Caller-supplied size, in bytes, of the buffer pointed to by <i>pBuffer</i>.</p>
</dd>

### -param <i>pcbNeeded</i> 

<dd>
<p>Caller-supplied pointer to a location to receive the required minimum <i>pBuffer</i> size.</p>
</dd>
</dl>

## -returns
<p>The method must return one of the following values.</p><dl>
<dt><b>S_OK</b></dt>
</dl><p>The operation succeeded.</p><dl>
<dt><b>E_FAIL</b></dt>
</dl><p>The operation failed</p>

<p> </p>

## -remarks
<p>A rendering plug-in for Unidrv must implement the <code>IPrintOemUni::DriverDMS</code> method. The method will be called only if Unidrv finds a valid interface pointer to the OEM's rendering plug-in.</p>

<p>The <code>IPrintOemUni::DriverDMS</code> method allows a rendering plug-in to indicate that it will be using a device-managed drawing surface instead of the default GDI-managed surface.</p>

<p>The method must specify HOOK_-prefixed flags in the buffer pointed to by <i>pBuffer</i>, indicating which of the plug-in's graphics DDI hooking functions are to be called for the drawing surface. The HOOK_-prefixed flags are defined in winddi.h and described in the <a href="https://msdn.microsoft.com/library/windows/hardware/ff564183">EngAssociateSurface</a> function's description. Flags specified by <code>IPrintOemUni::DriverDMS</code> are passed by Unidrv to <b>EngAssociateSurface</b>. (Note that to support a device-managed surface, the rendering plug-in must hook out all drawing functions.) For more information, see <a href="NULL">Handling Device-Managed Surfaces</a>.</p>

<p>If <code>IPrintOemUni::DriverDMS</code> sets flags in the buffer pointed to by <i>pBuffer</i>, Unidrv creates a device-managed surface by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff564206">EngCreateDeviceSurface</a>. If <code>IPrintOemUni::DriverDMS</code> does not set any flags, Unidrv creates a GDI-managed surface by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff564199">EngCreateBitmap</a>. In either of these cases, <code>IPrintOemUni::DriverDMS</code> should return S_OK.</p>

<p>If the output buffer size specified by <i>cbSize</i> is too small, the method should specify the required size in the location pointed to by <i>pcbNeeded</i>, call <b>SetLastError</b>(ERROR_INSUFFICIENT_BUFFER), and return E_FAIL.</p>

<p>A rendering plug-in for Unidrv must implement the <code>IPrintOemUni::DriverDMS</code> method. The method will be called only if Unidrv finds a valid interface pointer to the OEM's rendering plug-in.</p>

<p>The <code>IPrintOemUni::DriverDMS</code> method allows a rendering plug-in to indicate that it will be using a device-managed drawing surface instead of the default GDI-managed surface.</p>

<p>The method must specify HOOK_-prefixed flags in the buffer pointed to by <i>pBuffer</i>, indicating which of the plug-in's graphics DDI hooking functions are to be called for the drawing surface. The HOOK_-prefixed flags are defined in winddi.h and described in the <a href="https://msdn.microsoft.com/library/windows/hardware/ff564183">EngAssociateSurface</a> function's description. Flags specified by <code>IPrintOemUni::DriverDMS</code> are passed by Unidrv to <b>EngAssociateSurface</b>. (Note that to support a device-managed surface, the rendering plug-in must hook out all drawing functions.) For more information, see <a href="NULL">Handling Device-Managed Surfaces</a>.</p>

<p>If <code>IPrintOemUni::DriverDMS</code> sets flags in the buffer pointed to by <i>pBuffer</i>, Unidrv creates a device-managed surface by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff564206">EngCreateDeviceSurface</a>. If <code>IPrintOemUni::DriverDMS</code> does not set any flags, Unidrv creates a GDI-managed surface by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff564199">EngCreateBitmap</a>. In either of these cases, <code>IPrintOemUni::DriverDMS</code> should return S_OK.</p>

<p>If the output buffer size specified by <i>cbSize</i> is too small, the method should specify the required size in the location pointed to by <i>pcbNeeded</i>, call <b>SetLastError</b>(ERROR_INSUFFICIENT_BUFFER), and return E_FAIL.</p>

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
<dt>Prcomoem.h (include Prcomoem.h)</dt>
</dl>
</td>
</tr>
</table>