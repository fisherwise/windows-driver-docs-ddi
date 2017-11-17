---
UID: NF.wdfhwaccess.WDF_READ_PORT_USHORT
title: WDF_READ_PORT_USHORT
author: windows-driver-content
description: The WDF_READ_PORT_USHORT function reads a USHORT value from the specified port address.
old-location: wdf\wdf_read_port_ushort.htm
ms.assetid: F9688E1F-D8A3-432E-8724-2D601946E707
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: wdf
req.header: wdfhwaccess.h
req.include-header: 
req.target-type: Universal
req.target-min-winverclnt: Windows 8.1
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 2.0
req.alt-api: WDF_READ_PORT_USHORT
req.alt-loc: Wdfhwaccess.h
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
ms.keywords: WDF_READ_PORT_USHORT
req.iface: 
req.product: Windows 10 or later.
---

# WDF_READ_PORT_USHORT function



## -description
<p class="CCE_Message">[Applies to UMDF only]</p>
<p>The <b>WDF_READ_PORT_USHORT</b>  function reads a USHORT value from the specified port address.</p>


## -syntax

````
USHORT WDF_READ_PORT_USHORT(
  _In_ WDFDEVICE Device,
  _In_ PUSHORT   Port
);
````


## -parameters
<dl>

### -param <i>Device</i> [in]

<dd>
<p>A handle to a framework device object.</p>
</dd>

### -param <i>Port</i> [in]

<dd>
<p>Specifies the port address, which must be a mapped memory range in I/O space.</p>
</dd>
</dl>

## -returns
<p><b>WDF_READ_PORT_USHORT</b> returns the USHORT value that is read from the specified port address.</p>

## -remarks


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
<p>Minimum support</p>
</th>
<td width="70%">
<p>Windows 8.1</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum UMDF version</p>
</th>
<td width="70%">
<p>2.0</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdfhwaccess.h</dt>
</dl>
</td>
</tr>
</table>