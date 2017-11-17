---
UID: NF.wdm.InterlockedCompareExchange~r1
title: InterlockedCompareExchange
author: windows-driver-content
description: The InterlockedCompareExchange routine performs an atomic operation that compares the input value pointed to by Destination with the value of Comparand.
old-location: kernel\interlockedcompareexchange.htm
ms.assetid: 925a5481-d626-4824-8cbe-4fc2a0a6ad92
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: Available starting with Windows 2000.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: InterlockedCompareExchange
req.alt-loc: OneCoreUAP.lib,OneCoreUAP.dll,API-MS-Win-Core-Interlocked-l1-1-0.dll,API-MS-Win-Core-Interlocked-l1-2-0.dll,KernelBase.dll,MinKernelBase.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: OneCoreUAP.lib on Windows 10
req.dll: 
req.irql: Any level
ms.keywords: InterlockedCompareExchange
req.iface: 
req.product: Windows 10 or later.
---

# InterlockedCompareExchange function



## -description
<p>The <b>InterlockedCompareExchange</b> routine performs an atomic operation that compares the input value pointed to by <i>Destination</i> with the value of <i>Comparand</i>. </p>


## -syntax

````
LONG InterlockedCompareExchange(
  _Inout_ LONG volatile *Destination ,
  _In_    LONG          Exchange ,
  _In_    LONG          Comparand
);
````


## -parameters
<dl>

### -param <i>Destination </i> [in, out]

<dd>
<p>A pointer to the input value that is compared with the value of <i>Comparand</i>.</p>
</dd>

### -param <i>Exchange </i> [in]

<dd>
<p>Specifies the output value pointed to by <i>Destination</i> if the input value pointed to by <i>Destination</i> equals the value of <i>Comparand</i>. </p>
</dd>

### -param <i>Comparand</i> [in]

<dd>
<p>Specifies the value that is compared with the input value pointed to by <i>Destination</i>.</p>
</dd>
</dl>

## -returns
<p><b>InterlockedCompareExchange</b> returns the original value of *<i>Destination</i>. </p>

## -remarks
<p>If <i>Comparand</i> is equal to *<i>Destination</i>, then *<i>Destination</i> is set to equal <i>Exchange</i>. Otherwise, *<i>Destination</i> is unchanged.</p>

<p><b>InterlockedCompareExchange</b> provides a fast, atomic way to synchronize the testing and updating of a variable that is shared by multiple threads. If the input value pointed to by <i>Destination</i> equals the value of <i>Comparand</i>, the output value of <i>Destination</i> is set to the value of <i>Exchange</i>. </p>

<p><b>InterlockedCompareExchange</b> is designed for speed and, typically, is implemented inline by a compiler. <b>InterlockedCompareExchange </b>is atomic only with respect to other <b>Interlocked<i>Xxx</i></b> calls. It does not use a spin lock and can be safely used on pageable data. </p>

<p>Interlocked operations cannot be used on non-cached memory. </p>

<p>If <i>Comparand</i> is equal to *<i>Destination</i>, then *<i>Destination</i> is set to equal <i>Exchange</i>. Otherwise, *<i>Destination</i> is unchanged.</p>

<p><b>InterlockedCompareExchange</b> provides a fast, atomic way to synchronize the testing and updating of a variable that is shared by multiple threads. If the input value pointed to by <i>Destination</i> equals the value of <i>Comparand</i>, the output value of <i>Destination</i> is set to the value of <i>Exchange</i>. </p>

<p><b>InterlockedCompareExchange</b> is designed for speed and, typically, is implemented inline by a compiler. <b>InterlockedCompareExchange </b>is atomic only with respect to other <b>Interlocked<i>Xxx</i></b> calls. It does not use a spin lock and can be safely used on pageable data. </p>

<p>Interlocked operations cannot be used on non-cached memory. </p>

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
<p>Available starting with Windows 2000.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdm.h (include Wdm.h, Ntddk.h, or Ntifs.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>OneCoreUAP.lib on Windows 10</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>Any level</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545352">ExInterlockedCompareExchange64</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547863">InterlockedCompareExchangePointer</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547871">InterlockedDecrement</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547892">InterlockedExchange</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547904">InterlockedExchangePointer</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547910">InterlockedIncrement</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20InterlockedCompareExchange routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>