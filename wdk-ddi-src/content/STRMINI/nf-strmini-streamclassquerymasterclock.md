---
UID: NF.strmini.StreamClassQueryMasterClock
title: StreamClassQueryMasterClock
author: windows-driver-content
description: When the minidriver calls the StreamClassQueryMasterClock routine, the class driver queries the appropriate time value of the master clock asynchronously, and passes the result to the routine passed in the ClockCallbackRoutine parameter.
old-location: stream\streamclassquerymasterclock.htm
ms.assetid: 41b159b6-f365-4ade-b5d4-e7662c75e866
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: stream
req.header: strmini.h
req.include-header: Strmini.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: StreamClassQueryMasterClock
req.alt-loc: Stream.lib,Stream.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Stream.lib
req.dll: 
req.irql: 
ms.keywords: StreamClassQueryMasterClock
req.iface: 
req.product: Windows 10 or later.
---

# StreamClassQueryMasterClock function



## -description
<p>When the minidriver calls the <b>StreamClassQueryMasterClock</b> routine, the class driver queries the appropriate time value of the master clock asynchronously, and passes the result to the routine passed in the <i>ClockCallbackRoutine</i> parameter.</p>


## -syntax

````
VOID StreamClassQueryMasterClock(
  _In_ PHW_STREAM_OBJECT       HwStreamObject,
  _In_ HANDLE                  MasterClockHandle,
  _In_ TIME_FUNCTION           TimeFunction,
  _In_ PHW_QUERY_CLOCK_ROUTINE ClockCallbackRoutine
);
````


## -parameters
<dl>

### -param <i>HwStreamObject</i> [in]

<dd>
<p>Pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff559697">HW_STREAM_OBJECT</a> indicating the stream that is querying its master clock. The stream may only have one query pending at a time. The class driver passes this value to the callback in the <b>HwStreamObject</b> member of the callback's <i>TimeContext</i> parameter.</p>
</dd>

### -param <i>MasterClockHandle</i> [in]

<dd>
<p>Specifies the handle for the master clock that is being queried. The class driver passes this in the SRB_INDICATE_MASTER_CLOCK request to the minidriver's <a href="https://msdn.microsoft.com/library/windows/hardware/ff568467">StrMiniReceiveStreamControlPacket</a> routine.</p>
</dd>

### -param <i>TimeFunction</i> [in]

<dd>
<p>Specifies what time function to query the master clock for. See <a href="https://msdn.microsoft.com/library/windows/hardware/ff559706">HW_TIME_CONTEXT</a> for the possible values. The class driver passes this value to the callback in the <b>Function</b> member of the <i>TimeContext</i> parameter.</p>
</dd>

### -param <i>ClockCallbackRoutine</i> [in]

<dd>
<p>Specifies the routine to which the class driver passes the results. The function prototype must be:</p>
<div class="code"><span codelanguage=""><table>
<tr>
<th></th>
</tr>
<tr>
<td>
<pre>    ClockCallbackRoutine(PHW_TIME_CONTEXT TimeContext);</pre>
</td>
</tr>
</table></span></div>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>The class driver queries the master clock and passes the results in the <i>TimeContext</i> parameter (of type <a href="https://msdn.microsoft.com/library/windows/hardware/ff559706">HW_TIME_CONTEXT</a>) of the callback. In particular, it sets the <b>Time</b> member of this structure to the time value requested in the <i>TimeFunction</i> parameter, the current system time in the <b>SystemTime</b> member of the same structure, and the minidriver's device extension in the <b>HwDeviceExtension</b> member of that structure.</p>

<p>The class driver deallocates the HW_TIME_CONTEXT structure after the clock callback routine terminates, so the callback must store any information the minidriver wishes to maintain. For that purpose, the callback routine may use previously-allocated space in either the minidriver's device extension (<i>TimeContext-</i>&gt;<b>HwDeviceExtension</b>), or the stream extension of the stream that queried its master clock (<i>TimeContext</i>-&gt;<b>HwStreamObject</b>-&gt;<b>HwStreamExtension</b>).</p>

<p>On rare occasions, the graph manager switches the master clock. The class driver exposes a race condition in handling the new master clock. If the minidriver calls a stream class master clock routine immediately after it receives a new clock from the class driver, the class driver may produce unexpected results.</p>

<p>The class driver queries the master clock and passes the results in the <i>TimeContext</i> parameter (of type <a href="https://msdn.microsoft.com/library/windows/hardware/ff559706">HW_TIME_CONTEXT</a>) of the callback. In particular, it sets the <b>Time</b> member of this structure to the time value requested in the <i>TimeFunction</i> parameter, the current system time in the <b>SystemTime</b> member of the same structure, and the minidriver's device extension in the <b>HwDeviceExtension</b> member of that structure.</p>

<p>The class driver deallocates the HW_TIME_CONTEXT structure after the clock callback routine terminates, so the callback must store any information the minidriver wishes to maintain. For that purpose, the callback routine may use previously-allocated space in either the minidriver's device extension (<i>TimeContext-</i>&gt;<b>HwDeviceExtension</b>), or the stream extension of the stream that queried its master clock (<i>TimeContext</i>-&gt;<b>HwStreamObject</b>-&gt;<b>HwStreamExtension</b>).</p>

<p>On rare occasions, the graph manager switches the master clock. The class driver exposes a race condition in handling the new master clock. If the minidriver calls a stream class master clock routine immediately after it receives a new clock from the class driver, the class driver may produce unexpected results.</p>

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
<dt>Strmini.h (include Strmini.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Stream.lib</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff559706">HW_TIME_CONTEXT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff568251">StreamClassQueryMasterClockSync</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff568467">StrMiniReceiveStreamControlPacket</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [stream\stream]:%20StreamClassQueryMasterClock routine%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>