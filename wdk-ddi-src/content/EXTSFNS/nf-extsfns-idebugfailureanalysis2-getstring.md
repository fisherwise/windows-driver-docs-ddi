---
UID: NF.extsfns.IDebugFailureAnalysis2.GetString
title: IDebugFailureAnalysis2::GetString
author: windows-driver-content
description: The GetString method searches a DebugFailureAnalysis object for the first FA entry that has a specified tag. If it finds an FA entry with the specified tag, it gets the ANSI string value from the entry's data block.
old-location: debugger\idebugfailureanalysis2_getstring.htm
ms.assetid: 76F5F3E0-74BF-4DFF-9AA3-A67C03AF56F9
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: debugger
req.header: extsfns.h
req.include-header: 
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IDebugFailureAnalysis2.GetUlong
req.alt-loc: extsfns.h
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
ms.keywords: IDebugFailureAnalysis2, GetString, IDebugFailureAnalysis2::GetString
req.iface: IDebugFailureAnalysis2
---

# IDebugFailureAnalysis2::GetString method



## -description
<p>The <b>GetString</b> method searches a <a href="https://msdn.microsoft.com/0B44FCB9-D23F-4630-9F9A-FBAD46712B14">DebugFailureAnalysis</a> object for the first <a href="https://msdn.microsoft.com/759DE159-F2A8-4BB1-AAF5-B2B91C4F91B0">FA entry</a> that has a specified tag. If it finds an FA entry with the specified tag, it gets the ANSI string value from the entry's data block.</p>


## -syntax

````
PFA_ENTRY GetUlong(
  [in]  FA_TAG Tag,
  [out] PSTR   Str,
  [in]  ULONG  MaxSize
);
````


## -parameters
<dl>

### -param <i>Tag</i> [in]

<dd>
<p>A value in the <a href="https://msdn.microsoft.com/library/windows/hardware/jj991810">FA_TAG</a> enumeration.</p>
</dd>

### -param <i>Str</i> [out]

<dd>
<p>A pointer to a buffer that receives the string value from the entry's data block.</p>
</dd>

### -param <i>MaxSize</i> [in]

<dd>
<p>The size, in bytes, of the buffer pointed to by <i>Str</i>.</p>
</dd>
</dl>

## -returns
<p>If this method finds an <a href="https://msdn.microsoft.com/759DE159-F2A8-4BB1-AAF5-B2B91C4F91B0">FA entry</a> with the specified tag, and if it succeeds in getting the data block, it returns a pointer to the <a href="https://msdn.microsoft.com/library/windows/hardware/jj991808">FA_ENTRY</a> structure. Otherwise, it returns <b>NULL</b>.</p>

## -remarks
<p>This method copies a null-terminated string from the entry's data block to the buffer pointed to by <i>Str</i>. This method copies at most <i>MaxSize</i> characters including the NULL terminator.</p>

<p>Each tag that has already been used in a <a href="https://msdn.microsoft.com/0B44FCB9-D23F-4630-9F9A-FBAD46712B14">DebugFailureAnalysis</a> object is associated with one of the data types in the <a href="https://msdn.microsoft.com/library/windows/hardware/jj991809">FA_ENTRY_TYPE</a> enumeration. To determine the data type associated with a tag, call the <a href="https://msdn.microsoft.com/library/windows/hardware/jj991813">GetType</a> method of the <a href="https://msdn.microsoft.com/library/windows/hardware/jj983404">IDebugFAEntryTags</a> interface. To get a pointer to an IDebugFAEntryTags interface, call the <a href="https://msdn.microsoft.com/library/windows/hardware/jj983414">GetDebugFATagControl</a> method of the <b>IDebugFailureAnalysis2</b> interface.</p>

<p>The appropriate use of this method is get the data block from an <a href="https://msdn.microsoft.com/759DE159-F2A8-4BB1-AAF5-B2B91C4F91B0">FA entry</a> that has a data type of <b>DEBUG_FA_ENTRY_ANSI_STRING</b>. </p>

<p>This method copies a null-terminated string from the entry's data block to the buffer pointed to by <i>Str</i>. This method copies at most <i>MaxSize</i> characters including the NULL terminator.</p>

<p>Each tag that has already been used in a <a href="https://msdn.microsoft.com/0B44FCB9-D23F-4630-9F9A-FBAD46712B14">DebugFailureAnalysis</a> object is associated with one of the data types in the <a href="https://msdn.microsoft.com/library/windows/hardware/jj991809">FA_ENTRY_TYPE</a> enumeration. To determine the data type associated with a tag, call the <a href="https://msdn.microsoft.com/library/windows/hardware/jj991813">GetType</a> method of the <a href="https://msdn.microsoft.com/library/windows/hardware/jj983404">IDebugFAEntryTags</a> interface. To get a pointer to an IDebugFAEntryTags interface, call the <a href="https://msdn.microsoft.com/library/windows/hardware/jj983414">GetDebugFATagControl</a> method of the <b>IDebugFailureAnalysis2</b> interface.</p>

<p>The appropriate use of this method is get the data block from an <a href="https://msdn.microsoft.com/759DE159-F2A8-4BB1-AAF5-B2B91C4F91B0">FA entry</a> that has a data type of <b>DEBUG_FA_ENTRY_ANSI_STRING</b>. </p>

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
<dt>Extsfns.h</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/jj983405">IDebugFailureAnalysis2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/7648F789-85D5-4247-90DD-2EAA43543483">Writing an Analysis Extension Plug-in to Extend !analyze</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/jj983427">SetString</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh406612">AddString</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/jj983432">_EFN_Analyze</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [debugger\debugger]:%20IDebugFailureAnalysis2::GetUlong method%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>