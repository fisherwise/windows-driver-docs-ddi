---
UID: NF.wdfdpc.WdfDpcGetParentObject
title: WdfDpcGetParentObject
author: windows-driver-content
description: The WdfDpcGetParentObject method returns the parent object of a specified DPC object.
old-location: wdf\wdfdpcgetparentobject.htm
ms.assetid: 77ebca0f-3056-4f11-9d59-fbd166967ed3
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: wdf
req.header: wdfdpc.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 
req.alt-api: WdfDpcGetParentObject
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
req.irql: Any level
ms.keywords: WdfDpcGetParentObject
req.iface: 
req.product: Windows 10 or later.
---

# WdfDpcGetParentObject function



## -description
<p class="CCE_Message">[Applies to KMDF only]</p>
<p>The <b>WdfDpcGetParentObject</b> method returns the parent object of a specified DPC object.</p>


## -syntax

````
WDFOBJECT WdfDpcGetParentObject(
  _In_ WDFDPC Dpc
);
````


## -parameters
<dl>

### -param <i>Dpc</i> [in]

<dd>
<p>A handle to a framework DPC object.</p>
</dd>
</dl>

## -returns
<p><b>WdfDpcGetParentObject</b> returns a handle to the parent object of a specified DPC object.</p>

<p>A bug check occurs if the driver supplies an invalid object handle.

</p>

## -remarks
<p>A driver might call <b>WdfDpcGetParentObject</b> from within its <a href="https://msdn.microsoft.com/b934a0da-0709-4427-bbf2-8d53f9511cf1">EvtDpcFunc</a> callback function.</p>

<p>The following code example returns a handle to the parent object of a specified DPC object. The <a href="https://msdn.microsoft.com/library/windows/hardware/ff547140">WdfDpcCreate</a> code example shows how the specified DPC object was created.</p>

<p>A driver might call <b>WdfDpcGetParentObject</b> from within its <a href="https://msdn.microsoft.com/b934a0da-0709-4427-bbf2-8d53f9511cf1">EvtDpcFunc</a> callback function.</p>

<p>The following code example returns a handle to the parent object of a specified DPC object. The <a href="https://msdn.microsoft.com/library/windows/hardware/ff547140">WdfDpcCreate</a> code example shows how the specified DPC object was created.</p>

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
<dt>Wdfdpc.h (include Wdf.h)</dt>
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
<p>Any level</p>
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
<a href="https://msdn.microsoft.com/b934a0da-0709-4427-bbf2-8d53f9511cf1">EvtDpcFunc</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WdfDpcGetParentObject method%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>