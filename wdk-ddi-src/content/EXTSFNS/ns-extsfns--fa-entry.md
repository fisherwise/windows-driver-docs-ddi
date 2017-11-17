---
UID: NS.extsfns._FA_ENTRY
title: FA_ENTRY
author: windows-driver-content
description: A DebugFailureAnalysis object has a collection of failure analysis entries (FA entries). Each FA entry is represented by an FA_ENTRY structure. For more information, see Failure Analysis Entries, Tags, and Data Types.
old-location: debugger\fa_entry.htm
ms.assetid: 912DCC1E-2C81-4702-8E12-6331DFB298F0
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: debugger
req.header: extsfns.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FA_ENTRY
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
ms.keywords: FA_ENTRY, FA_ENTRY, *PFA_ENTRY
req.iface: IDebugFailureAnalysis2
---

# FA_ENTRY structure



## -description
<p>A <a href="https://msdn.microsoft.com/0B44FCB9-D23F-4630-9F9A-FBAD46712B14">DebugFailureAnalysis</a> object has a collection of <a href="https://msdn.microsoft.com/library/windows/hardware/jj991807">failure analysis entries</a> (FA entries).  Each FA entry is represented by an <b>FA_ENTRY</b> structure. For more information, see <a href="debugger.writing_an_analysis_extension_to_extend__analyze#failure_analysis_entries_tags_and_data_types#failure_analysis_entries_tags_and_data_types">Failure Analysis Entries, Tags, and Data Types</a>.</p>


## -syntax

````
struct FA_ENTRY {
  FA_TAG Tag;
  USHORT FullSize;
  USHORT DataSize;
};
````


## -struct-fields
<dl>

### -field <b>Tag</b>

<dd>
<p>A value in the <a href="https://msdn.microsoft.com/library/windows/hardware/jj991810">FA_TAG</a> enumeration.</p>
</dd>

### -field <b>FullSize</b>

<dd>
<p>The size of the of <a href="https://msdn.microsoft.com/759DE159-F2A8-4BB1-AAF5-B2B91C4F91B0">FA entry</a>, which includes the size of the <b>FA_ENTRY</b> structure and the size of the FA entry's data block.</p>
</dd>

### -field <b>DataSize</b>

<dd>
<p>The size of the <a href="https://msdn.microsoft.com/759DE159-F2A8-4BB1-AAF5-B2B91C4F91B0">FA entry's</a> data block. </p>
</dd>
</dl>

## -remarks


## -requirements
<table>
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
<a href="https://msdn.microsoft.com/7648F789-85D5-4247-90DD-2EAA43543483">Writing an Analysis Extension Plug-in to Extend !analyze</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/jj991807">Failure Analysis Entries</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/jj983405">IDebugFailureAnalysis2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/jj983432">_EFN_Analyze</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [debugger\debugger]:%20FA_ENTRY structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>