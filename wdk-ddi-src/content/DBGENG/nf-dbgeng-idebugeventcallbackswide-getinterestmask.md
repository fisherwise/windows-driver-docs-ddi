---
UID: NF.dbgeng.IDebugEventCallbacksWide.GetInterestMask
title: IDebugEventCallbacksWide::GetInterestMask
author: windows-driver-content
description: The GetInterestMask callback method is called to determine which events the IDebugEventCallbacksWide object is interested in. The engine calls GetInterestMask when the object is registered with a client by using SetEventCallbacks.
old-location: debugger\idebugeventcallbackswide_getinterestmask.htm
ms.assetid: b1e62ae3-4a3d-42db-b7fe-87d1a7e0b438
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
req.alt-api: IDebugEventCallbacksWide.GetInterestMask
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
ms.keywords: IDebugEventCallbacksWide, GetInterestMask, IDebugEventCallbacksWide::GetInterestMask
req.iface: IDebugEventCallbacksWide
---

# IDebugEventCallbacksWide::GetInterestMask method



## -description
<p>The <b>GetInterestMask</b> callback method is called to determine which <a href="debugger.events#events#events">events</a> the <b>IDebugEventCallbacksWide</b> object is interested in.  The engine calls <b>GetInterestMask</b> when the object is registered with a client by using <a href="https://msdn.microsoft.com/library/windows/hardware/ff556671">SetEventCallbacks</a>.</p>


## -syntax

````
HRESULT GetInterestMask(
  [out] PULONG Mask
);
````


## -parameters
<dl>

### -param <i>Mask</i> [out]

<dd>
<p>Receives a bitmask that indicates which events the object is interested in.  The engine will call only those methods that correspond to the bit flags set by <b>GetInterestMask</b>.  For a description of the bit flags and their corresponding methods, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff541478">DEBUG_EVENT_XXX</a>.</p>
</dd>
</dl>

## -returns
<p>The return value S_OK indicates the method was successful.  All other return values indicate an error occurred,  in which case the <b>SetEventCallbacks</b> call will fail and the callback object will not be used nor will it receive events.</p>

## -remarks
<p>For more information about handling events, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff552239">Monitoring Events</a>.</p>

<p>For more information about handling events, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff552239">Monitoring Events</a>.</p>

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