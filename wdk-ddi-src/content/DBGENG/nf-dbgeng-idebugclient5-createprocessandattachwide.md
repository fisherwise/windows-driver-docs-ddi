---
UID: NF.dbgeng.IDebugClient5.CreateProcessAndAttachWide
title: IDebugClient5::CreateProcessAndAttachWide
author: windows-driver-content
description: The CreateProcessAndAttachWide method creates a process from a specified command line, then attach to another user-mode process.
old-location: debugger\createprocessandattachwide.htm
ms.assetid: ceaadcca-e206-402b-8aff-62aca483fb64
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
req.alt-api: IDebugClient3.CreateProcessAndAttachWide,IDebugClient4.CreateProcessAndAttachWide,IDebugClient5.CreateProcessAndAttachWide
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
ms.keywords: IDebugClient5, CreateProcessAndAttachWide, IDebugClient5::CreateProcessAndAttachWide
req.iface: IDebugClient5
---

# IDebugClient5::CreateProcessAndAttachWide method



## -description
<p>The <b>CreateProcessAndAttachWide</b> method creates a process from a specified command line, then attach to another user-mode process.  The created process is suspended and only allowed to execute when the attach has completed.  This allows rough synchronization when debugging both,  client and server processes.</p>


## -syntax

````
HRESULT CreateProcessAndAttachWide(
  [in]           ULONG64 Server,
  [in, optional] PWSTR   CommandLine,
  [in]           ULONG   CreateFlags,
  [in]           ULONG   ProcessId,
  [in]           ULONG   AttachFlags
);
````


## -parameters
<dl>

### -param <i>Server</i> [in]

<dd>
<p>Specifies the process server to use to attach to the process.  If <i>Server</i> is zero, the engine will connect to the local process without using a process server.</p>
</dd>

### -param <i>CommandLine</i> [in, optional]

<dd>
<p>Specifies the command line to execute to create the new process.  If <i>CommandLine</i> is <b>NULL</b>, then no process is created and these methods attach to an existing process, as <a href="https://msdn.microsoft.com/library/windows/hardware/ff538150">AttachProcess</a> does.</p>
</dd>

### -param <i>CreateFlags</i> [in]

<dd>
<p>Specifies the flags to use when creating the process.  For details on these flags, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff541464">DEBUG_CREATE_PROCESS_OPTIONS</a>.<b>CreateFlags</b>.</p>
</dd>

### -param <i>ProcessId</i> [in]

<dd>
<p>Specifies the process ID of the target process the debugger will attach to.  If <i>ProcessId</i> is zero, the debugger will attach to the process it created from <i>CommandLine</i>.</p>
</dd>

### -param <i>AttachFlags</i> [in]

<dd>
<p>Specifies the flags that control how the debugger attaches to the target process.  For details on these flags, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff541454">DEBUG_ATTACH_XXX</a>.</p>
</dd>
</dl>

## -returns
<p>This method may also return error values.  See <a href="https://msdn.microsoft.com/713f3ee2-2f5b-415e-9908-90f5ae428b43">Return Values</a> for more details.</p><dl>
<dt><b>S_OK</b></dt>
</dl><p>The method was successful.</p>

<p> </p>

## -remarks
<p>This method is available only for live user-mode debugging.</p>

<p>If <i>CommandLine</i> is not <b>NULL</b> and <i>ProcessId</i> is not zero, then the engine will create the process in a suspended state.  The engine will resume this newly created process after it successfully connects to the process specified in <i>ProcessId</i>.</p>

<p>The engine does not completely attach to the process until the <a href="https://msdn.microsoft.com/library/windows/hardware/ff561229">WaitForEvent</a> method has been called.  Only after the process has generated an event -- for example, the create-process event -- does it become available in the debugger session.</p>

<p>For more information about creating and attaching to live user-mode targets, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff552020">Live User-Mode Targets</a>.</p>

<p>This method is available only for live user-mode debugging.</p>

<p>If <i>CommandLine</i> is not <b>NULL</b> and <i>ProcessId</i> is not zero, then the engine will create the process in a suspended state.  The engine will resume this newly created process after it successfully connects to the process specified in <i>ProcessId</i>.</p>

<p>The engine does not completely attach to the process until the <a href="https://msdn.microsoft.com/library/windows/hardware/ff561229">WaitForEvent</a> method has been called.  Only after the process has generated an event -- for example, the create-process event -- does it become available in the debugger session.</p>

<p>For more information about creating and attaching to live user-mode targets, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff552020">Live User-Mode Targets</a>.</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550488">IDebugClient3</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550494">IDebugClient4</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550497">IDebugClient5</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff540055">CreateProcessAndAttach2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff538150">AttachProcess</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562135">.attach (Attach to Process)</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562280">.create (Create Process)</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539237">ConnectProcessServer</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539323">CreateProcess2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548265">GetRunningProcessSystemIds</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548243">GetRunningProcessDescription</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541846">DetachCurrentProcess</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff558866">TerminateCurrentProcess</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff537786">AbandonCurrentProcess</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [debugger\debugger]:%20IDebugClient3::CreateProcessAndAttachWide method%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>