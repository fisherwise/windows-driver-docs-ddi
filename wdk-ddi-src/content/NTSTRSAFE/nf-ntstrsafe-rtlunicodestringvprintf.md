---
UID: NF.ntstrsafe.RtlUnicodeStringVPrintf
title: RtlUnicodeStringVPrintf
author: windows-driver-content
description: The RtlUnicodeStringVPrintf function creates a text string, with formatting that is based on supplied formatting information, and stores the string in a UNICODE_STRING structure.
old-location: kernel\rtlunicodestringvprintf.htm
ms.assetid: d8ca2c47-e3b6-4ead-8d8e-2b2a4fe97658
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: ntstrsafe.h
req.include-header: Ntstrsafe.h
req.target-type: Desktop
req.target-min-winverclnt: Available in Windows XP with Service Pack 1 (SP1) and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RtlUnicodeStringVPrintf
req.alt-loc: Ntstrsafe.lib,Ntstrsafe.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ntstrsafe.lib
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: RtlUnicodeStringVPrintf
req.iface: 
---

# RtlUnicodeStringVPrintf function



## -description
<p>The <b>RtlUnicodeStringVPrintf</b> function creates a text string, with formatting that is based on supplied formatting information, and stores the string in a <a href="https://msdn.microsoft.com/library/windows/hardware/ff564879">UNICODE_STRING</a> structure.</p>


## -syntax

````
NTSTATUS RtlUnicodeStringVPrintf(
  _Out_ PUNICODE_STRING  DestinationString,
  _In_  NTSTRSAFE_PCWSTR pszFormat,
  _In_  va_list          argList
);
````


## -parameters
<dl>

### -param <i>DestinationString</i> [out]

<dd>
<p>A pointer to a <b>UNICODE_STRING</b> structure that receives a formatted string. <b>RtlUnicodeStringVPrintf</b> creates this string from the formatting string that <i>pszFormat</i> specifies and the function's argument list. The maximum number of characters in the string is NTSTRSAFE_UNICODE_STRING_MAX_CCH.</p>
</dd>

### -param <i>pszFormat</i> [in]

<dd>
<p>A pointer to a null-terminated text string that contains <b>printf</b>-styled formatting directives.</p>
</dd>

### -param <i>argList</i> [in]

<dd>
<p>A <b>va_list</b>-typed argument list. Arguments in this argument list will be interpreted by using the formatting string that <i>pszFormat</i> specifies. </p>
</dd>
</dl>

## -returns
<p><b>RtlUnicodeStringVPrintf</b> returns one of the following NTSTATUS values. </p><dl>
<dt><b>STATUS_SUCCESS</b></dt>
</dl><p>This <i>success</i> status means source data was present, the string was copied without truncation, and the resultant destination buffer is null-terminated.</p><dl>
<dt><b>STATUS_BUFFER_OVERFLOW</b></dt>
</dl><p>This <i>warning</i> status means the copy operation did not complete due to insufficient buffer space. The destination buffer contains a truncated, null-terminated version of the intended result.</p><dl>
<dt><b>STATUS_INVALID_PARAMETER</b></dt>
</dl><p>This <i>error</i> status means the function received an invalid input parameter. For more information, see the following paragraph.</p>

<p> </p>

<p><b>RtlUnicodeStringVPrintf</b> returns the STATUS_INVALID_PARAMETER value when one of the following occurs:</p>

<p>For information about how to test NTSTATUS values, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff565436">Using NTSTATUS Values</a>.</p>

## -remarks
<p>The <b>RtlUnicodeStringVPrintf</b> function uses the destination buffer's size to ensure that the string formatting operation does not write past the end of the buffer. The function does not terminate the resultant string with a null character.</p>

<p>If the format string and destination string overlap, the behavior of the function is undefined.</p>

<p>The <i>pszFormat</i> and <i>DestinationString</i> pointers cannot be <b>NULL</b>. If you need to handle <b>NULL</b> pointer values, use the <a href="https://msdn.microsoft.com/library/windows/hardware/ff562988">RtlUnicodeStringVPrintfEx</a> function.</p>

<p>For more information about the safe string functions, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff565508">Using Safe String Functions</a>. </p>

<p>The <b>RtlUnicodeStringVPrintf</b> function uses the destination buffer's size to ensure that the string formatting operation does not write past the end of the buffer. The function does not terminate the resultant string with a null character.</p>

<p>If the format string and destination string overlap, the behavior of the function is undefined.</p>

<p>The <i>pszFormat</i> and <i>DestinationString</i> pointers cannot be <b>NULL</b>. If you need to handle <b>NULL</b> pointer values, use the <a href="https://msdn.microsoft.com/library/windows/hardware/ff562988">RtlUnicodeStringVPrintfEx</a> function.</p>

<p>For more information about the safe string functions, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff565508">Using Safe String Functions</a>. </p>

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
<p>Available in Windows XP with Service Pack 1 (SP1) and later versions of Windows. </p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntstrsafe.h (include Ntstrsafe.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Ntstrsafe.lib</dt>
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

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562961">RtlUnicodeStringPrintf</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562964">RtlUnicodeStringPrintfEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562988">RtlUnicodeStringVPrintfEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564879">UNICODE_STRING</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20RtlUnicodeStringVPrintf function%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>