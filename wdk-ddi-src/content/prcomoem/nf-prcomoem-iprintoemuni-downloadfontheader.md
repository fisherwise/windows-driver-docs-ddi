---
UID: NF.prcomoem.IPrintOemUni.DownloadFontHeader
title: IPrintOemUni::DownloadFontHeader
author: windows-driver-content
description: The IPrintOemUni::DownloadFontHeader method allows a rendering plug-in for Unidrv to send a font's header information to a printer.
old-location: print\iprintoemuni_downloadfontheader.htm
ms.assetid: 3d660d04-2872-44e6-ab76-719f5262bdd8
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
req.alt-api: IPrintOemUni.DownloadFontHeader
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
ms.keywords: IPrintOemUni, DownloadFontHeader, IPrintOemUni::DownloadFontHeader
req.iface: IPrintOemUni
req.product: Windows 10 or later.
---

# IPrintOemUni::DownloadFontHeader method



## -description
<p>The <code>IPrintOemUni::DownloadFontHeader</code> method allows a rendering plug-in for <a href="wdkgloss.u#wdkgloss.unidrv#wdkgloss.unidrv"><i>Unidrv</i></a> to send a font's header information to a printer.</p>


## -syntax

````
HRESULT DownloadFontHeader(
        PDEVOBJ     pdevobj,
        PUNIFONTOBJ pUFObj,
  [out] DWORD       *pdwResult
);
````


## -parameters
<dl>

### -param <i>pdevobj</i> 

<dd>
<p>Caller-supplied pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff547573">DEVOBJ</a> structure.</p>
</dd>

### -param <i>pUFObj</i> 

<dd>
<p>Caller-supplied pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff563590">UNIFONTOBJ</a> structure.</p>
</dd>

### -param <i>pdwResult</i> [out]

<dd>
<p>Receives a method-supplied value representing the amount of printer memory, in bytes, required to store the font header information. If the operation fails, the returned value should be zero.</p>
</dd>
</dl>

## -returns
<p>The method must return one of the following values.</p><dl>
<dt><b>S_OK</b></dt>
</dl><p>The operation succeeded.</p><dl>
<dt><b>E_FAIL</b></dt>
</dl><p>The operation failed</p><dl>
<dt><b>E_NOTIMPL</b></dt>
</dl><p>The method is not implemented.</p>

<p> </p>

## -remarks
<p>The <code>IPrintOemUni::DownloadFontHeader</code> method is used for supporting soft fonts on printers that do not accept <a href="wdkgloss.p#wdkgloss.pcl#wdkgloss.pcl"><i>PCL</i></a> commands. Its purpose is to allow a rendering plug-in to obtain font header information from Unidrv and to send the information to the printer.</p>

<p>Information that might be required for constructing a non-<a href="wdkgloss.p#wdkgloss.pcl#wdkgloss.pcl"><i>PCL</i></a> font header can be obtained by:</p>

<p>Referencing the <a href="https://msdn.microsoft.com/library/windows/hardware/ff563590">UNIFONTOBJ</a> structure that is received as an input argument.</p>

<p>Calling the <a href="https://msdn.microsoft.com/library/windows/hardware/ff563594">UNIFONTOBJ_GetInfo</a> callback function to get the font's <a href="https://msdn.microsoft.com/library/windows/hardware/ff565974">FONTOBJ</a> structure.</p>

<p>The method should send the header information to the spooler by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff553138">IPrintOemDriverUni::DrvWriteSpoolBuf</a>.</p>

<p>The <code>IPrintOemUni::DownloadFontHeader</code> method is optional. If a rendering plug-in implements this method, the plug-in's <a href="https://msdn.microsoft.com/library/windows/hardware/ff554253">IPrintOemUni::GetImplementedMethod</a> method must return S_OK when it receives "DownloadFontHeader" as input.</p>

<p>If you implement the <code>IPrintOemUni::DownloadFontHeader</code> method, you must also implement the <a href="https://msdn.microsoft.com/library/windows/hardware/ff554241">IPrintOemUni::DownloadCharGlyph</a> method.</p>

<p>For additional information see <a href="NULL">Customized Font Management</a>.</p>

<p>The <code>IPrintOemUni::DownloadFontHeader</code> method is used for supporting soft fonts on printers that do not accept <a href="wdkgloss.p#wdkgloss.pcl#wdkgloss.pcl"><i>PCL</i></a> commands. Its purpose is to allow a rendering plug-in to obtain font header information from Unidrv and to send the information to the printer.</p>

<p>Information that might be required for constructing a non-<a href="wdkgloss.p#wdkgloss.pcl#wdkgloss.pcl"><i>PCL</i></a> font header can be obtained by:</p>

<p>Referencing the <a href="https://msdn.microsoft.com/library/windows/hardware/ff563590">UNIFONTOBJ</a> structure that is received as an input argument.</p>

<p>Calling the <a href="https://msdn.microsoft.com/library/windows/hardware/ff563594">UNIFONTOBJ_GetInfo</a> callback function to get the font's <a href="https://msdn.microsoft.com/library/windows/hardware/ff565974">FONTOBJ</a> structure.</p>

<p>The method should send the header information to the spooler by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff553138">IPrintOemDriverUni::DrvWriteSpoolBuf</a>.</p>

<p>The <code>IPrintOemUni::DownloadFontHeader</code> method is optional. If a rendering plug-in implements this method, the plug-in's <a href="https://msdn.microsoft.com/library/windows/hardware/ff554253">IPrintOemUni::GetImplementedMethod</a> method must return S_OK when it receives "DownloadFontHeader" as input.</p>

<p>If you implement the <code>IPrintOemUni::DownloadFontHeader</code> method, you must also implement the <a href="https://msdn.microsoft.com/library/windows/hardware/ff554241">IPrintOemUni::DownloadCharGlyph</a> method.</p>

<p>For additional information see <a href="NULL">Customized Font Management</a>.</p>

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