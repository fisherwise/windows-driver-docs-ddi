---
UID: NF.wdm.IoCsqInitialize
title: IoCsqInitialize
author: windows-driver-content
description: The IoCsqInitialize routine initializes the driver's cancel-safe IRP queue dispatch table.
old-location: kernel\iocsqinitialize.htm
ms.assetid: 5287db75-3096-45ab-b35b-1ee8b076157d
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: Available in Windows XP and later versions of the Windows operating system. Drivers that must also work for Windows 2000 and Windows 98/Me can instead link to Csq.lib to use the routine.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IoCsqInitialize
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
ms.keywords: IoCsqInitialize
req.iface: 
req.product: Windows 10 or later.
---

# IoCsqInitialize function



## -description
<p>The <b>IoCsqInitialize</b> routine initializes the driver's cancel-safe IRP queue dispatch table.</p>


## -syntax

````
NTSTATUS IoCsqInitialize(
  _Out_ PIO_CSQ                       Csq,
  _In_  PIO_CSQ_INSERT_IRP            CsqInsertIrp,
  _In_  PIO_CSQ_REMOVE_IRP            CsqRemoveIrp,
  _In_  PIO_CSQ_PEEK_NEXT_IRP         CsqPeekNextIrp,
  _In_  PIO_CSQ_ACQUIRE_LOCK          CsqAcquireLock,
  _In_  PIO_CSQ_RELEASE_LOCK          CsqReleaseLock,
  _In_  PIO_CSQ_COMPLETE_CANCELED_IRP CsqCompleteCanceledIrp
);
````


## -parameters
<dl>

### -param <i>Csq</i> [out]

<dd>
<p>Pointer to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff550560">IO_CSQ</a> structure to be initialized by <b>IoCsqInitialize</b>.</p>
</dd>

### -param <i>CsqInsertIrp</i> [in]

<dd>
<p>Pointer to the driver-defined <a href="https://msdn.microsoft.com/library/windows/hardware/ff542947">CsqInsertIrp</a> function for the driver's cancel-safe IRP queue.</p>
</dd>

### -param <i>CsqRemoveIrp</i> [in]

<dd>
<p>Pointer to the driver-defined <a href="https://msdn.microsoft.com/library/windows/hardware/ff542968">CsqRemoveIrp</a> function for the driver's cancel-safe IRP queue.</p>
</dd>

### -param <i>CsqPeekNextIrp</i> [in]

<dd>
<p>Pointer to the driver-defined <a href="https://msdn.microsoft.com/library/windows/hardware/ff542959">CsqPeekNextIrp</a> function for the driver's cancel-safe IRP queue.</p>
</dd>

### -param <i>CsqAcquireLock</i> [in]

<dd>
<p>Pointer to the driver-defined <a href="https://msdn.microsoft.com/library/windows/hardware/ff542934">CsqAcquireLock</a> function for the driver's cancel-safe IRP queue.</p>
</dd>

### -param <i>CsqReleaseLock</i> [in]

<dd>
<p>Pointer to the driver-defined <a href="https://msdn.microsoft.com/library/windows/hardware/ff542965">CsqReleaseLock</a> function for the driver's cancel-safe IRP queue.</p>
</dd>

### -param <i>CsqCompleteCanceledIrp</i> [in]

<dd>
<p>Pointer to the driver-defined <a href="https://msdn.microsoft.com/library/windows/hardware/ff542940">CsqCompleteCanceledIrp</a> function for the driver's cancel-safe IRP queue. </p>
</dd>
</dl>

## -returns
<p>This routine returns STATUS_SUCCESS on success, or the appropriate NTSTATUS error code on failure.</p>

## -remarks
<p>The <b>IoCsqInitialize</b> routine initializes an <a href="https://msdn.microsoft.com/library/windows/hardware/ff550560">IO_CSQ</a> structure that describes a driver's cancel-safe IRP queue. Drivers can also use <a href="https://msdn.microsoft.com/library/windows/hardware/ff549060">IoCsqInitializeEx</a> to create an IRP queue with extended capabilities. For more information, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff540755">Cancel-Safe IRP Queues</a>.</p>

<p>Note that <b>IoCsq<i>Xxx</i></b> routines use the <b>DriverContext</b>[3] member of the IRP to hold IRP context information. Drivers that use these routines to queue IRPs must leave that member unused.</p>

<p>The <b>IoCsqInitialize</b> routine initializes an <a href="https://msdn.microsoft.com/library/windows/hardware/ff550560">IO_CSQ</a> structure that describes a driver's cancel-safe IRP queue. Drivers can also use <a href="https://msdn.microsoft.com/library/windows/hardware/ff549060">IoCsqInitializeEx</a> to create an IRP queue with extended capabilities. For more information, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff540755">Cancel-Safe IRP Queues</a>.</p>

<p>Note that <b>IoCsq<i>Xxx</i></b> routines use the <b>DriverContext</b>[3] member of the IRP to hold IRP context information. Drivers that use these routines to queue IRPs must leave that member unused.</p>

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
<p>Available in Windows XP and later versions of the Windows operating system. Drivers that must also work for Windows 2000 and Windows 98/Me can instead link to Csq.lib to use the routine.</p>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550560">IO_CSQ</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549060">IoCsqInitializeEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549066">IoCsqInsertIrp</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549067">IoCsqInsertIrpEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549070">IoCsqRemoveIrp</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549072">IoCsqRemoveNextIrp</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542934">CsqAcquireLock</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542940">CsqCompleteCanceledIrp</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542947">CsqInsertIrp</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542956">CsqInsertIrpEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542959">CsqPeekNextIrp</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542965">CsqReleaseLock</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542968">CsqRemoveIrp</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20IoCsqInitialize routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>