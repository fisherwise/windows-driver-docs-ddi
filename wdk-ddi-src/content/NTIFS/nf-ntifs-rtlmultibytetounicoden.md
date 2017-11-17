---
UID: NF.ntifs.RtlMultiByteToUnicodeN
title: RtlMultiByteToUnicodeN
author: windows-driver-content
description: The RtlMultiByteToUnicodeN routine translates the specified source string into a Unicode string, using the current system ANSI code page (ACP). The source string is not necessarily from a multibyte character set.
old-location: ifsk\rtlmultibytetounicoden.htm
ms.assetid: c0cc4fba-01ba-4745-8dee-fc4c43f570cf
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: ifsk
req.header: ntifs.h
req.include-header: Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RtlMultiByteToUnicodeN
req.alt-loc: NtosKrnl.exe,Ntdll.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe (kernel mode); 
Ntdll.dll (user mode)
req.irql: < DISPATCH_LEVEL
ms.keywords: RtlMultiByteToUnicodeN
req.iface: 
---

# RtlMultiByteToUnicodeN function



## -description
<p>The <b>RtlMultiByteToUnicodeN</b> routine translates the specified source string into a Unicode string, using the current system ANSI code page (ACP). The source string is not necessarily from a multibyte character set. </p>


## -syntax

````
NTSTATUS RtlMultiByteToUnicodeN(
  _Out_           PWCH   UnicodeString,
  _In_            ULONG  MaxBytesInUnicodeString,
  _Out_opt_       PULONG BytesInUnicodeString,
  _In_      const CHAR   *MultiByteString,
  _In_            ULONG  BytesInMultiByteString
);
````


## -parameters
<dl>

### -param <i>UnicodeString</i> [out]

<dd>
<p>Pointer to a caller-allocated buffer that receives the translated string. <i>UnicodeString</i> buffer must not overlap with <i>MultiByteString </i>buffer.</p>
</dd>

### -param <i>MaxBytesInUnicodeString</i> [in]

<dd>
<p>Maximum number of bytes to be written at <i>UnicodeString</i>. If this value causes the translated string to be truncated, <b>RtlMultiByteToUnicodeN</b> does not return an error status. </p>
</dd>

### -param <i>BytesInUnicodeString</i> [out, optional]

<dd>
<p>Pointer to a caller-allocated variable that receives the length, in bytes, of the translated string. This parameter can be <b>NULL</b>. </p>
</dd>

### -param <i>MultiByteString</i> [in]

<dd>
<p>Pointer to the string to be translated. </p>
</dd>

### -param <i>BytesInMultiByteString</i> [in]

<dd>
<p>Size, in bytes, of the string at <i>MultiByteString</i>. </p>
</dd>
</dl>

## -returns
<p><b>RtlMultiByteToUnicodeN</b> returns STATUS_SUCCESS. </p>

## -remarks
<p><b>RtlMultiByteToUnicodeN</b> supports only precomposed Unicode characters that are mapped to the current system ANSI code page installed at system boot. </p>

<p>Although <i>BytesInUnicodeString</i> is optional and can be <b>NULL</b>, callers should provide storage for it, because the received length can be used to determine whether the conversion was successful.</p>

<p>If the current system code page defines a single-byte character set, all ANSI characters in the range 0x00 to 0x7f are simply zero-extended in the corresponding Unicode string to speed the conversion operation. The ANSI value 0x5c in such a code page is translated into the backslash character, even if the current single-byte code page defines this character as the Yen sign. </p>

<p><b>RtlMultiByteToUnicodeN</b> does not modify the source string unless the <i>UnicodeString</i> and <i>MultiByteString</i> pointers are equivalent. The returned Unicode string is not null-terminated. </p>

<p>Like <b>RtlMultiByteToUnicodeSize</b>, <b>RtlMultiByteToUnicodeN</b> supports only precomposed Unicode characters that are mapped to the current system ANSI code page installed at system boot. </p>

<p>For information about other string-handling routines, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563884">Strings</a>. </p>

<p><b>RtlMultiByteToUnicodeN</b> supports only precomposed Unicode characters that are mapped to the current system ANSI code page installed at system boot. </p>

<p>Although <i>BytesInUnicodeString</i> is optional and can be <b>NULL</b>, callers should provide storage for it, because the received length can be used to determine whether the conversion was successful.</p>

<p>If the current system code page defines a single-byte character set, all ANSI characters in the range 0x00 to 0x7f are simply zero-extended in the corresponding Unicode string to speed the conversion operation. The ANSI value 0x5c in such a code page is translated into the backslash character, even if the current single-byte code page defines this character as the Yen sign. </p>

<p><b>RtlMultiByteToUnicodeN</b> does not modify the source string unless the <i>UnicodeString</i> and <i>MultiByteString</i> pointers are equivalent. The returned Unicode string is not null-terminated. </p>

<p>Like <b>RtlMultiByteToUnicodeSize</b>, <b>RtlMultiByteToUnicodeN</b> supports only precomposed Unicode characters that are mapped to the current system ANSI code page installed at system boot. </p>

<p>For information about other string-handling routines, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563884">Strings</a>. </p>

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
<dt>Ntifs.h (include Ntifs.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>NtosKrnl.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>NtosKrnl.exe (kernel mode); </dt>
<dt>Ntdll.dll (user mode)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&lt; DISPATCH_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553121">RtlMultiByteToUnicodeSize</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553261">RtlUnicodeToMultiByteN</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20RtlMultiByteToUnicodeN routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>