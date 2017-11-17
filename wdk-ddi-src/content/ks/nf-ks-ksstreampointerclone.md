---
UID: NF.ks.KsStreamPointerClone
title: KsStreamPointerClone
author: windows-driver-content
description: The KsStreamPointerClone function creates a clone of a given stream pointer.
old-location: stream\ksstreampointerclone.htm
ms.assetid: b51e1c17-e6b5-4108-bfbc-29f1ee06d9f4
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
req.alt-api: KsStreamPointerClone
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
req.irql: <=DISPATCH_LEVEL
ms.keywords: KsStreamPointerClone
req.iface: 
---

# KsStreamPointerClone function



## -description
<p>The<b> KsStreamPointerClone </b>function creates a clone of a given stream pointer.</p>


## -syntax

````
NTSTATUS KsStreamPointerClone(
  _In_     PKSSTREAM_POINTER  StreamPointer,
  _In_opt_ PFNKSSTREAMPOINTER CancelCallback,
  _In_     ULONG              ContextSize,
  _Out_    PKSSTREAM_POINTER  *CloneStreamPointer
);
````


## -parameters
<dl>

### -param <i>StreamPointer</i> [in]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff567139">KSSTREAM_POINTER</a> structure representing the stream pointer that is to be cloned.</p>
</dd>

### -param <i>CancelCallback</i> [in, optional]

<dd>
<p>Optional. A pointer to a minidriver-supplied <a href="https://msdn.microsoft.com/library/windows/hardware/ff554271">AVStrMiniCancelCallback</a> routine. AVStream calls this routine if the IRP associated with <i>CloneStreamPointer</i> is canceled.</p>
</dd>

### -param <i>ContextSize</i> [in]

<dd>
<p>This parameter indicates how many bytes of minidriver context information the resulting clone stream pointer should have. If nonzero, the requested number of bytes are allocated immediately after the returned stream pointer, and the <i>Context</i> field of <i>CloneStreamPointer</i> points to the allocated memory.</p>
</dd>

### -param <i>CloneStreamPointer</i> [out]

<dd>
<p>A pointer to a pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff567139">KSSTREAM_POINTER</a> structure. Upon successful completion of the cloning operation, <i>CloneStreamPointer</i> contains a pointer to the address of the cloned stream pointer.</p>
</dd>
</dl>

## -returns
<p><b>KsStreamPointerClone </b>returns either STATUS_SUCCESS, indicating that the cloning operation completed normally, or an appropriate error code.</p>

## -remarks
<p>The resulting clone initially refers to the same data frame as the original stream pointer and is in the same state (locked or unlocked). Adding a clone stream pointer referencing a data frame increments the reference count on that particular frame. Note that the frame in question, and therefore the IRP to which the frame belongs, is not completed until the reference count drops to zero.</p>

<p>You can use the <i>ContextSize</i> parameter of this call to minimize allocation calls.</p>

<p>Also see <a href="NULL">Stream Pointers</a>.</p>

<p>The resulting clone initially refers to the same data frame as the original stream pointer and is in the same state (locked or unlocked). Adding a clone stream pointer referencing a data frame increments the reference count on that particular frame. Note that the frame in question, and therefore the IRP to which the frame belongs, is not completed until the reference count drops to zero.</p>

<p>You can use the <i>ContextSize</i> parameter of this call to minimize allocation calls.</p>

<p>Also see <a href="NULL">Stream Pointers</a>.</p>

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
<p>&lt;=DISPATCH_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567130">KsStreamPointerDelete</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/dn892390">KsStreamPointerLock</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567137">KsStreamPointerUnlock</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567125">KsStreamPointerAdvance</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567126">KsStreamPointerAdvanceOffsets</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567127">KsStreamPointerAdvanceOffsetsAndUnlock</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [stream\stream]:%20KsStreamPointerClone function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>