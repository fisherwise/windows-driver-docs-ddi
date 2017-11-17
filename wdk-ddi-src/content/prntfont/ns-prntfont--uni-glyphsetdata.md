---
UID: NS.prntfont._UNI_GLYPHSETDATA
title: UNI_GLYPHSETDATA
author: windows-driver-content
description: The UNI_GLYPHSEDATA structure is one of the structures used to define the contents of glyph translation table files (.gtt files).
old-location: print\uni_glyphsetdata.htm
ms.assetid: a2c98783-c463-435e-9d78-c10686f1c75c
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: print
req.header: prntfont.h
req.include-header: Prntfont.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: UNI_GLYPHSETDATA
req.alt-loc: prntfont.h
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
ms.keywords: UNI_GLYPHSETDATA, UNI_GLYPHSETDATA, *PUNI_GLYPHSETDATA
req.iface: 
req.product: Windows 10 or later.
---

# UNI_GLYPHSETDATA structure



## -description
<p>The UNI_GLYPHSEDATA structure is one of the structures used to define the contents of <a href="print.customized_font_management#ddk_glyph_translation_table_files_gg#ddk_glyph_translation_table_files_gg">glyph translation table files</a> (.gtt files).</p>


## -syntax

````
typedef struct _UNI_GLYPHSETDATA {
  DWORD dwSize;
  DWORD dwVersion;
  DWORD dwFlags;
  LONG  lPredefinedID;
  DWORD dwGlyphCount;
  DWORD dwRunCount;
  DWORD loRunOffset;
  DWORD dwCodePageCount;
  DWORD loCodePageOffset;
  DWORD loMapTableOffset;
  DWORD dwReserved[2];
} UNI_GLYPHSETDATA, *PUNI_GLYPHSETDATA;
````


## -struct-fields
<dl>

### -field <b>dwSize</b>

<dd>
<p>Specifies the total size, in bytes, of the .gtt file. Note that this is the total size of all structures used to define the file. This value is not the size of the UNI_GLYPHSETDATA structure.</p>
</dd>

### -field <b>dwVersion</b>

<dd>
<p>Specifies the file version number, as defined in prntfont.h by a constant with a name format of UNI_GLYPHSETDATA_VERSION_<i>x</i>_<i>x</i>.</p>
</dd>

### -field <b>dwFlags</b>

<dd>
<p>Not used.</p>
</dd>

### -field <b>lPredefinedID</b>

<dd>
<p>Specifies one of the CC_-prefixed code conversion identifiers defined in prntfont.h. </p>
</dd>

### -field <b>dwGlyphCount</b>

<dd>
<p>Specifies the number of glyphs provided by this font.</p>
</dd>

### -field <b>dwRunCount</b>

<dd>
<p>Specifies the number of <a href="https://msdn.microsoft.com/library/windows/hardware/ff550544">GLYPHRUN</a> structures in the array pointed to by <b>loRunOffset</b>.</p>
</dd>

### -field <b>loRunOffset</b>

<dd>
<p>Specifies the byte offset from the beginning of the UNI_GLYPHSETDATA structure to the beginning of an array of <a href="https://msdn.microsoft.com/library/windows/hardware/ff550544">GLYPHRUN</a> structures.</p>
</dd>

### -field <b>dwCodePageCount</b>

<dd>
<p>Specifies the number of <a href="https://msdn.microsoft.com/library/windows/hardware/ff563596">UNI_CODEPAGEINFO</a> structures in the array pointed to by <b>loCodePageOffset</b>.</p>
</dd>

### -field <b>loCodePageOffset</b>

<dd>
<p>Specifies the byte offset from the beginning of the UNI_GLYPHSETDATA structure to the beginning of an array of <a href="https://msdn.microsoft.com/library/windows/hardware/ff563596">UNI_CODEPAGEINFO</a> structures.</p>
</dd>

### -field <b>loMapTableOffset</b>

<dd>
<p>Specifies the byte offset from the beginning of the UNI_GLYPHSETDATA structure to the beginning of a <a href="https://msdn.microsoft.com/library/windows/hardware/ff556509">MAPTABLE</a> structure.</p>
</dd>

### -field <b>dwReserved</b>

<dd>
<p>Reserved for system use.</p>
</dd>
</dl>

## -remarks
<p>A UNI_GLYPHSETDATA structure must be the first structure contained in a .gtt file.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Prntfont.h (include Prntfont.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550544">GLYPHRUN</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563596">UNI_CODEPAGEINFO</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff556509">MAPTABLE</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [print\print]:%20UNI_GLYPHSETDATA structure%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>