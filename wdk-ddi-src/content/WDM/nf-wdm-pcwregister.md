---
UID: NF.wdm.PcwRegister
title: PcwRegister
author: windows-driver-content
description: The PcwRegister function registers the caller as a provider of the specified counter set.
old-location: devtest\pcwregister.htm
ms.assetid: 40fdb77c-bd6b-4ecd-a9c8-fd5e5b2adc80
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: devtest
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h
req.target-type: Universal
req.target-min-winverclnt: Available in Windows 7 and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: PcwRegister
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
req.irql: <=APC_LEVEL
ms.keywords: PcwRegister
req.iface: 
req.product: Windows 10 or later.
---

# PcwRegister function



## -description
<p>The <b>PcwRegister</b> function registers the caller as a provider of the specified counter set.</p>


## -syntax

````
NTSTATUS PcwRegister(
  _Out_ PPCW_REGISTRATION             *Registration,
  _In_  PPCW_REGISTRATION_INFORMATION Info
);
````


## -parameters
<dl>

### -param <i>Registration</i> [out]

<dd>
<p>A pointer to a PCW_REGISTRATION structure. Receives the handle to the newly allocated registration. The pointer is referenced before the function returns. The caller is responsible to dereference the pointer.</p>
</dd>

### -param <i>Info</i> [in]

<dd>
<p>A pointer to a PCW_REGISTRATION_INFORMATION structure that contains the details about the counter set being registered.</p>
</dd>
</dl>

## -returns
<p>This function returns one of the following values:</p><dl>
<dt><b>STATUS_SUCCESS</b></dt>
</dl><p>The counter set is successfully registered.</p><dl>
<dt><b>STATUS_INVALID_PARAMETER_2</b></dt>
</dl><p>The <i>Version</i> specified by <i>Info</i> does not match the supported value for this version of Windows.</p><dl>
<dt><b>STATUS_INTEGER_OVERFLOW</b></dt>
</dl><p>The number of the counters exposed by this registration exceeds the space available.</p><dl>
<dt><b>STATUS_NO_MEMORY</b></dt>
</dl><p>There is not enough space available to allocate memory for the counters</p>

<p> </p>

## -remarks
<p>The provider calls this function to create a new registration. The registration is added to the counter set's registration list. All the input arguments are captured so that the caller does not have to keep a copy of them.</p>

<p>The provider calls this function to create a new registration. The registration is added to the counter set's registration list. All the input arguments are captured so that the caller does not have to keep a copy of them.</p>

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
<p>Available in Windows 7 and later versions of Windows.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdm.h (include Wdm.h or Ntddk.h)</dt>
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
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550326">PcwUnregister</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [devtest\devtest]:%20PcwRegister function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>