---
UID: NF.ks.IKsControl.KsMethod
title: IKsControl::KsMethod
author: windows-driver-content
description: The IKsControl::KsMethod method sends a method to a KS object, together with any other defined support operations available on a method set.
old-location: stream\ikscontrol_ksmethod2.htm
ms.assetid: 75100366-ba79-4ff2-b8e0-64c5c3f5f3b9
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: stream
req.header: ks.h
req.include-header: Ks.h
req.target-type: Desktop
Mobile
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IKsControl.KsMethod
req.alt-loc: ks.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: IKsControl, KsMethod, IKsControl::KsMethod
req.iface: IKsControl
---

# IKsControl::KsMethod method



## -description
<p>The <b>IKsControl::KsMethod</b> method sends a method to a KS object, together with any other defined support operations available on a method set. </p>


## -syntax

````
NTSTATUS KsMethod(
  [in]      PKSMETHOD Method,
  [in]      ULONG     MethodLength,
  [in, out] PVOID     MethodData,
  [in]      ULONG     DataLength,
  [out]     ULONG     *BytesReturned
);
````


## -parameters
<dl>

### -param <i>Method</i> [in]

<dd>
<p>Pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff563398">KSMETHOD</a> structure that describes a method and the request type of the method request. </p>
</dd>

### -param <i>MethodLength</i> [in]

<dd>
<p>Specifies size, in bytes, of the buffer at <i>Method</i>. </p>
</dd>

### -param <i>MethodData</i> [in, out]

<dd>
<p>Pointer to a buffer that contains data and buffer space for a KSMETHOD_TYPE_SEND operation, or buffer space that receives data for all other operations. </p>
</dd>

### -param <i>DataLength</i> [in]

<dd>
<p>Specifies size, in bytes, of the buffer at <i>MethodData</i>. </p>
</dd>

### -param <i>BytesReturned</i> [out]

<dd>
<p>Pointer to a variable that receives the size, in bytes, of the data that <b>KsMethod</b> stores in the buffer at <i>MethodData</i>. </p>
</dd>
</dl>

## -returns
<p>The <b>IKsControl::KsMethod</b> method returns the same value that would be returned if the method had been sent by IOCTL.</p>

## -remarks
<p>To determine the buffer size that is required for a specific method request, you can call this method with MethodData set to <b>NULL</b> and DataLength equal to zero. The method returns HRESULT_FROM_WIN32(ERROR_MORE_DATA and BytesReturned contains the size of the required buffer.</p>

<p>To determine the buffer size that is required for a specific method request, you can call this method with MethodData set to <b>NULL</b> and DataLength equal to zero. The method returns HRESULT_FROM_WIN32(ERROR_MORE_DATA and BytesReturned contains the size of the required buffer.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt>Desktop</dt>
<dt>Mobile</dt>
</dl>
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
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563398">KSMETHOD</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563420">KSMETHOD_ITEM</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563423">KSMETHOD_SET</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [stream\stream]:%20IKsControl::KsMethod method%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>