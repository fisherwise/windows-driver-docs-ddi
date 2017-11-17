---
UID: NF.wdm.RtlFindClearRuns
title: RtlFindClearRuns
author: windows-driver-content
description: The RtlFindClearRuns routine finds the specified number of runs of clear bits within a given bitmap.
old-location: kernel\rtlfindclearruns.htm
ms.assetid: ad44c7ba-1d8e-4ba4-8d1b-83ff8b2e3d06
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: Available starting with Windows 2000.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RtlFindClearRuns
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
req.irql: <= APC_LEVEL (See Remarks section)
ms.keywords: RtlFindClearRuns
req.iface: 
req.product: Windows 10 or later.
---

# RtlFindClearRuns function



## -description
<p>The <b>RtlFindClearRuns</b> routine finds the specified number of runs of clear bits within a given bitmap.</p>


## -syntax

````
ULONG RtlFindClearRuns(
  _In_  PRTL_BITMAP     BitMapHeader,
  _Out_ PRTL_BITMAP_RUN RunArray,
  _In_  ULONG           SizeOfRunArray,
  _In_  BOOLEAN         LocateLongestRuns
);
````


## -parameters
<dl>

### -param <i>BitMapHeader</i> [in]

<dd>
<p>A pointer to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff563614">RTL_BITMAP</a> structure that describes the bitmap. This structure must have been initialized by the <a href="https://msdn.microsoft.com/library/windows/hardware/ff561925">RtlInitializeBitMap</a> routine. </p>
</dd>

### -param <i>RunArray</i> [out]

<dd>
<p>Pointer to the first element in a caller-allocated array for the bit position and length of each clear run found in the given bitmap variable. </p>
</dd>

### -param <i>SizeOfRunArray</i> [in]

<dd>
<p>Specifies the maximum number of clear runs to satisfy this request.</p>
</dd>

### -param <i>LocateLongestRuns</i> [in]

<dd>
<p>If <b>TRUE</b>, specifies that the routine is to search the entire bitmap for the longest clear runs it can find. Otherwise, the routine stops searching when it has found the number of clear runs specified by <i>SizeOfRunArray</i>. </p>
</dd>
</dl>

## -returns
<p><b>RtlFindClearRuns</b> returns the number of clear runs found.</p>

## -remarks
<p>If <i>LocateLongestRuns </i>is <b>TRUE</b>, the clear runs indicated at <i>RunArray </i>are sorted from longest to shortest. A clear run can consist of a single bit.</p>

<p>Callers of <b>RtlFindClearRuns</b> must be running at IRQL &lt;= APC_LEVEL if the memory that contains the bitmap variable is pageable or the memory at <i>BitMapHeader</i> is pageable. Otherwise, <b>RtlFindClearRuns</b> can be called at any IRQL.</p>

<p>If <i>LocateLongestRuns </i>is <b>TRUE</b>, the clear runs indicated at <i>RunArray </i>are sorted from longest to shortest. A clear run can consist of a single bit.</p>

<p>Callers of <b>RtlFindClearRuns</b> must be running at IRQL &lt;= APC_LEVEL if the memory that contains the bitmap variable is pageable or the memory at <i>BitMapHeader</i> is pageable. Otherwise, <b>RtlFindClearRuns</b> can be called at any IRQL.</p>

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
<p>Version</p>
</th>
<td width="70%">
<p>Available starting with Windows 2000.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdm.h (include Wdm.h, Ntddk.h, or Ntifs.h)</dt>
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
<p>&lt;= APC_LEVEL (See Remarks section)</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561742">RtlAreBitsClear</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563614">RTL_BITMAP</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561873">RtlFindClearBits</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561881">RtlFindLongestRunClear</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561877">RtlFindFirstRunClear</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561885">RtlFindNextForwardRunClear</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561879">RtlFindLastBackwardRunClear</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561925">RtlInitializeBitMap</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20RtlFindClearRuns routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>