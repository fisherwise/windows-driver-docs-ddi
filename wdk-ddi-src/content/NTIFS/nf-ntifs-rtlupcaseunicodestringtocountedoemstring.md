---
UID: NF.ntifs.RtlUpcaseUnicodeStringToCountedOemString
title: RtlUpcaseUnicodeStringToCountedOemString
author: windows-driver-content
description: The RtlUpcaseUnicodeStringToCountedOemString routine translates a given Unicode source string into an uppercase counted OEM string using the current system OEM code page.
old-location: ifsk\rtlupcaseunicodestringtocountedoemstring.htm
ms.assetid: c1e466d7-892f-4049-a6c2-60ab8f960acb
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
req.alt-api: RtlUpcaseUnicodeStringToCountedOemString
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: < DISPATCH_LEVEL
ms.keywords: RtlUpcaseUnicodeStringToCountedOemString
req.iface: 
---

# RtlUpcaseUnicodeStringToCountedOemString function



## -description
<p>The <b>RtlUpcaseUnicodeStringToCountedOemString</b> routine translates a given Unicode source string into an uppercase counted OEM string using the current system OEM code page. </p>


## -syntax

````
NTSTATUS RtlUpcaseUnicodeStringToCountedOemString(
       POEM_STRING      DestinationString,
  _In_ PCUNICODE_STRING SourceString,
  _In_ BOOLEAN          AllocateDestinationString
);
````


## -parameters
<dl>

### -param <i>DestinationString</i> 

<dd>
<p>Pointer to a caller-allocated buffer to receive the counted OEM string. If <i>AllocateDestinationString</i> is <b>FALSE</b>, the caller must also allocate a buffer for the <b>Buffer</b> member of <i>DestinationString</i> to hold the OEM data. If <i>AllocateDestinationString</i> is <b>TRUE</b>, <b>RtlUpcaseUnicodeStringToCountedOemString </b>allocates a buffer large enough to hold the string, passes a pointer to it in <b>Buffer</b>, and updates the length and maximum length members of <i>DestinationString</i> accordingly. </p>
</dd>

### -param <i>SourceString</i> [in]

<dd>
<p>Pointer to the Unicode string to be translated. </p>
</dd>

### -param <i>AllocateDestinationString</i> [in]

<dd>
<p>Set to <b>TRUE</b> if <b>RtlUpcaseUnicodeStringToCountedOemString </b>should allocate the buffer space for the <i>DestinationString</i>, <b>FALSE</b> otherwise. If this parameter is <b>TRUE</b>, the caller is responsible for freeing the buffer when it is no longer needed by calling <b>RtlFreeOemString</b>. </p>
</dd>
</dl>

## -returns
<p><b>RtlUpcaseUnicodeStringToCountedOemString</b> returns STATUS_SUCCESS if it returns a translated string at <i>DestinationString</i>. Otherwise, no storage was allocated, nor was any conversion performed. It returns STATUS_UNMAPPABLE_CHARACTER if it cannot translate a character in the given <i>SourceString</i>. </p>

## -remarks
<p><b>RtlUpcaseUnicodeStringToCountedOemString</b> returns a string that is not null-terminated. It translates the given source string using the OEM code page that was installed as the current system code page at system boot time, and converts the translated string to uppercase. </p>

<p>To find a best-match mapping for any special characters, such as a copyright character, in the given source string, <b>RtlUpcaseUnicodeStringToCountedOemString</b> performs the following operations: </p>

<p>Translates a copy of the Unicode string at <i>SourceString</i> into an OEM string</p>

<p>Translates the OEM string back into Unicode</p>

<p>Converts this new Unicode string to uppercase</p>

<p>Translates the uppercase Unicode string into a counted OEM string and returns it at <i>DestinationString</i></p>

<p>This routine does not modify the source string. </p>

<p>For information about other string-handling routines, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563884">Strings</a>. </p>

<p><b>RtlUpcaseUnicodeStringToCountedOemString</b> returns a string that is not null-terminated. It translates the given source string using the OEM code page that was installed as the current system code page at system boot time, and converts the translated string to uppercase. </p>

<p>To find a best-match mapping for any special characters, such as a copyright character, in the given source string, <b>RtlUpcaseUnicodeStringToCountedOemString</b> performs the following operations: </p>

<p>Translates a copy of the Unicode string at <i>SourceString</i> into an OEM string</p>

<p>Translates the OEM string back into Unicode</p>

<p>Converts this new Unicode string to uppercase</p>

<p>Translates the uppercase Unicode string into a counted OEM string and returns it at <i>DestinationString</i></p>

<p>This routine does not modify the source string. </p>

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
<dt>NtosKrnl.exe</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff558741">OEM_STRING</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552281">RtlFreeOemString</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553142">RtlOemStringToCountedUnicodeString</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553251">RtlUnicodeStringToCountedOemString</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553254">RtlUnicodeStringToOemSize</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553282">RtlUpcaseUnicodeStringToOemString</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553309">RtlUpcaseUnicodeToOemN</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564879">UNICODE_STRING</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20RtlUpcaseUnicodeStringToCountedOemString routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>