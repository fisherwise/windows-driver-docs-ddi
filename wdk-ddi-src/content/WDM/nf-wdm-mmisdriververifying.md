---
UID: NF.wdm.MmIsDriverVerifying
title: MmIsDriverVerifying
author: windows-driver-content
description: The MmIsDriverVerifying routine indicates whether the kernel-mode driver that is identified by the specified driver object is being verified or calls a driver that is being verified by Driver Verifier.
old-location: kernel\mmisdriververifying.htm
ms.assetid: 74bfe9fb-f751-46a6-a95b-f715ebedd2ec
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
req.alt-api: MmIsDriverVerifying
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
ms.keywords: MmIsDriverVerifying
req.iface: 
req.product: Windows 10 or later.
---

# MmIsDriverVerifying function



## -description
<p>The <b>MmIsDriverVerifying</b> routine indicates whether the kernel-mode driver that is identified by the specified <a href="https://msdn.microsoft.com/497ee2dc-671d-408e-b228-16dc24532375">driver object</a> is being verified or calls a driver that is being verified by <a href="https://msdn.microsoft.com/library/windows/hardware/ff557262">Driver Verifier</a>.</p>


## -syntax

````
LOGICAL MmIsDriverVerifying(
  _In_ struct _DRIVER_OBJECT *DriverObject
);
````


## -parameters
<dl>

### -param <i>DriverObject</i> [in]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff544174">DRIVER_OBJECT</a> structure that represents a driver object. The driver receives this pointer as an input parameter to its <a href="https://msdn.microsoft.com/library/windows/hardware/ff552644">DriverEntry</a> routine. </p>
</dd>
</dl>

## -returns
<p><b>MmIsDriverVerifying</b> returns <b>TRUE</b> if the specified driver either is in the driver verification list or imports calls to entry points in a driver that is in the driver verification list. Otherwise, this routine returns <b>FALSE</b>.</p>

## -remarks
<p>A kernel-mode driver can call this routine to determine whether it is being monitored by <a href="https://msdn.microsoft.com/library/windows/hardware/ff557262">Driver Verifier</a>. Driver Verifier monitors kernel-mode drivers to detect illegal function calls or actions that might corrupt the system. To select drivers to be verified, you can use the <a href="https://msdn.microsoft.com/7cdf5277-7187-4e90-b22a-6f828f06e2fb">Verifier Command Line</a> or <a href="https://msdn.microsoft.com/37a7d348-8b55-44f7-86d6-6b195704b9fd">Driver Verifier Manager</a>. For more information about adding drivers to the driver verification list, see <a href="NULL">Selecting Drivers to be Verified</a>.</p>

<p>A similar routine, <a href="https://msdn.microsoft.com/library/windows/hardware/ff554583">MmIsDriverVerifyingByAddress</a>, indicates whether a driver identified by a driver image address is being verified or calls a driver that is being verified. <b>MmIsDriverVerifyingByAddress</b> is available starting with Windows Vista.</p>

<p>Another related routine, <a href="https://msdn.microsoft.com/library/windows/hardware/jj552960">MmIsDriverSuspectForVerifier</a>, indicates whether a driver represented by a <a href="https://msdn.microsoft.com/497ee2dc-671d-408e-b228-16dc24532375">driver object</a> is in the list of drivers that are selected to be verified. <b>MmIsDriverSuspectForVerifier</b> is available starting with Windows 8.</p>

<p>For example, if driver A has an import table through which it calls one or more entry points in driver B, and driver B is in the driver verification list, then <code>MmIsDriverVerifying(A)</code> returns <b>TRUE</b> and <code>MmIsDriverSuspectForVerifier(B)</code> returns <b>TRUE</b>. If driver A is not in the driver verification list, <code>MmIsDriverSuspectForVerifier(A)</code> returns <b>FALSE</b>. Even if driver B does not call entry points in any drivers that are in the driver verification list, <code>MmIsDriverVerifying(B)</code> returns <b>TRUE</b> because driver B is in the driver verification list. If a driver C is not in the driver verification list and does not call entry points in any drivers that are in the driver verification list, <code>MmIsDriverVerifying(C)</code> and <code>MmIsDriverSuspectForVerifier(C)</code> both return <b>FALSE</b>.</p>

<p>A kernel-mode driver can call this routine to determine whether it is being monitored by <a href="https://msdn.microsoft.com/library/windows/hardware/ff557262">Driver Verifier</a>. Driver Verifier monitors kernel-mode drivers to detect illegal function calls or actions that might corrupt the system. To select drivers to be verified, you can use the <a href="https://msdn.microsoft.com/7cdf5277-7187-4e90-b22a-6f828f06e2fb">Verifier Command Line</a> or <a href="https://msdn.microsoft.com/37a7d348-8b55-44f7-86d6-6b195704b9fd">Driver Verifier Manager</a>. For more information about adding drivers to the driver verification list, see <a href="NULL">Selecting Drivers to be Verified</a>.</p>

<p>A similar routine, <a href="https://msdn.microsoft.com/library/windows/hardware/ff554583">MmIsDriverVerifyingByAddress</a>, indicates whether a driver identified by a driver image address is being verified or calls a driver that is being verified. <b>MmIsDriverVerifyingByAddress</b> is available starting with Windows Vista.</p>

<p>Another related routine, <a href="https://msdn.microsoft.com/library/windows/hardware/jj552960">MmIsDriverSuspectForVerifier</a>, indicates whether a driver represented by a <a href="https://msdn.microsoft.com/497ee2dc-671d-408e-b228-16dc24532375">driver object</a> is in the list of drivers that are selected to be verified. <b>MmIsDriverSuspectForVerifier</b> is available starting with Windows 8.</p>

<p>For example, if driver A has an import table through which it calls one or more entry points in driver B, and driver B is in the driver verification list, then <code>MmIsDriverVerifying(A)</code> returns <b>TRUE</b> and <code>MmIsDriverSuspectForVerifier(B)</code> returns <b>TRUE</b>. If driver A is not in the driver verification list, <code>MmIsDriverSuspectForVerifier(A)</code> returns <b>FALSE</b>. Even if driver B does not call entry points in any drivers that are in the driver verification list, <code>MmIsDriverVerifying(B)</code> returns <b>TRUE</b> because driver B is in the driver verification list. If a driver C is not in the driver verification list and does not call entry points in any drivers that are in the driver verification list, <code>MmIsDriverVerifying(C)</code> and <code>MmIsDriverSuspectForVerifier(C)</code> both return <b>FALSE</b>.</p>

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
<p>&lt;= APC_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552644">DriverEntry</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544174">DRIVER_OBJECT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554583">MmIsDriverVerifyingByAddress</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20MmIsDriverVerifying routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>