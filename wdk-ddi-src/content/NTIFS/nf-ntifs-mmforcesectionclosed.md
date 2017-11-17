---
UID: NF.ntifs.MmForceSectionClosed
title: MmForceSectionClosed
author: windows-driver-content
description: The MmForceSectionClosed routine deletes the data and image sections for a file that is no longer in use.
old-location: ifsk\mmforcesectionclosed.htm
ms.assetid: aa598c4b-e840-41cb-81a3-719a5b1ee48b
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
req.alt-api: MmForceSectionClosed
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
ms.keywords: MmForceSectionClosed
req.iface: 
---

# MmForceSectionClosed function



## -description
<p>The <b>MmForceSectionClosed</b> routine deletes the data and image sections for a file that is no longer in use. </p>


## -syntax

````
BOOLEAN MmForceSectionClosed(
  _In_ PSECTION_OBJECT_POINTERS SectionObjectPointer,
  _In_ BOOLEAN                  DelayClose
);
````


## -parameters
<dl>

### -param <i>SectionObjectPointer</i> [in]

<dd>
<p>A pointer to a structure that contains the file object's section object pointers.</p>
</dd>

### -param <i>DelayClose</i> [in]

<dd>
<p>A Boolean value that specifies whether the section is subsequently deleted if <b>MmForceSectionClosed</b> cannot delete the section synchronously (that is, prior to <b>MmForceSectionClosed</b> returning). </p>
<p><b>TRUE</b> indicates that if <b>MmForceSectionClosed</b> cannot delete the section synchronously, <b>MmForceSectionClosed</b> sets a flag. With this flag set, when the section's outstanding reference count reaches zero, the memory manager deletes the section automatically. </p>
<p><b>FALSE</b> indicates that if <b>MmForceSectionClosed</b> cannot delete the section synchronously, the section is not deleted.</p>
</dd>
</dl>

## -returns
<p><b>MmForceSectionClosed</b> returns <b>TRUE</b> if the sections were successfully deleted or no sections were found, <b>FALSE</b> otherwise.</p>

## -remarks
<p>For more information about creating mapped sections and views of memory, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563682">Sections and Views</a>.</p>

<p>For more information about creating mapped sections and views of memory, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563682">Sections and Views</a>.</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539188">CcPurgeCacheSection</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549808">MmFlushImageSection</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20MmForceSectionClosed routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>