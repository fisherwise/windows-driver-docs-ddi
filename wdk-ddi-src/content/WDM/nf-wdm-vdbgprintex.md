---
UID: NF.wdm.vDbgPrintEx
title: vDbgPrintEx
author: windows-driver-content
description: The vDbgPrintEx routine sends a string to the kernel debugger if certain conditions are met.
old-location: devtest\vdbgprintex.htm
ms.assetid: e7118f5b-819f-428f-a5e6-80a36705d626
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: devtest
req.header: wdm.h
req.include-header: Dpfilter.h, Wdm.h, Ntddk.h, Ndis.h
req.target-type: Universal
req.target-min-winverclnt: Available in Microsoft Windows XP and later operating system versions.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: vDbgPrintEx
req.alt-loc: NtDll.dll,NtosKrnl.exe
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtDll.lib (user mode); 
NtosKrnl.lib (kernel mode)
req.dll: NtDll.dll (user mode); 
NtosKrnl.exe (kernel mode)
req.irql: <= DIRQL (see Comments section)
ms.keywords: vDbgPrintEx
req.iface: 
req.product: Windows 10 or later.
---

# vDbgPrintEx function



## -description
<p>The <b>vDbgPrintEx</b> routine sends a string to the kernel debugger if certain conditions are met.</p>


## -syntax

````
ULONG vDbgPrintEx(
  _In_ ULONG   ComponentId,
  _In_ ULONG   Level,
  _In_ PCCH    Format,
  _In_ va_list arglist
);
````


## -parameters
<dl>

### -param <i>ComponentId</i> [in]

<dd>
<p>The component that is calling this routine. This parameter must be one of the component name filter IDs that are defined in Dpfilter.h. To avoid mixing your driver's output with the output of Windows components, you should use only the following values for <i>ComponentId</i>:</p>
<ul>
<li>
<p>DPFLTR_IHVVIDEO_ID </p>
</li>
<li>
<p>DPFLTR_IHVAUDIO_ID </p>
</li>
<li>
<p>DPFLTR_IHVNETWORK_ID </p>
</li>
<li>
<p>DPFLTR_IHVSTREAMING_ID </p>
</li>
<li>
<p>DPFLTR_IHVBUS_ID </p>
</li>
<li>
<p>DPFLTR_IHVDRIVER_ID </p>
</li>
</ul>
</dd>

### -param <i>Level</i> [in]

<dd>
<p>The severity of the message that is being sent. This parameter can be any 32-bit integer. Values between 0 and 31 (inclusive) are treated differently than values between 32 and 0xFFFFFFFF. For more information about how the values are treated, see <a href="NULL">Reading and Filtering Debugging Messages</a>.</p>
</dd>

### -param <i>Format</i> [in]

<dd>
<p>A pointer to the format string to print. The <i>Format</i> string supports most of the <b>printf</b>-style formatting codes. However, you can use the Unicode format codes (<b>%C</b>, <b>%S</b>, <b>%lc</b>, <b>%ls</b>, <b>%wc</b>, <b>%ws</b>, and <b>%wZ</b>) only with IRQL = PASSIVE_LEVEL. The <b>vDbgPrintEx</b> routine does not support any of the floating point types (<b>%f</b>, <b>%e</b>, <b>%E</b>, <b>%g</b>, <b>%G</b>, <b>%a</b>, or <b>%A</b>).</p>
</dd>

### -param <i>arglist</i> [in]

<dd>
<p>An argument list for the format string. The <b>vDbgPrintEx</b> routine uses this list in the same way that <b>vprintf</b> does.</p>
</dd>
</dl>

## -returns
<p><b>vDbgPrintEx</b> returns STATUS_SUCCESS if the operation succeeds. Otherwise, this routine returns the appropriate error code.</p>

## -remarks
<p>Only kernel-mode drivers can call the <b>vDbgPrintEx</b> routine.</p>

