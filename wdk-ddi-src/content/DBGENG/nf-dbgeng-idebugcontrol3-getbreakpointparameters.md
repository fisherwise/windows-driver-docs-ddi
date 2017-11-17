---
UID: NF.dbgeng.IDebugControl3.GetBreakpointParameters
title: IDebugControl3::GetBreakpointParameters
author: windows-driver-content
description: The GetBreakpointParameters method returns the parameters of one or more breakpoints.
old-location: debugger\getbreakpointparameters.htm
ms.assetid: c4426dfa-7c14-4ef0-8660-855ee24ed7fe
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: debugger
req.header: dbgeng.h
req.include-header: Dbgeng.h, Dbgeng.h, Dbgeng.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IDebugControl.GetBreakpointParameters,IDebugControl2.GetBreakpointParameters,IDebugControl3.GetBreakpointParameters
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
ms.keywords: IDebugControl3, GetBreakpointParameters, IDebugControl3::GetBreakpointParameters
req.iface: IDebugControl3
---

# IDebugControl3::GetBreakpointParameters method



## -description
<p>The <b>GetBreakpointParameters</b> method returns the parameters of one or more <a href="debugger.multiprocessor_syntax#breakpoints#breakpoints">breakpoints</a>.</p>


## -syntax

````
HRESULT GetBreakpointParameters(
  [in]           ULONG                        Count,
  [in, optional] PULONG                       Ids,
  [in]           ULONG                        Start,
  [out]          PDEBUG_BREAKPOINT_PARAMETERS Params
);
````


## -parameters
<dl>

### -param <i>Count</i> [in]

<dd>
<p>Specifies the number of breakpoints whose parameters are being requested.</p>
</dd>

### -param <i>Ids</i> [in, optional]

<dd>
<p>Specifies an array containing the IDs of the breakpoints whose parameters are being requested.  The number of items in this array must be equal to the value specified in <i>Count</i>.  If <i>Ids</i> is <b>NULL</b>, <i>Start</i> is used instead.</p>
</dd>

### -param <i>Start</i> [in]

<dd>
<p>Specifies the beginning index of the breakpoints whose parameters are being requested.  The parameters for breakpoints with indices <i>Start</i> through <i>Start</i> plus <i>Count</i> minus one will be returned.  <i>Start</i> is used only if <i>Ids</i> is <b>NULL</b>.</p>
</dd>

### -param <i>Params</i> [out]

<dd>
<p>Receives the parameters for the specified breakpoints. The size of this array is equal to the value of <i>Count</i>.  For details on the structure returned, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff541459">DEBUG_BREAKPOINT_PARAMETERS</a>.</p>
</dd>
</dl>

## -returns
<p>This method can also return error values.  See <a href="https://msdn.microsoft.com/713f3ee2-2f5b-415e-9908-90f5ae428b43">Return Values</a> for more details.</p><dl>
<dt><b>S_OK</b></dt>
</dl><p>The method was successful.</p><dl>
<dt><b>S_FALSE</b></dt>
</dl><p>The method was successful. However, the parameters for some of the breakpoints were not returned.  The parameters that were not returned have their <b>Id</b> field set to DEBUG_ANY_ID.</p>

<p> </p>

## -remarks
<p>Some of the parameters might not be returned.  This happens if either a breakpoint could not be found or a breakpoint is private (see <a href="https://msdn.microsoft.com/library/windows/hardware/ff546791">GetFlags</a>).</p>

<p>Some of the parameters might not be returned.  This happens if either a breakpoint could not be found or a breakpoint is private (see <a href="https://msdn.microsoft.com/library/windows/hardware/ff546791">GetFlags</a>).</p>

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
<dt>Dbgeng.h (include Dbgeng.h, Dbgeng.h, or Dbgeng.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550508">IDebugControl</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550512">IDebugControl2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550519">IDebugControl3</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548095">GetParameters</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545617">GetBreakpointById</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545639">GetBreakpointByIndex</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [debugger\debugger]:%20IDebugControl::GetBreakpointParameters method%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>