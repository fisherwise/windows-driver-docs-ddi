---
UID: NF.wdm.ObReleaseObjectSecurity
title: ObReleaseObjectSecurity
author: windows-driver-content
description: The ObReleaseObjectSecurity routine is the reciprocal to ObGetObjectSecurity.
old-location: kernel\obreleaseobjectsecurity.htm
ms.assetid: d4f9d02a-2541-445a-95f1-e08ebb0c8a39
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
req.alt-api: ObReleaseObjectSecurity
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: IrqlApcLte, HwStorPortProhibitedDDIs
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: <=APC_LEVEL
ms.keywords: ObReleaseObjectSecurity
req.iface: 
req.product: Windows 10 or later.
---

# ObReleaseObjectSecurity function



## -description
<p>The <b>ObReleaseObjectSecurity</b> routine is the reciprocal to <b>ObGetObjectSecurity</b>. </p>


## -syntax

````
VOID ObReleaseObjectSecurity(
  _In_ PSECURITY_DESCRIPTOR SecurityDescriptor,
  _In_ BOOLEAN              MemoryAllocated
);
````


## -parameters
<dl>

### -param <i>SecurityDescriptor</i> [in]

<dd>
<p>Pointer to the buffered <a href="https://msdn.microsoft.com/library/windows/hardware/ff563689">SECURITY_DESCRIPTOR</a> to be released. The caller obtained this parameter from <b>ObGetObjectSecurity</b></p>
</dd>

### -param <i>MemoryAllocated</i> [in]

<dd>
<p>Specifies the value also obtained from <b>ObGetObjectSecurity</b>. </p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>After a successful call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff557738">ObGetObjectSecurity</a>, a driver must call <b>ObReleaseObjectSecurity</b> eventually. </p>

<p><b>ObReleaseObjectSecurity</b> releases any resources that were allocated by <b>ObGetObjectSecurity</b>. It also decrements the reference count on the given security descriptor. </p>

<p>After a successful call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff557738">ObGetObjectSecurity</a>, a driver must call <b>ObReleaseObjectSecurity</b> eventually. </p>

<p><b>ObReleaseObjectSecurity</b> releases any resources that were allocated by <b>ObGetObjectSecurity</b>. It also decrements the reference count on the given security descriptor. </p>

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
<p>&lt;=APC_LEVEL</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547740">IrqlApcLte</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh454220">HwStorPortProhibitedDDIs</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563689">SECURITY_DESCRIPTOR</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff557738">ObGetObjectSecurity</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20ObReleaseObjectSecurity routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>