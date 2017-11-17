---
UID: NF.dbgeng.IDebugSystemObjects4.GetSystemIdsByIndex
title: IDebugSystemObjects4::GetSystemIdsByIndex
author: windows-driver-content
description: The GetSystemIdsByIndex method returns the engine target IDs for the specified targets.
old-location: debugger\getsystemidsbyindex.htm
ms.assetid: 7b2dcb75-f674-4a66-a483-8c3f644390c1
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
req.alt-api: IDebugSystemObjects3.GetSystemIdsByIndex,IDebugSystemObjects4.GetSystemIdsByIndex
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
ms.keywords: IDebugSystemObjects4, GetSystemIdsByIndex, IDebugSystemObjects4::GetSystemIdsByIndex
req.iface: IDebugSystemObjects4
---

# IDebugSystemObjects4::GetSystemIdsByIndex method



## -description
<p>The <b>GetSystemIdsByIndex</b> method returns the engine target IDs for the specified targets.</p>


## -syntax

````
HRESULT GetSystemIdsByIndex(
  [in]  ULONG  Start,
  [in]  ULONG  Count,
  [out] PULONG Ids
);
````


## -parameters
<dl>

### -param <i>Start</i> [in]

<dd>
<p>Specifies the index of the first target whose target ID is requested.</p>
</dd>

### -param <i>Count</i> [in]

<dd>
<p>Specifies the number of processes whose IDs are requested.</p>
</dd>

### -param <i>Ids</i> [out]

<dd>
<p>Receives the engine target IDs.  If <i>Ids</i> is <b>NULL</b>, this information is not returned; otherwise, <i>Ids</i> is treated as an array of <i>Count</i> ULONG values.</p>
</dd>
</dl>

## -returns
<p>This method may also return error values.  See <a href="https://msdn.microsoft.com/713f3ee2-2f5b-415e-9908-90f5ae428b43">Return Values</a> for more details.</p><dl>
<dt><b>S_OK</b></dt>
</dl><p>The method was successful.</p>

<p> </p>

## -remarks
<p>The index of the first target is zero.  The index of the last target is the number of targets returned by <a href="https://msdn.microsoft.com/library/windows/hardware/ff547978">GetNumberSystems</a> minus one.</p>

<p>The index of the first target is zero.  The index of the last target is the number of targets returned by <a href="https://msdn.microsoft.com/library/windows/hardware/ff547978">GetNumberSystems</a> minus one.</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550892">IDebugSystemObjects3</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550893">IDebugSystemObjects4</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541386">Debugging Session and Execution Model</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [debugger\debugger]:%20IDebugSystemObjects3::GetSystemIdsByIndex method%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>