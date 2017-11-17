---
UID: NF.prcomoem.IPrintOemDriverUni.DrvGetStandardVariable
title: IPrintOemDriverUni::DrvGetStandardVariable
author: windows-driver-content
description: The IPrintOemDriverUni::DrvGetStandardVariable method is provided by the Unidrv driver so that rendering plug-ins can obtain the current value of Unidrv's standard variables.
old-location: print\iprintoemdriveruni_drvgetstandardvariable.htm
ms.assetid: d55d3130-14e7-438f-bfb5-18927466bd60
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
req.alt-api: IPrintOemDriverUni.DrvGetStandardVariable
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
ms.keywords: IPrintOemDriverUni, DrvGetStandardVariable, IPrintOemDriverUni::DrvGetStandardVariable
req.iface: IPrintOemDriverUni
req.product: Windows 10 or later.
---

# IPrintOemDriverUni::DrvGetStandardVariable method



## -description
<p>The <code>IPrintOemDriverUni::DrvGetStandardVariable</code> method is provided by the Unidrv driver so that rendering plug-ins can obtain the current value of Unidrv's <a href="NULL">standard variables</a>.</p>


## -syntax

````
HRESULT DrvGetStandardVariable(
   PDEVOBJ pdevobj,
   DWORD   dwIndex,
   PVOID   pBuffer,
   DWORD   cbSize,
   PDWORD  pcbNeeded
);
````


## -parameters
<dl>

### -param <i>pdevobj</i> 

<dd>
<p>Caller-supplied pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff547573">DEVOBJ</a> structure.</p>
</dd>

### -param <i>dwIndex</i> 

<dd>
<p>Caller-supplied, SVI_-prefixed index into the list of Unidrv's standard variables. The SVI_-prefixed index values are defined in printoem.h.</p>
</dd>

### -param <i>pBuffer</i> 

<dd>
<p>Caller-supplied pointer to a DWORD to receive the standard variable's current value.</p>
</dd>

### -param <i>cbSize</i> 

<dd>
<p>Caller-supplied size of the buffer pointed to by <i>pBuffer</i>.</p>
</dd>

### -param <i>pcbNeeded</i> 

<dd>
<p>Caller-supplied pointer to a location to receive the minimum buffer size required to contain the requested information.</p>
</dd>
</dl>

## -returns
<p>The method must return one of the following values.</p><dl>
<dt><b>S_OK</b></dt>
</dl><p>The operation succeeded.</p><dl>
<dt><b>E_FAIL</b></dt>
</dl><p>The operation failed.</p><dl>
<dt><b>E_NOTIMPL</b></dt>
</dl><p>The method is not implemented.</p>

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
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Prcomoem.h (include Prcomoem.h)</dt>
</dl>
</td>
</tr>
</table>