<p><b>vDbgPrintEx</b> can be called at IRQL &lt;= DIRQL. However, you can use Unicode format codes (%<b>wc</b> and %<b>ws</b>) only at IRQL = PASSIVE_LEVEL. Also, because the debugger uses interprocess interrupts (IPIs) to communicate with other processors, calling <b>vDbgPrintEx</b> at IRQL &gt; DIRQL can cause deadlocks.</p>

<p><b>vDbgPrintEx</b> either passes the string that it creates to the kernel debugger or does nothing at all, depending on the values of <i>ComponentId</i>, <i>Level</i>, and the corresponding component filter masks. For more information about what <b>vDbgPrintEx</b> does, see <a href="NULL">Reading and Filtering Debugging Messages</a>.</p>

<p>Unless it is absolutely necessary, you should not obtain a string from user input or another process and pass it to <b>vDbgPrintEx</b>. If you do use a string that you did not create, you must verify that this string is a valid format string and that the format codes match the argument list in type and quantity. The best coding practice is for all <i>Format</i> strings to be static and defined at compile time.</p>

<p>There is no upper limit to the size of the <i>Format</i> string or the number of arguments in the <i>arglist</i> list. However, any single call to <b>vDbgPrintEx</b> will transmit only 512 bytes of information. </p>

<p>There is also a limit to the size of the buffer that the debugger uses. For more information about this limit, see <a href="devtest.reading_and_filtering_debugging_messages#ddk_the_dbgprint_buffer_and_the_debugger_tools#ddk_the_dbgprint_buffer_and_the_debugger_tools">The DbgPrint Buffer and the Debugger</a>.</p>

<p>This routine is defined in Wdm.h. Component filter IDs are defined in Dpfilter.h.</p>

<p>Only kernel-mode drivers can call the <b>vDbgPrintEx</b> routine.</p>

<p><b>vDbgPrintEx</b> can be called at IRQL &lt;= DIRQL. However, you can use Unicode format codes (%<b>wc</b> and %<b>ws</b>) only at IRQL = PASSIVE_LEVEL. Also, because the debugger uses interprocess interrupts (IPIs) to communicate with other processors, calling <b>vDbgPrintEx</b> at IRQL &gt; DIRQL can cause deadlocks.</p>

<p><b>vDbgPrintEx</b> either passes the string that it creates to the kernel debugger or does nothing at all, depending on the values of <i>ComponentId</i>, <i>Level</i>, and the corresponding component filter masks. For more information about what <b>vDbgPrintEx</b> does, see <a href="NULL">Reading and Filtering Debugging Messages</a>.</p>

<p>Unless it is absolutely necessary, you should not obtain a string from user input or another process and pass it to <b>vDbgPrintEx</b>. If you do use a string that you did not create, you must verify that this string is a valid format string and that the format codes match the argument list in type and quantity. The best coding practice is for all <i>Format</i> strings to be static and defined at compile time.</p>

<p>There is no upper limit to the size of the <i>Format</i> string or the number of arguments in the <i>arglist</i> list. However, any single call to <b>vDbgPrintEx</b> will transmit only 512 bytes of information. </p>

<p>There is also a limit to the size of the buffer that the debugger uses. For more information about this limit, see <a href="devtest.reading_and_filtering_debugging_messages#ddk_the_dbgprint_buffer_and_the_debugger_tools#ddk_the_dbgprint_buffer_and_the_debugger_tools">The DbgPrint Buffer and the Debugger</a>.</p>

<p>This routine is defined in Wdm.h. Component filter IDs are defined in Dpfilter.h.</p>

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
<p>Available in Microsoft Windows XP and later operating system versions.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdm.h (include Dpfilter.h, Wdm.h, Ntddk.h, or Ndis.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>NtDll.lib (user mode); </dt>
<dt>NtosKrnl.lib (kernel mode)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>NtDll.dll (user mode); </dt>
<dt>NtosKrnl.exe (kernel mode)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&lt;= DIRQL (see Comments section)</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543634">DbgPrintEx</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [devtest\devtest]:%20vDbgPrintEx routine%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>