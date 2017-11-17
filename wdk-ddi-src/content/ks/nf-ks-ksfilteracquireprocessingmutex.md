---
UID: NF.ks.KsFilterAcquireProcessingMutex
title: KsFilterAcquireProcessingMutex
author: windows-driver-content
description: The KsFilterAcquireProcessingMutex function acquires the processing mutex for a specified AVStream filter.
old-location: stream\ksfilteracquireprocessingmutex.htm
ms.assetid: d4a2fe1a-9a16-45b8-b061-9d1b1398e801
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: stream
req.header: ks.h
req.include-header: Ks.h
req.target-type: Universal
req.target-min-winverclnt: Available in Microsoft Windows XP and later operating systems and DirectX 8.0 and later DirectX versions.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: KsFilterAcquireProcessingMutex
req.alt-loc: Ks.lib,Ks.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ks.lib
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: KsFilterAcquireProcessingMutex
req.iface: 
---

# KsFilterAcquireProcessingMutex function



## -description
<p>The<b> KsFilterAcquireProcessingMutex </b>function acquires the processing mutex for a specified AVStream filter. </p>


## -syntax

````
void KsFilterAcquireProcessingMutex(
  _In_ PKSFILTER Filter
);
````


## -parameters
<dl>

### -param <i>Filter</i> [in]

<dd>
<p>A pointer to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff562522">KSFILTER</a> structure representing the AVStream filter for which to acquire the processing mutex.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>AVStream holds the processing control mutex upon return from this routine. For more information, see <a href="NULL">Mutexes in AVStream</a>.</p>

<p>A minidriver that must suspend processing for a long period of time should not use this mechanism. Instead, it should manipulate the processing control gate directly by using the <b>KSGATE</b><i>Xxx</i> functions. </p>

<p>AVStream holds the processing control mutex upon return from this routine. For more information, see <a href="NULL">Mutexes in AVStream</a>.</p>

<p>A minidriver that must suspend processing for a long period of time should not use this mechanism. Instead, it should manipulate the processing control gate directly by using the <b>KSGATE</b><i>Xxx</i> functions. </p>

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
<p>Available in Microsoft Windows XP and later operating systems and DirectX 8.0 and later DirectX versions.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ks.h (include Ks.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Ks.lib</dt>
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
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562552">KsFilterReleaseProcessingMutex</a>
</dt>
<dt><b>KsFilterReleaseProcessingMutex</b></dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562527">KsFilterAttemptProcessing</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563502">KsPinGetAndGate</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563488">KsPinAcquireProcessingMutex</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563527">KsPinReleaseProcessingMutex</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [stream\stream]:%20KsFilterAcquireProcessingMutex function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>