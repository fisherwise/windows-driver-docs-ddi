---
UID: NI.ntdd8042.IOCTL_INTERNAL_I8042_HOOK_KEYBOARD
title: IOCTL_INTERNAL_I8042_HOOK_KEYBOARD
author: windows-driver-content
description: The IOCTL_INTERNAL_I8042_HOOK_KEYBOARD request does the following:Adds an initialization callback routine to the I8042prt keyboard initialization routineAdds an ISR callback routine to the I8042prt keyboard ISRThe initialization and ISR callbacks are optional and are provided by an upper-level filter driver for a PS/2-style keyboard device.After I8042prt receives an IOCTL_INTERNAL_KEYBOARD_CONNECT request, it sends a synchronous IOCTL_INTERNAL_I8042_HOOK_KEYBOARD request to the top of the keyboard device stack.After Kbfiltr receives the hook keyboard request, Kbfiltr filters the request in the following way:Saves the upper-level information passed to Kbfiltr, which includes the context of an upper-level device object, a pointer to an initialization callback, and a pointer to an ISR callbackReplaces the upper-level information with its ownSaves the context of I8042prt and pointers to callbacks that the Kbfiltr ISR callback can useFor more information about this request and the callbacks, see the following topics:I8042prt Callback RoutinesKbfiltr Callback Routines.
old-location: hid\ioctl_internal_i8042_hook_keyboard.htm
ms.assetid: 74580730-1cbb-40fb-a4a3-20523f933171
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: ioctl
ms.prod: windows-hardware
ms.technology: hid
req.header: ntdd8042.h
req.include-header: Ntdd8042.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IOCTL_INTERNAL_I8042_HOOK_KEYBOARD
req.alt-loc: ntdd8042.h
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
ms.keywords: MSFC_VirtualFibrePortAttributes, MSFC_VirtualFibrePortAttributes, *PMSFC_VirtualFibrePortAttributes
req.iface: 
---

# IOCTL_INTERNAL_I8042_HOOK_KEYBOARD IOCTL



## -description
<p>
<p>The IOCTL_INTERNAL_I8042_HOOK_KEYBOARD request does the following:</p>
<ul>
<li>
<p>Adds an initialization callback routine to the I8042prt keyboard initialization routine</p>
</li>
<li>
<p>Adds an ISR callback routine to the I8042prt keyboard ISR</p>
</li>
</ul>
<p>The initialization and ISR callbacks are optional and are provided by an upper-level filter driver for a PS/2-style keyboard device.</p>
<p>After I8042prt receives an <a href="https://msdn.microsoft.com/library/windows/hardware/ff541273">IOCTL_INTERNAL_KEYBOARD_CONNECT</a> request, it sends a synchronous IOCTL_INTERNAL_I8042_HOOK_KEYBOARD request to the top of the keyboard device stack.</p>
<p>After Kbfiltr receives the hook keyboard request, Kbfiltr filters the request in the following way:</p>
<ul>
<li>
<p>Saves the upper-level information passed to Kbfiltr, which includes the context of an upper-level device object, a pointer to an initialization callback, and a pointer to an ISR callback</p>
</li>
<li>
<p>Replaces the upper-level information with its own</p>
</li>
<li>
<p>Saves the context of I8042prt and pointers to callbacks that the Kbfiltr ISR callback can use</p>
</li>
</ul>
<p>For more information about this request and the callbacks, see the following topics:</p>
<dl>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539965">I8042prt Callback Routines</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/a939a2f1-740d-4d6e-a908-cfbefc0808a2">Kbfiltr Callback Routines</a>
</p>
</dd>
</dl>
</p>
<p>The IOCTL_INTERNAL_I8042_HOOK_KEYBOARD request does the following:</p>
<p>Adds an initialization callback routine to the I8042prt keyboard initialization routine</p>
<p>Adds an ISR callback routine to the I8042prt keyboard ISR</p>
<p>The initialization and ISR callbacks are optional and are provided by an upper-level filter driver for a PS/2-style keyboard device.</p>
<p>After I8042prt receives an <a href="https://msdn.microsoft.com/library/windows/hardware/ff541273">IOCTL_INTERNAL_KEYBOARD_CONNECT</a> request, it sends a synchronous IOCTL_INTERNAL_I8042_HOOK_KEYBOARD request to the top of the keyboard device stack.</p>
<p>After Kbfiltr receives the hook keyboard request, Kbfiltr filters the request in the following way:</p>
<p>Saves the upper-level information passed to Kbfiltr, which includes the context of an upper-level device object, a pointer to an initialization callback, and a pointer to an ISR callback</p>
<p>Replaces the upper-level information with its own</p>
<p>Saves the context of I8042prt and pointers to callbacks that the Kbfiltr ISR callback can use</p>
<p>For more information about this request and the callbacks, see the following topics:</p>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539965">I8042prt Callback Routines</a>
</p>
<p>
<a href="https://msdn.microsoft.com/a939a2f1-740d-4d6e-a908-cfbefc0808a2">Kbfiltr Callback Routines</a>
</p>


