---
UID: NF.ntifs.CcSetDirtyPageThreshold
title: CcSetDirtyPageThreshold
author: windows-driver-content
description: The CcSetDirtyPageThreshold routine sets a per-file dirty page threshold on a cached file.
old-location: ifsk\ccsetdirtypagethreshold.htm
ms.assetid: ba7023d9-5130-4eea-9de9-034f5bf0b145
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
req.alt-api: CcSetDirtyPageThreshold
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
req.irql: 
ms.keywords: CcSetDirtyPageThreshold
req.iface: 
---

# CcSetDirtyPageThreshold function



## -description
<p>The <b>CcSetDirtyPageThreshold</b> routine sets a per-file dirty page threshold on a cached file.</p>


## -syntax

````
VOID CcSetDirtyPageThreshold(
  _In_ PFILE_OBJECT FileObject,
  _In_ ULONG        DirtyPageThreshold
);
````


## -parameters
<dl>

### -param <i>FileObject</i> [in]

<dd>
<p>Pointer to a file object for the cached file on which the dirty page threshold is to be set.</p>
</dd>

### -param <i>DirtyPageThreshold</i> [in]

<dd>
<p>Specifies, as a number of pages, the dirty page threshold value. To remove a per-file dirty page threshold value that was set previously, set <i>DirtyPageThreshold</i> to zero.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p><b>CcSetDirtyPageThreshold</b> sets or removes a per-file dirty page threshold. After a per-file dirty page threshold is set on a cached file, if the file system attempts to exceed the threshold, the cache manager will refuse requests to write to the file.</p>

<p>To determine whether the cache manager will accept or refuse write requests, use <a href="https://msdn.microsoft.com/library/windows/hardware/ff539021">CcCanIWrite</a>.</p>

<p>Note that the <i>per-file</i> dirty page threshold is not the same as the <i>global</i> dirty page threshold for the entire system cache.</p>

<p><b>CcSetDirtyPageThreshold</b> sets or removes a per-file dirty page threshold. After a per-file dirty page threshold is set on a cached file, if the file system attempts to exceed the threshold, the cache manager will refuse requests to write to the file.</p>

<p>To determine whether the cache manager will accept or refuse write requests, use <a href="https://msdn.microsoft.com/library/windows/hardware/ff539021">CcCanIWrite</a>.</p>

<p>Note that the <i>per-file</i> dirty page threshold is not the same as the <i>global</i> dirty page threshold for the entire system cache.</p>

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
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539021">CcCanIWrite</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539060">CcDeferWrite</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20CcSetDirtyPageThreshold routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>