---
UID: NS.parallel._PARALLEL_INTERRUPT_INFORMATION
title: PARALLEL_INTERRUPT_INFORMATION
author: windows-driver-content
description: The PARALLEL_INTERRUPT_INFORMATION structure specifies information that a kernel-mode driver can use in the context of an ISR that the driver connects to a parallel port.
old-location: parports\parallel_interrupt_information.htm
ms.assetid: aa4baa12-c349-4961-9694-b8fb3cd8dc50
ms.author: windowsdriverdev
ms.date: 10/23/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: parports
req.header: parallel.h
req.include-header: Parallel.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: PARALLEL_INTERRUPT_INFORMATION
req.alt-loc: parallel.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: 
ms.keywords: PARALLEL_INTERRUPT_INFORMATION, PARALLEL_INTERRUPT_INFORMATION, *PPARALLEL_INTERRUPT_INFORMATION
req.iface: 
---

# PARALLEL_INTERRUPT_INFORMATION structure



## -description
<p>The PARALLEL_INTERRUPT_INFORMATION structure specifies information that a kernel-mode driver can use in the context of an ISR that the driver connects to a parallel port.</p>


## -syntax

````
typedef struct _PARALLEL_INTERRUPT_INFORMATION {
  PKINTERRUPT                    InterruptObject;
  PPARALLEL_TRY_ALLOCATE_ROUTINE TryAllocatePortAtInterruptLevel;
  PPARALLEL_FREE_ROUTINE         FreePortFromInterruptLevel;
  PVOID                          Context;
} PARALLEL_INTERRUPT_INFORMATION, *PPARALLEL_INTERRUPT_INFORMATION;
````


## -struct-fields
<dl>

### -field <b>InterruptObject</b>

<dd>
<p>Pointer to the parallel port interrupt object.</p>
</dd>

### -field <b>TryAllocatePortAtInterruptLevel</b>

<dd>
<p>Pointer to the system-supplied <a href="https://msdn.microsoft.com/bc69e347-8ef7-4a80-9ef4-bbc03f5586c4">PPARALLEL_TRY_ALLOCATE_ROUTINE (ISR)</a> callback routine that a kernel-mode driver can use to attempt to allocate the parallel port at IRQL = DIRQL.</p>
</dd>

### -field <b>FreePortFromInterruptLevel</b>

<dd>
<p>Pointer to the system-supplied <a href="https://msdn.microsoft.com/library/windows/hardware/ff544515">PPARALLEL_FREE_ROUTINE (ISR)</a> callback routine that a kernel-mode driver can use to free the parallel port at IRQL = DIRQL.</p>
</dd>

### -field <b>Context</b>

<dd>
<p>Pointer to the device extension of a functional device object that represents the parallel port.</p>
</dd>
</dl>

## -remarks
<p>A kernel-mode driver can use the parallel interrupt information in the context of an interrupt service routine (ISR). A driver connects an ISR using an <a href="https://msdn.microsoft.com/library/windows/hardware/ff544020">IOCTL_INTERNAL_PARALLEL_CONNECT_INTERRUPT</a> request.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Parallel.h (include Parallel.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544020">IOCTL_INTERNAL_PARALLEL_CONNECT_INTERRUPT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544021">IOCTL_INTERNAL_PARALLEL_DISCONNECT_INTERRUPT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544295">PARALLEL_INTERRUPT_SERVICE_ROUTINE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544515">PPARALLEL_FREE_ROUTINE (ISR)</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/bc69e347-8ef7-4a80-9ef4-bbc03f5586c4">PPARALLEL_TRY_ALLOCATE_ROUTINE (ISR)</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [parports\parports]:%20PARALLEL_INTERRUPT_INFORMATION structure%20 RELEASE:%20(10/23/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>