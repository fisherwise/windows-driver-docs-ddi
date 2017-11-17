---
UID: NF.ntifs.CcMdlWriteComplete
title: CcMdlWriteComplete
author: windows-driver-content
description: The CcMdlWriteComplete routine frees the memory descriptor lists (MDL) created by CcPrepareMdlWrite for a cached file.
old-location: ifsk\ccmdlwritecomplete.htm
ms.assetid: dcd13afa-1467-407c-b843-ff88bd6526c3
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
req.alt-api: CcMdlWriteComplete
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
req.irql: PASSIVE_LEVEL
ms.keywords: CcMdlWriteComplete
req.iface: 
---

# CcMdlWriteComplete function



## -description
<p>The <b>CcMdlWriteComplete</b> routine frees the memory descriptor lists (MDL) created by <a href="https://msdn.microsoft.com/library/windows/hardware/ff539181">CcPrepareMdlWrite</a> for a cached file.</p>


## -syntax

````
VOID CcMdlWriteComplete(
  _In_ PFILE_OBJECT   FileObject,
  _In_ PLARGE_INTEGER FileOffset,
  _In_ PMDL           MdlChain
);
````


## -parameters
<dl>

### -param <i>FileObject</i> [in]

<dd>
<p>File object pointer that was passed to <a href="https://msdn.microsoft.com/library/windows/hardware/ff539181">CcPrepareMdlWrite</a>.</p>
</dd>

### -param <i>FileOffset</i> [in]

<dd>
<p>Value of <i>FileOffset</i> that was passed to <a href="https://msdn.microsoft.com/library/windows/hardware/ff539181">CcPrepareMdlWrite</a>.</p>
</dd>

### -param <i>MdlChain</i> [in]

<dd>
<p>Address of the MDL chain returned by <a href="https://msdn.microsoft.com/library/windows/hardware/ff539181">CcPrepareMdlWrite</a>.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>File systems call <b>CcMdlWriteComplete</b> to free the memory descriptor lists (MDL) created by <a href="https://msdn.microsoft.com/library/windows/hardware/ff539181">CcPrepareMdlWrite</a> for a cached file and to mark the specified byte range for write. All physical pages that were locked down are unlocked. Any pages that were mapped are unmapped.</p>

<p>If the FO_WRITE_THROUGH flag is set on the file object pointed to by the <i>FileObject</i> parameter, the file data is immediately flushed to disk. This flush operation re-enters the file system and can cause <b>CcMdlWriteComplete</b> to raise an exception if the flush operation fails. In this case, the MDL has not been freed and the caller may re-try the operation.</p>

<p>After <b>CcMdlWriteComplete</b> is called successfully for an IRP_MN_COMPLETE operation, the caller must set the IRP's <b>MdlAddress</b> field to <b>NULL</b>. </p>

<p>Before using <b>CcMdlWriteComplete</b>, file system developers are strongly encouraged to study the way this routine is used in the FASTFAT sample. </p>

<p>Each call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff539181">CcPrepareMdlWrite</a> must be followed by a call to <b>CcMdlWriteComplete</b> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff539166">CcMdlWriteAbort</a>.</p>

<p>File systems call <b>CcMdlWriteComplete</b> to free the memory descriptor lists (MDL) created by <a href="https://msdn.microsoft.com/library/windows/hardware/ff539181">CcPrepareMdlWrite</a> for a cached file and to mark the specified byte range for write. All physical pages that were locked down are unlocked. Any pages that were mapped are unmapped.</p>

<p>If the FO_WRITE_THROUGH flag is set on the file object pointed to by the <i>FileObject</i> parameter, the file data is immediately flushed to disk. This flush operation re-enters the file system and can cause <b>CcMdlWriteComplete</b> to raise an exception if the flush operation fails. In this case, the MDL has not been freed and the caller may re-try the operation.</p>

<p>After <b>CcMdlWriteComplete</b> is called successfully for an IRP_MN_COMPLETE operation, the caller must set the IRP's <b>MdlAddress</b> field to <b>NULL</b>. </p>

<p>Before using <b>CcMdlWriteComplete</b>, file system developers are strongly encouraged to study the way this routine is used in the FASTFAT sample. </p>

<p>Each call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff539181">CcPrepareMdlWrite</a> must be followed by a call to <b>CcMdlWriteComplete</b> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff539166">CcMdlWriteAbort</a>.</p>

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
<p>PASSIVE_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539166">CcMdlWriteAbort</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539181">CcPrepareMdlWrite</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20CcMdlWriteComplete routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>