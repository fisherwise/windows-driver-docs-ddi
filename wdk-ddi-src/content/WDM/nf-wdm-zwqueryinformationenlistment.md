---
UID: NF.wdm.ZwQueryInformationEnlistment
title: ZwQueryInformationEnlistment
author: windows-driver-content
description: The ZwQueryInformationEnlistment routine retrieves information about a specified enlistment object.
old-location: kernel\zwqueryinformationenlistment.htm
ms.assetid: d8aa5227-7150-4fb1-a8ab-cb0f8ae4f74a
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: Available in Windows Vista and later operating system versions.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: ZwQueryInformationEnlistment,NtQueryInformationEnlistment
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: PowerIrpDDis, HwStorPortProhibitedDDIs
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: PASSIVE_LEVEL
ms.keywords: ZwQueryInformationEnlistment
req.iface: 
req.product: Windows 10 or later.
---

# ZwQueryInformationEnlistment function



## -description
<p>The <b>ZwQueryInformationEnlistment</b> routine retrieves information about a specified <a href="https://msdn.microsoft.com/80e61475-4bb7-4eaa-b9f1-ff95eac9bc77">enlistment object</a>.</p>


## -syntax

````
NTSTATUS ZwQueryInformationEnlistment(
  _In_      HANDLE                       EnlistmentHandle,
  _In_      ENLISTMENT_INFORMATION_CLASS EnlistmentInformationClass,
  _Out_     PVOID                        EnlistmentInformation,
  _In_      ULONG                        EnlistmentInformationLength,
  _Out_opt_ PULONG                       ReturnLength
);
````


## -parameters
<dl>

### -param <i>EnlistmentHandle</i> [in]

<dd>
<p>A handle to an enlistment object that was obtained by a previous call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff566422">ZwCreateEnlistment</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff567008">ZwOpenEnlistment</a>. The handle must have ENLISTMENT_QUERY_INFORMATION access to the object.</p>
</dd>

### -param <i>EnlistmentInformationClass</i> [in]

<dd>
<p>An <a href="https://msdn.microsoft.com/library/windows/hardware/ff544260">ENLISTMENT_INFORMATION_CLASS</a>-typed enumeration value that specifies the information to be obtained. This value must be one of the following values:</p>
<ul>
<li>
<p><b>EnlistmentBasicInformation</b></p>
</li>
<li>
<p><b>EnlistmentRecoveryInformation</b></p>
</li>
</ul>
<p>The enumeration's <b>EnlistmentFullInformation</b> value is not used with <b>ZwQueryInformationEnlistment</b>. </p>
</dd>

### -param <i>EnlistmentInformation</i> [out]

<dd>
<p>A pointer to a caller-allocated buffer that receives the information that the <i>EnlistmentInformationClass </i>parameter specifies. If the <i>EnlistmentInformationClass</i> parameter's value is <b>EnlistmentBasicInformation</b>, this buffer's structure type must be <a href="https://msdn.microsoft.com/library/windows/hardware/ff544254">ENLISTMENT_BASIC_INFORMATION</a>. If the <i>EnlistmentInformationClass</i> parameter's value is <b>EnlistmentRecoveryInformation</b>, this buffer's type must match the caller-defined type that the caller used when it called <a href="https://msdn.microsoft.com/library/windows/hardware/ff567094">ZwSetInformationEnlistment</a>.</p>
</dd>

### -param <i>EnlistmentInformationLength</i> [in]

<dd>
<p>The length, in bytes, of the buffer that the <i>EnlistmentInformation</i> parameter points to.</p>
</dd>

### -param <i>ReturnLength</i> [out, optional]

<dd>
<p>A pointer to a caller-allocated variable that receives the length, in bytes, of the information that KTM writes to the <i>EnlistmentInformation </i>buffer. This parameter is optional and can be <b>NULL</b>.</p>
</dd>
</dl>