## -ioctlparameters

### -input-buffer
<p>The <b>Parameters.DeviceIoControl.Type3InputBuffer</b> points to an INTERNAL_I8042_HOOK_KEYBOARD structure. This structure includes the following members:</p>

<p></p>

<p>Pointer to an optional callback that the I8042prt keyboard initialization routine calls when it initializes a keyboard device.</p>

<p>Pointer to an optional callback that is called by the I8042prt keyboard ISR.</p>

### -input-buffer-length
<p>The <b>Parameters.DeviceIoControl.InputBufferLength</b> member is set to a value that is greater than or equal to the size, in bytes, of an <a href="https://msdn.microsoft.com/library/windows/hardware/ff541039">INTERNAL_I8042_HOOK_KEYBOARD</a> structure.</p>

<p>The <b>Parameters.DeviceIoControl.InputBufferLength</b> member is set to a value that is greater than or equal to the size, in bytes, of an <a href="https://msdn.microsoft.com/library/windows/hardware/ff541039">INTERNAL_I8042_HOOK_KEYBOARD</a> structure.</p>

### -output-buffer
<p>None</p>

<p>None</p>

<p>None</p>

### -output-buffer-length
<p>None</p>

<p>None</p>

<p>None</p>

<p>None</p>

### -in-out-buffer

<text></text>

### -inout-buffer-length

<text></text>

### -status-block
I/O Status block
<p>The <b>Status</b> member is set to one of the following values:</p>

<p></p>

<p>The request completed successfully. </p>

<p><b>Parameters.DeviceIoControl.InputBufferLength</b> is less than the size, in bytes, of an INTERNAL_I8042_HOOK_KEYBOARD structure.</p>

<p>The <b>Status</b> member is set to one of the following values:</p>

<p></p>

<p>The request completed successfully. </p>

<p><b>Parameters.DeviceIoControl.InputBufferLength</b> is less than the size, in bytes, of an INTERNAL_I8042_HOOK_KEYBOARD structure.</p>

<p>The <b>Status</b> member is set to one of the following values:</p>

<p></p>

<p>The request completed successfully. </p>

<p><b>Parameters.DeviceIoControl.InputBufferLength</b> is less than the size, in bytes, of an INTERNAL_I8042_HOOK_KEYBOARD structure.</p>

<p>The <b>Status</b> member is set to one of the following values:</p>

<p></p>

<p>The request completed successfully. </p>

<p><b>Parameters.DeviceIoControl.InputBufferLength</b> is less than the size, in bytes, of an INTERNAL_I8042_HOOK_KEYBOARD structure.</p>

<p>The <b>Status</b> member is set to one of the following values:</p>

<p></p>

<p>The request completed successfully. </p>

<p><b>Parameters.DeviceIoControl.InputBufferLength</b> is less than the size, in bytes, of an INTERNAL_I8042_HOOK_KEYBOARD structure.</p>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntdd8042.h (include Ntdd8042.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541039">INTERNAL_I8042_HOOK_KEYBOARD</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541273">IOCTL_INTERNAL_KEYBOARD_CONNECT</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [hid\hid]:%20IOCTL_INTERNAL_I8042_HOOK_KEYBOARD control code%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>