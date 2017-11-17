---
UID: NF.wdm.MmProtectMdlSystemAddress
title: MmProtectMdlSystemAddress
author: windows-driver-content
description: The MmProtectMdlSystemAddress routine sets the protection type for a memory address range.
old-location: kernel\mmprotectmdlsystemaddress.htm
ms.assetid: e0ccc6e8-9351-4440-808b-e0b8eef48bc2
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: Available in Windows XP and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: MmProtectMdlSystemAddress
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
req.irql: <=DISPATCH_LEVEL
ms.keywords: MmProtectMdlSystemAddress
req.iface: 
req.product: Windows 10 or later.
---

# MmProtectMdlSystemAddress function



## -description
<p>The <b>MmProtectMdlSystemAddress</b> routine sets the protection type for a memory address range.</p>


## -syntax

````
NTSTATUS MmProtectMdlSystemAddress(
  _In_ PMDLX MemoryDescriptorList,
  _In_ ULONG NewProtect
);
````


## -parameters
<dl>

### -param <i>MemoryDescriptorList</i> [in]

<dd>
<p>Specifies the memory address range to set the protection type for. </p>
</dd>

### -param <i>NewProtect</i> [in]

<dd>
<p>Specifies the new protection setting for the memory pages. Drivers should specify one of the following values:</p>
<p></p>
<dl>

### -param <a id="PAGE_NOACCESS"></a><a id="page_noaccess"></a>PAGE_NOACCESS

<dd>
<p>The underlying memory pages cannot be read or written. </p>
</dd>

### -param <a id="PAGE_READONLY"></a><a id="page_readonly"></a>PAGE_READONLY

<dd>
<p>The underlying memory pages can only be read, not written. </p>
</dd>

### -param <a id="PAGE_READWRITE"></a><a id="page_readwrite"></a>PAGE_READWRITE

<dd>
<p>The underlying memory pages can be read or written. </p>
</dd>

### -param <a id="PAGE_EXECUTE"></a><a id="page_execute"></a>PAGE_EXECUTE

<dd>
<p>The underlying memory pages can be executed, but not read or written.</p>
</dd>

### -param <a id="PAGE_EXECUTE_READ"></a><a id="page_execute_read"></a>PAGE_EXECUTE_READ

<dd>
<p>The underlying memory pages can be executed or read, but not written.</p>
</dd>

### -param <a id="PAGE_EXECUTE_READWRITE"></a><a id="page_execute_readwrite"></a>PAGE_EXECUTE_READWRITE

<dd>
<p>The underlying memory pages can be executed, read, or written.</p>
</dd>
</dl>
</dd>
</dl>

## -returns
<p><b>MmProtectMdlSystemAddress</b> returns an NTSTATUS code. The possible return values include:</p><dl>
<dt><b>STATUS_SUCCESS</b></dt>
</dl><p>The routine successfully changed the protection type for the memory address range.</p><dl>
<dt><b>STATUS_INVALID_PAGE_PROTECTION</b></dt>
</dl><p>The value specified for <i>NewProtect</i> is not a valid one for this routine.</p><dl>
<dt><b>STATUS_NOT_MAPPED_VIEW</b></dt>
</dl><p>The MDL has not yet been mapped. <b>MmProtectMdlSystemAddress</b> can only be used on MDLs that have already been mapped.</p>

<p> </p>

## -remarks
<p>The <b>MmProtectMdlSystemAddress</b> routine can only be called on an MDL that has already been mapped. For example, the routine can be called on an MDL mapped by <a href="https://msdn.microsoft.com/library/windows/hardware/ff554629">MmMapLockedPagesSpecifyCache</a>. </p>

<p>The <b>MmProtectMdlSystemAddress</b> routine can only be called on an MDL that has already been mapped. For example, the routine can be called on an MDL mapped by <a href="https://msdn.microsoft.com/library/windows/hardware/ff554629">MmMapLockedPagesSpecifyCache</a>. </p>

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
<p>Available in Windows XP and later versions of Windows.</p>
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
<p>&lt;=DISPATCH_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554629">MmMapLockedPagesSpecifyCache</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20MmProtectMdlSystemAddress routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>