## -returns
<p><b>ZwQueryInformationEnlistment</b> returns STATUS_SUCCESS if the operation succeeds. Otherwise, this routine might return one of the following values: </p><dl>
<dt><b>STATUS_OBJECT_TYPE_MISMATCH</b></dt>
</dl><p>The specified handle is not a handle to an enlistment object.</p><dl>
<dt><b>STATUS_INVALID_HANDLE</b></dt>
</dl><p>The object handle is invalid.</p><dl>
<dt><b>STATUS_INVALID_INFO_CLASS</b></dt>
</dl><p>The <i>EnlistmentInformationClass</i> parameter's value is invalid.</p><dl>
<dt><b>STATUS_INFO_LENGTH_MISMATCH</b></dt>
</dl><p>The <i>EnlistmentInformationLength</i> parameter's value is invalid.</p><dl>
<dt><b>STATUS_ACCESS_DENIED</b></dt>
</dl><p>The caller does not have appropriate access to the enlistment object.</p>

<p> </p>

<p>The routine might return other <a href="https://msdn.microsoft.com/library/windows/hardware/ff557697">NTSTATUS values</a>.</p>

## -remarks
<p>A resource manager can call <a href="https://msdn.microsoft.com/library/windows/hardware/ff567094">ZwSetInformationEnlistment</a> to set enlistment-specific recovery information for an enlistment object and then call <b>ZwQueryInformationEnlistment</b> to retrieve the recovery information.</p>

<p>For more information about <b>ZwQueryInformationEnlistment</b>, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff546922">Handling Recovery Operations</a>.</p>

<p>Callers of <b>ZwQueryInformationEnlistment</b> must be running at IRQL = PASSIVE_LEVEL.</p>

<p><b>NtQueryInformationEnlistment</b> and <b>ZwQueryInformationEnlistment</b> are two versions of the same Windows Native System Services routine.</p>

<p>For calls from kernel-mode drivers, the <b>Nt<i>Xxx</i></b> and <b>Zw<i>Xxx</i></b> versions of a Windows Native System Services routine can behave differently in the way that they handle and interpret input parameters. For more information about the relationship between the <b>Nt<i>Xxx</i></b> and <b>Zw<i>Xxx</i></b> versions of a routine, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff565438">Using Nt and Zw Versions of the Native System Services Routines</a>.</p>

<p>A resource manager can call <a href="https://msdn.microsoft.com/library/windows/hardware/ff567094">ZwSetInformationEnlistment</a> to set enlistment-specific recovery information for an enlistment object and then call <b>ZwQueryInformationEnlistment</b> to retrieve the recovery information.</p>

<p>For more information about <b>ZwQueryInformationEnlistment</b>, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff546922">Handling Recovery Operations</a>.</p>

<p>Callers of <b>ZwQueryInformationEnlistment</b> must be running at IRQL = PASSIVE_LEVEL.</p>

<p><b>NtQueryInformationEnlistment</b> and <b>ZwQueryInformationEnlistment</b> are two versions of the same Windows Native System Services routine.</p>

<p>For calls from kernel-mode drivers, the <b>Nt<i>Xxx</i></b> and <b>Zw<i>Xxx</i></b> versions of a Windows Native System Services routine can behave differently in the way that they handle and interpret input parameters. For more information about the relationship between the <b>Nt<i>Xxx</i></b> and <b>Zw<i>Xxx</i></b> versions of a routine, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff565438">Using Nt and Zw Versions of the Native System Services Routines</a>.</p>

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
<p>Available in Windows Vista and later operating system versions.</p>
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
<p>PASSIVE_LEVEL</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/hh975204">PowerIrpDDis</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh454220">HwStorPortProhibitedDDIs</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544254">ENLISTMENT_BASIC_INFORMATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544260">ENLISTMENT_INFORMATION_CLASS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff565438">Using Nt and Zw Versions of the Native System Services Routines</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff566422">ZwCreateEnlistment</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567008">ZwOpenEnlistment</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567094">ZwSetInformationEnlistment</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20ZwQueryInformationEnlistment routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>