---
UID: NF.ntddk.IoGetPagingIoPriority
title: IoGetPagingIoPriority
author: windows-driver-content
description: The IoGetPagingIoPriority routine indicates the priority level of a paging I/O request.
old-location: kernel\iogetpagingiopriority.htm
ms.assetid: 3b0f4fc9-58fd-46ba-be17-2e1b36b16caa
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: ntddk.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: Available in Microsoft Windows Server 2003 and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IoGetPagingIoPriority
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
ms.keywords: IoGetPagingIoPriority
req.iface: 
---

# IoGetPagingIoPriority function



## -description
<p>The <b>IoGetPagingIoPriority</b> routine indicates the priority level of a paging I/O request.</p>


## -syntax

````
IO_PAGING_PRIORITY IoGetPagingIoPriority(
  _In_ PIRP Irp
);
````


## -parameters
<dl>

### -param <i>Irp</i> [in]

<dd>
<p>Pointer to the IRP to be tested for paging priority.</p>
</dd>
</dl>

## -returns
<p><b>IoGetPagingIoPriority</b> returns the <a href="https://msdn.microsoft.com/library/windows/hardware/ff550590">IO_PAGING_PRIORITY</a> value for the associated IRP.</p>

## -remarks
<p>For I/O requests that causing paging, the system associates an <b>IO_PAGING_PRIORITY</b> value that describes the IRP's priority. Drivers can use this value when queuing IRPs.</p>

<p>For I/O requests that causing paging, the system associates an <b>IO_PAGING_PRIORITY</b> value that describes the IRP's priority. Drivers can use this value when queuing IRPs.</p>

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
<p>Available in Microsoft Windows Server 2003 and later versions of Windows.</p>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550590">IO_PAGING_PRIORITY</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20IoGetPagingIoPriority routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>