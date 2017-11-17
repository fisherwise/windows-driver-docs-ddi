---
UID: NF.ntddk.RtlRunOnceInitialize
title: RtlRunOnceInitialize
author: windows-driver-content
description: The RtlRunOnceInitialize routine initializes a RTL_RUN_ONCE structure.
old-location: kernel\rtlrunonceinitialize.htm
ms.assetid: 4d1a65af-a475-4360-9db3-d5b9e302697d
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: ntddk.h
req.include-header: Ntddk.h
req.target-type: Universal
req.target-min-winverclnt: Available in Windows Vista and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RtlRunOnceInitialize
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
req.irql: <= APC_LEVEL
ms.keywords: RtlRunOnceInitialize
req.iface: 
---

# RtlRunOnceInitialize function



## -description
<p>The <b>RtlRunOnceInitialize</b> routine initializes a <a href="https://msdn.microsoft.com/library/windows/hardware/ff563626">RTL_RUN_ONCE</a> structure.</p>


## -syntax

````
VOID RtlRunOnceInitialize(
  _Out_ PRTL_RUN_ONCE RunOnce
);
````


## -parameters
<dl>

### -param <i>RunOnce</i> [out]

<dd>
<p>Pointer to the <b>RTL_RUN_ONCE</b> one-time initialization structure.</p>
</dd>
</dl>

## -returns
<p>None </p>

## -remarks


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
<p>Available in Windows Vista and later versions of Windows.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntddk.h (include Ntddk.h)</dt>
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
<p>&lt;= APC_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563626">RTL_RUN_ONCE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562759">RtlRunOnceBeginInitialize</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562763">RtlRunOnceComplete</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562765">RtlRunOnceExecuteOnce</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563635">RunOnceInitialization</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20RtlRunOnceInitialize routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>