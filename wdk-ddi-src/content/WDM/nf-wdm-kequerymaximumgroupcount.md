---
UID: NF.wdm.KeQueryMaximumGroupCount
title: KeQueryMaximumGroupCount
author: windows-driver-content
description: The KeQueryMaximumGroupCount routine returns the maximum number of groups in a multiprocessor system.
old-location: kernel\kequerymaximumgroupcount.htm
ms.assetid: b5cf231b-1a78-485f-bf26-fe50fbe63d08
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: Available in Windows 7 and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: KeQueryMaximumGroupCount
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
req.irql: Any level
ms.keywords: KeQueryMaximumGroupCount
req.iface: 
req.product: Windows 10 or later.
---

# KeQueryMaximumGroupCount function



## -description
<p>The <b>KeQueryMaximumGroupCount</b> routine returns the maximum number of groups in a multiprocessor system.</p>


## -syntax

````
USHORT KeQueryMaximumGroupCount(void);
````


## -parameters


## -returns
<p><b>KeQueryMaximumGroupCount</b> returns the maximum number of groups. </p>

<p><b>KeQueryMaximumGroupCount</b> returns the maximum number of groups. </p>

<p><b>KeQueryMaximumGroupCount</b> returns the maximum number of groups. </p>

## -remarks
<p>The value that is returned by <b>KeQueryMaximumGroupCount</b> remains constant during runtime. This value depends on the hardware configuration of the multiprocessor system, but it can never exceed a fixed limit that is set by the Windows operating system.</p>

<p>In Windows 7, the maximum number of groups in a multiprocessor system is four, but this value might change in future versions of Windows. The safest way to determine the maximum number of groups in Windows 7 or a later versions of the Windows operating system is to call <b>KeQueryMaximumGroupCount</b>. Kernel-mode drivers that call <b>KeQueryMaximumGroupCount</b> will not require code changes if the formula that is used to calculate the maximum number of groups changes in a future version of Windows.</p>

<p>To obtain the number of active groups in a multiprocessor system, call the <a href="https://msdn.microsoft.com/library/windows/hardware/ff552981">KeQueryActiveGroupCount</a> routine.</p>

<p>The value that is returned by <b>KeQueryMaximumGroupCount</b> remains constant during runtime. This value depends on the hardware configuration of the multiprocessor system, but it can never exceed a fixed limit that is set by the Windows operating system.</p>

<p>In Windows 7, the maximum number of groups in a multiprocessor system is four, but this value might change in future versions of Windows. The safest way to determine the maximum number of groups in Windows 7 or a later versions of the Windows operating system is to call <b>KeQueryMaximumGroupCount</b>. Kernel-mode drivers that call <b>KeQueryMaximumGroupCount</b> will not require code changes if the formula that is used to calculate the maximum number of groups changes in a future version of Windows.</p>

<p>To obtain the number of active groups in a multiprocessor system, call the <a href="https://msdn.microsoft.com/library/windows/hardware/ff552981">KeQueryActiveGroupCount</a> routine.</p>

<p>The value that is returned by <b>KeQueryMaximumGroupCount</b> remains constant during runtime. This value depends on the hardware configuration of the multiprocessor system, but it can never exceed a fixed limit that is set by the Windows operating system.</p>

<p>In Windows 7, the maximum number of groups in a multiprocessor system is four, but this value might change in future versions of Windows. The safest way to determine the maximum number of groups in Windows 7 or a later versions of the Windows operating system is to call <b>KeQueryMaximumGroupCount</b>. Kernel-mode drivers that call <b>KeQueryMaximumGroupCount</b> will not require code changes if the formula that is used to calculate the maximum number of groups changes in a future version of Windows.</p>

<p>To obtain the number of active groups in a multiprocessor system, call the <a href="https://msdn.microsoft.com/library/windows/hardware/ff552981">KeQueryActiveGroupCount</a> routine.</p>

<p>The value that is returned by <b>KeQueryMaximumGroupCount</b> remains constant during runtime. This value depends on the hardware configuration of the multiprocessor system, but it can never exceed a fixed limit that is set by the Windows operating system.</p>

<p>In Windows 7, the maximum number of groups in a multiprocessor system is four, but this value might change in future versions of Windows. The safest way to determine the maximum number of groups in Windows 7 or a later versions of the Windows operating system is to call <b>KeQueryMaximumGroupCount</b>. Kernel-mode drivers that call <b>KeQueryMaximumGroupCount</b> will not require code changes if the formula that is used to calculate the maximum number of groups changes in a future version of Windows.</p>

<p>To obtain the number of active groups in a multiprocessor system, call the <a href="https://msdn.microsoft.com/library/windows/hardware/ff552981">KeQueryActiveGroupCount</a> routine.</p>

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
<p>Available in Windows 7 and later versions of Windows. </p>
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
<p>Any level</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552981">KeQueryActiveGroupCount</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20KeQueryMaximumGroupCount routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>