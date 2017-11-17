---
UID: NF.dbgeng.IDebugClient5.AttachKernel
title: IDebugClient5::AttachKernel
author: windows-driver-content
description: The AttachKernel methods connect the debugger engine to a kernel target.
old-location: debugger\attachkernel.htm
ms.assetid: eb861179-3567-4654-a702-40ee3319b27a
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: debugger
req.header: dbgeng.h
req.include-header: Dbgeng.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IDebugClient.AttachKernel,IDebugClient2.AttachKernel,IDebugClient3.AttachKernel,IDebugClient4.AttachKernel,IDebugClient5.AttachKernel
req.alt-loc: dbgeng.h
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
ms.keywords: IDebugClient5, AttachKernel, IDebugClient5::AttachKernel
req.iface: IDebugClient5
---

# IDebugClient5::AttachKernel method



## -description
<p>The <b>AttachKernel</b>  methods connect the <a href="debugger.d#debugger_engine#debugger_engine"><i>debugger engine</i></a> to a kernel target.</p>


## -syntax

````
HRESULT AttachKernel(
  [in]           ULONG Flags,
  [in, optional] PCSTR ConnectOptions
);
````


## -parameters
<dl>

### -param <i>Flags</i> [in]

<dd>
<p>Specifies the flags that control how the debugger attaches to the kernel target.  The possible values are:</p>
<table>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
<tr>
<td>
<p>DEBUG_ATTACH_KERNEL_CONNECTION</p>
</td>
<td>
<p>Attach to the kernel on the target computer.</p>
</td>
</tr>
<tr>
<td>
<p>DEBUG_ATTACH_EXDI_DRIVER</p>
</td>
<td>
<p>Attach to a kernel by using an eXDI driver.</p>
</td>
</tr>
</table>
<p> </p>
</dd>

### -param <i>ConnectOptions</i> [in, optional]

<dd>
<p>Specifies the connection settings for communicating with the computer running the kernel target.  The interpretation of <i>ConnectOptions</i> depends on the value of <i>Flags</i>.</p>
<p></p>
<dl>

### -param <a id="DEBUG_ATTACH_KERNEL_CONNECTION"></a><a id="debug_attach_kernel_connection"></a>DEBUG_ATTACH_KERNEL_CONNECTION

<dd>
<p><i>ConnectOptions</i> will be interpreted the same way as the options that follow the <b>-k</b> switch on the WinDbg and KD command lines.  Environment variables affect <i>ConnectOptions</i> in the same way they affect the <b>-k</b> switch.</p>
</dd>

### -param <a id="DEBUG_ATTACH_EXDI_DRIVER"></a><a id="debug_attach_exdi_driver"></a>DEBUG_ATTACH_EXDI_DRIVER

<dd>
<p>eXDI drivers are not described in this documentation.  If you have an eXDI interface to your hardware probe or hardware simulator, please contact Microsoft for debugging information.</p>
</dd>
</dl>
</dd>
</dl>

## -returns
<p>This method may also return error values.  See <a href="https://msdn.microsoft.com/713f3ee2-2f5b-415e-9908-90f5ae428b43">Return Values</a> for more details.</p><dl>
<dt><b>S_OK</b></dt>
</dl><p>The method was successful.</p>

<p> </p>

## -remarks
<p>For more information about connecting to live kernel-mode targets, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff552005">Live Kernel-Mode Targets</a>.</p>

<p>For more information about connecting to live kernel-mode targets, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff552005">Live Kernel-Mode Targets</a>.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt>Desktop</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Dbgeng.h (include Dbgeng.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549827">IDebugClient</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550481">IDebugClient2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550488">IDebugClient3</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550494">IDebugClient4</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550497">IDebugClient5</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546970">GetKernelConnectionOptions</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff538150">AttachProcess</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551088">IsKernelDebuggerEnabled</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [debugger\debugger]:%20IDebugClient::AttachKernel method%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>