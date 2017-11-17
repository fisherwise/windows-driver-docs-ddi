---
UID: NF.winppi.GdiEndPageEMF
title: GdiEndPageEMF
author: windows-driver-content
description: The GdiEndPageEMF function ends EMF playback operations for a physical page of an EMF-formatted print job.
old-location: print\gdiendpageemf.htm
ms.assetid: e15344a5-32ed-43a8-93c2-d5201617d595
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: print
req.header: winppi.h
req.include-header: Winppi.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: GdiEndPageEMF
req.alt-loc: Gdi32.dll,Ext-MS-Win-GDI-Internal-Desktop-L1-1-0.dll,GDI32Full.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Gdi32.Lib
req.dll: Gdi32.dll
req.irql: 
ms.keywords: GdiEndPageEMF
req.iface: 
req.product: Windows 10 or later.
---

# GdiEndPageEMF function



## -description
<p>The <b>GdiEndPageEMF</b> function ends EMF playback operations for a physical page of an EMF-formatted print job.</p>


## -syntax

````
BOOL GdiEndPageEMF(
   HANDLE SpoolFileHandle,
   DWORD  dwOptimization
);
````


## -parameters
<dl>

### -param <i>SpoolFileHandle</i> 

<dd>
<p>Caller-supplied spool file handle, obtained by a previous call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff549517">GdiGetSpoolFileHandle</a>.</p>
</dd>

### -param <i>dwOptimization</i> 

<dd>
<p>Caller-supplied flags. The following flag is defined:</p>
<p></p>
<dl>

### -param <a id="EMF_PP_COLOR_OPTIMIZATION"></a><a id="emf_pp_color_optimization"></a>EMF_PP_COLOR_OPTIMIZATION

<dd>
<p>Enable color optimization. For more information, see Remarks.</p>
</dd>
</dl>
</dd>
</dl>

## -returns
<p>If the operation succeeds, the function returns <b>TRUE</b>. Otherwise the function returns <b>FALSE</b>, and an error code can be obtained by calling <b>GetLastError</b>.</p>

## -remarks
<p>The <b>GdiEndPageEMF</b> function is exported by gdi32.dll for use within a print processor's <a href="https://msdn.microsoft.com/library/windows/hardware/ff560724">PrintDocumentOnPrintProcessor</a> function.</p>

<p>The <b>GdiEndPageEMF</b> function ends the processing of a physical page and causes it to be ejected from the printer. A print processor should call <b>GdiEndPageEMF</b> at the following times:</p>

<p>After the appropriate number of document pages have been placed on the physical page by making calls to <a href="https://msdn.microsoft.com/library/windows/hardware/ff549524">GdiPlayPageEMF</a>. Note that <b>GdiPlayPageEMF</b> does not actually print on the device context, but instead prepares a data structure that describes the text and graphics that are to be printed on the physical page(s). The text and graphics are printed to the device context when <b>GdiEndPageEMF</b> is called.</p>

<p>Whenever a call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff549478">GdiGetDevmodeForPage</a> indicates a document page's <a href="https://msdn.microsoft.com/library/windows/hardware/ff552837">DEVMODEW</a> structure is different from the previous page's DEVMODE structure.</p>

<p>If this function is called with the <i>dwOptimization </i>parameter set to EMF_PP_COLOR_OPTIMIZATION, color optimization is enabled. If <i>dwOptimization</i> is set to 0, no optimization is performed. When color optimization is enabled, the presence of color in the spool file causes the spool file to be played in color; the lack of color in the spool file causes the spool file to be played in monochrome.</p>

<p>If you are creating a Unidrv rendering plug-in to generate color watermarks, be advised that color optimization causes color watermarks to be printed in black and white when they are printed on black-and-white documents. To ensure that color watermarks print correctly with color and black-and-white documents, disable color optimization.</p>

<p>The color optimization controlled by the <i>dwOptimization</i> parameter can also be controlled by setting the <b>dwColorOptimization</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff545091">ATTRIBUTE_INFO_2</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff545093">ATTRIBUTE_INFO_3</a> structures. This optimization also can be controlled by the Unidrv *<b>ChangeColorModeOnDoc?</b> color attribute (see <a href="NULL">Color Attributes</a>).</p>

<p>For additional information, see <a href="NULL">Using GDI Functions in Print Processors</a>.</p>

<p>The <b>GdiEndPageEMF</b> function is exported by gdi32.dll for use within a print processor's <a href="https://msdn.microsoft.com/library/windows/hardware/ff560724">PrintDocumentOnPrintProcessor</a> function.</p>

<p>The <b>GdiEndPageEMF</b> function ends the processing of a physical page and causes it to be ejected from the printer. A print processor should call <b>GdiEndPageEMF</b> at the following times:</p>

<p>After the appropriate number of document pages have been placed on the physical page by making calls to <a href="https://msdn.microsoft.com/library/windows/hardware/ff549524">GdiPlayPageEMF</a>. Note that <b>GdiPlayPageEMF</b> does not actually print on the device context, but instead prepares a data structure that describes the text and graphics that are to be printed on the physical page(s). The text and graphics are printed to the device context when <b>GdiEndPageEMF</b> is called.</p>

<p>Whenever a call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff549478">GdiGetDevmodeForPage</a> indicates a document page's <a href="https://msdn.microsoft.com/library/windows/hardware/ff552837">DEVMODEW</a> structure is different from the previous page's DEVMODE structure.</p>

<p>If this function is called with the <i>dwOptimization </i>parameter set to EMF_PP_COLOR_OPTIMIZATION, color optimization is enabled. If <i>dwOptimization</i> is set to 0, no optimization is performed. When color optimization is enabled, the presence of color in the spool file causes the spool file to be played in color; the lack of color in the spool file causes the spool file to be played in monochrome.</p>

<p>If you are creating a Unidrv rendering plug-in to generate color watermarks, be advised that color optimization causes color watermarks to be printed in black and white when they are printed on black-and-white documents. To ensure that color watermarks print correctly with color and black-and-white documents, disable color optimization.</p>

<p>The color optimization controlled by the <i>dwOptimization</i> parameter can also be controlled by setting the <b>dwColorOptimization</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff545091">ATTRIBUTE_INFO_2</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff545093">ATTRIBUTE_INFO_3</a> structures. This optimization also can be controlled by the Unidrv *<b>ChangeColorModeOnDoc?</b> color attribute (see <a href="NULL">Color Attributes</a>).</p>

<p>For additional information, see <a href="NULL">Using GDI Functions in Print Processors</a>.</p>

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
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Winppi.h (include Winppi.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Gdi32.Lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>Gdi32.dll</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549543">GdiStartPageEMF</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549524">GdiPlayPageEMF</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [print\print]:%20GdiEndPageEMF function%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>