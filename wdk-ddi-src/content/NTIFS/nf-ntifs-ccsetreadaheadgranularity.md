---
UID: NF.ntifs.CcSetReadAheadGranularity
title: CcSetReadAheadGranularity
author: windows-driver-content
description: The CcSetReadAheadGranularity routine sets the read-ahead granularity for a cached file.
old-location: ifsk\ccsetreadaheadgranularity.htm
ms.assetid: 3ab0c8b8-1f41-48b7-9c42-ea843ebcd82e
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
req.alt-api: CcSetReadAheadGranularity
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
ms.keywords: CcSetReadAheadGranularity
req.iface: 
---

# CcSetReadAheadGranularity function



## -description
<p>The <b>CcSetReadAheadGranularity</b> routine sets the read-ahead granularity for a cached file.</p>


## -syntax

````
VOID CcSetReadAheadGranularity(
  _In_ PFILE_OBJECT FileObject,
  _In_ ULONG        Granularity
);
````


## -parameters
<dl>

### -param <i>FileObject</i> [in]

<dd>
<p>Pointer to a file object for the cached file whose read-ahead granularity is to be set.</p>
</dd>

### -param <i>Granularity</i> [in]

<dd>
<p>Specifies the desired read-ahead granularity, which must be an even power of two and must be greater than or equal to PAGE_SIZE.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>After <a href="https://msdn.microsoft.com/library/windows/hardware/ff539135">CcInitializeCacheMap</a> is called to cache a file, but before <b>CcSetReadAheadGranularity</b> is called for the cached file, the default read-ahead granularity for the cached file is equal to PAGE_SIZE.</p>

<p>After <a href="https://msdn.microsoft.com/library/windows/hardware/ff539135">CcInitializeCacheMap</a> is called to cache a file, but before <b>CcSetReadAheadGranularity</b> is called for the cached file, the default read-ahead granularity for the cached file is equal to PAGE_SIZE.</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539135">CcInitializeCacheMap</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539191">CcReadAhead</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539200">CcScheduleReadAhead</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539203">CcSetAdditionalCacheAttributes</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20CcSetReadAheadGranularity routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>