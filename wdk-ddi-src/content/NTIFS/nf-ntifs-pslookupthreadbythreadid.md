---
UID: NF.ntifs.PsLookupThreadByThreadId
title: PsLookupThreadByThreadId
author: windows-driver-content
description: The PsLookupThreadByThreadId routine accepts the thread ID of a thread and returns a referenced pointer to the ETHREAD structure of the thread.
old-location: ifsk\pslookupthreadbythreadid.htm
ms.assetid: 4b61f480-6432-48db-9211-68a7d823d698
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
req.alt-api: PsLookupThreadByThreadId
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
ms.keywords: PsLookupThreadByThreadId
req.iface: 
---

# PsLookupThreadByThreadId function



## -description
<p>The <b>PsLookupThreadByThreadId</b> routine accepts the thread ID of a thread and returns a referenced pointer to the ETHREAD structure of the thread.</p>


## -syntax

````
NTSTATUS PsLookupThreadByThreadId(
  _In_  HANDLE   ThreadId,
  _Out_ PETHREAD *Thread
);
````


## -parameters
<dl>

### -param <i>ThreadId</i> [in]

<dd>
<p>Specifies the thread ID of the thread.</p>
</dd>

### -param <i>Thread</i> [out]

<dd>
<p>Returns a referenced pointer to the ETHREAD structure of thread specified by the <i>ThreadId</i>.</p>
</dd>
</dl>

## -returns
<p><b>PsLookupThreadByThreadId </b>returns STATUS_SUCCESS on success or an appropriate NTSTATUS value, such as: </p><dl>
<dt><b>STATUS_INVALID_PARAMETER</b></dt>
</dl><p>The thread ID was not found.</p>

<p> </p>

## -remarks
<p>This routine is available on Windows 2000 and later versions. </p>

<p>If the call to <b>PsLookupThreadByThreadId</b> is successful, <b>PsLookupThreadByThreadId</b> increases the reference count on the object returned in the <i>Thread</i> parameter. Consequently, when a driver has completed using the <i>Thread</i> parameter, the driver must call <a href="https://msdn.microsoft.com/library/windows/hardware/ff557724">ObDereferenceObject</a> to dereference the <i>Thread</i> parameter received from the <b>PsLookupThreadByThreadId</b> routine. </p>

<p>The ETHREAD structure is an opaque data structure used internally by the operating system. This structure can be passed to other routines to access specific information in this structure.</p>

<p>A file system filter driver can enumerate active threads by calling <b>PsLookupThreadByThreadId</b> to convert a thread ID to an ETHREAD structure. The thread ID is available in the thread create routine. A file system filter driver can set a thread notification callback routine using <a href="https://msdn.microsoft.com/library/windows/hardware/ff559954">PsSetCreateThreadNotifyRoutine</a>. In the notification callback routine, the file system filter driver can use the passed in <i>ThreadId</i> parameter and call <b>PsLookupThreadByThreadId </b>to locate the ETHREAD structure.</p>

<p>The <b>PsLookupThreadByThreadId</b> routine contains pageable code. </p>

<p>This routine is available on Windows 2000 and later versions. </p>

<p>If the call to <b>PsLookupThreadByThreadId</b> is successful, <b>PsLookupThreadByThreadId</b> increases the reference count on the object returned in the <i>Thread</i> parameter. Consequently, when a driver has completed using the <i>Thread</i> parameter, the driver must call <a href="https://msdn.microsoft.com/library/windows/hardware/ff557724">ObDereferenceObject</a> to dereference the <i>Thread</i> parameter received from the <b>PsLookupThreadByThreadId</b> routine. </p>

<p>The ETHREAD structure is an opaque data structure used internally by the operating system. This structure can be passed to other routines to access specific information in this structure.</p>

<p>A file system filter driver can enumerate active threads by calling <b>PsLookupThreadByThreadId</b> to convert a thread ID to an ETHREAD structure. The thread ID is available in the thread create routine. A file system filter driver can set a thread notification callback routine using <a href="https://msdn.microsoft.com/library/windows/hardware/ff559954">PsSetCreateThreadNotifyRoutine</a>. In the notification callback routine, the file system filter driver can use the passed in <i>ThreadId</i> parameter and call <b>PsLookupThreadByThreadId </b>to locate the ETHREAD structure.</p>

<p>The <b>PsLookupThreadByThreadId</b> routine contains pageable code. </p>

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
<p>&lt;= APC_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff557724">ObDereferenceObject</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff559933">PsGetCurrentProcess</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff559935">PsGetCurrentProcessId</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff559936">PsGetCurrentThread</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff559937">PsGetCurrentThreadId</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551920">PsLookupProcessByProcessId</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff559947">PsRemoveCreateThreadNotifyRoutine</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff559949">PsRemoveLoadImageNotifyRoutine</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff559954">PsSetCreateThreadNotifyRoutine</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff559957">PsSetLoadImageNotifyRoutine</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20PsLookupThreadByThreadId routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>