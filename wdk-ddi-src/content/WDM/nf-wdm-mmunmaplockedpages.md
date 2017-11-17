---
UID: NF.wdm.MmUnmapLockedPages
title: MmUnmapLockedPages
author: windows-driver-content
description: The MmUnmapLockedPages routine releases a mapping that was set up by a preceding call to the MmMapLockedPages or MmMapLockedPagesSpecifyCache routine.
old-location: kernel\mmunmaplockedpages.htm
ms.assetid: ab5f33b9-5261-4d30-bceb-8e91a24ae0a8
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
req.alt-api: MmUnmapLockedPages
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: HwStorPortProhibitedDDIs
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: See Remarks section.
ms.keywords: MmUnmapLockedPages
req.iface: 
req.product: Windows 10 or later.
---

# MmUnmapLockedPages function



## -description
<p>The <b>MmUnmapLockedPages</b> routine releases a mapping that was set up by a preceding call to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff554622">MmMapLockedPages</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff554629">MmMapLockedPagesSpecifyCache</a> routine.</p>


## -syntax

````
VOID MmUnmapLockedPages(
  _In_ PVOID BaseAddress,
  _In_ PMDL  MemoryDescriptorList
);
````


## -parameters
<dl>

### -param <i>BaseAddress</i> [in]

<dd>
<p>Pointer to the base virtual address to which the physical pages were mapped.</p>
</dd>

### -param <i>MemoryDescriptorList</i> [in]

<dd>
<p>Pointer to an MDL.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>Callers of <b>MmUnmapLockedPages</b> must be running at IRQL &lt;= DISPATCH_LEVEL if the pages were mapped to system space. Otherwise, the caller must be running at IRQL &lt;= APC_LEVEL.</p>

<p>Note that if the call to <b>MmMapLockedPages</b> or <b>MmMapLockedPagesSpecifyCache</b> specified user mode, the caller must be in the context of the original process before calling <b>MmUnmapLockedPages</b>. This is because the unmapping operation occurs in the context of the calling process, and, if the context is incorrect, the unmapping operation could delete the address range of a random process.</p>

<p>Callers of <b>MmUnmapLockedPages</b> must be running at IRQL &lt;= DISPATCH_LEVEL if the pages were mapped to system space. Otherwise, the caller must be running at IRQL &lt;= APC_LEVEL.</p>

<p>Note that if the call to <b>MmMapLockedPages</b> or <b>MmMapLockedPagesSpecifyCache</b> specified user mode, the caller must be in the context of the original process before calling <b>MmUnmapLockedPages</b>. This is because the unmapping operation occurs in the context of the calling process, and, if the context is incorrect, the unmapping operation could delete the address range of a random process.</p>

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
<p>See Remarks section.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/hh454220">HwStorPortProhibitedDDIs</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554622">MmMapLockedPages</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554629">MmMapLockedPagesSpecifyCache</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20MmUnmapLockedPages routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>