---
UID: NF.iointex.WdmlibIoConnectInterruptEx
title: WdmlibIoConnectInterruptEx
author: windows-driver-content
description: The WdmlibIoConnectInterruptEx function registers an interrupt-handling routine for a device's interrupts.
old-location: kernel\wdmlibioconnectinterruptex.htm
ms.assetid: 172598B1-C486-489F-98F0-382EB8139A08
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: iointex.h
req.include-header: Iointex.h, Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: Available on Windows Vista and later versions of the Windows operating system. Drivers that must also work on Windows 2000, Windows XP, or Windows Server 2003 can instead link to Iointex.lib to use the routine.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: WdmlibIoConnectInterruptEx,IoConnectInterruptEx
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: HwStorPortProhibitedDDIs
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: PASSIVE_LEVEL
ms.keywords: WdmlibIoConnectInterruptEx
req.iface: 
---

# WdmlibIoConnectInterruptEx function



## -description
<p>The <b>WdmlibIoConnectInterruptEx</b> function registers an interrupt-handling routine for a device's interrupts.</p>


## -syntax

````
NTSTATUS WdmlibIoConnectInterruptEx(
  _Inout_ PIO_CONNECT_INTERRUPT_PARAMETERS Parameters
);
````


## -parameters
<dl>

### -param <i>Parameters</i> [in, out]

<dd>
<p>Pointer to an <a href="https://msdn.microsoft.com/library/windows/hardware/ff550541">IO_CONNECT_INTERRUPT_PARAMETERS</a> structure that specifies the device and interrupt-handling routine. On return,  <b>WdmlibIoConnectInterruptEx</b> updates this structure to hold information about the device's interrupts.</p>
</dd>
</dl>

## -returns
<p>The function returns STATUS_SUCCESS on success, or the appropriate NTSTATUS error value on failure. Possible error values include:</p><dl>
<dt><b>STATUS_INVALID_DEVICE_REQUEST</b></dt>
</dl><p>The operation is invalid for the specified device. For example, <i>Parameters</i>-&gt;<b>Version</b> = CONNECT_LINE_BASED, and the system has assigned multiple interrupt messages to the device.</p>

## -remarks
<p><b>WdmlibIoConnectInterruptEx</b>
           can be used to register an interrupt-handling routine for both traditional line-based interrupts (such as that supported by the PCI bus), and the newer message-signaled interrupts (such as that supported by PCI versions 2.2 and 3.0). </p>

<p>Drivers register an <a href="https://msdn.microsoft.com/library/windows/hardware/ff547958">InterruptService</a> routine for line-based interrupts, and an <a href="https://msdn.microsoft.com/library/windows/hardware/ff547940">InterruptMessageService</a> routine for message-signaled interrupts. For more information about how to specify the members of <i>Parameters</i> in each case, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff550541">IO_CONNECT_INTERRUPT_PARAMETERS</a>.</p>

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
<p>Available on Windows Vista and later versions of the Windows operating system. Drivers that must also work on Windows 2000, Windows XP, or Windows Server 2003 can instead link to Iointex.lib to use the routine.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Iointex.h (include Iointex.h, Wdm.h, Ntddk.h, or Ntifs.h)</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/hh454220">HwStorPortProhibitedDDIs</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547958">InterruptService</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547940">InterruptMessageService</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550541">IO_CONNECT_INTERRUPT_PARAMETERS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/B6F8663C-3A13-45DA-80FE-CC8B9194D083">WdmlibIoDisconnectInterruptEx</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20WdmlibIoConnectInterruptEx function%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>