---
UID: NF.d3dkmthk.D3DKMTAcquireKeyedMutex2
title: D3DKMTAcquireKeyedMutex2
author: windows-driver-content
description: Acquires a keyed mutex object that includes private data.
old-location: display\d3dkmtacquirekeyedmutex2.htm
ms.assetid: 94ebfeb6-2035-4dd6-bbc9-ba82939b51ec
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmthk.h
req.include-header: D3dkmthk.h
req.target-type: Universal
req.target-min-winverclnt: Windows 8
req.target-min-winversvr: Windows Server 2012
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3DKMTAcquireKeyedMutex2
req.alt-loc: Gdi32.dll,API-MS-Win-dx-d3dkmt-l1-1-0.dll,API-MS-Win-dx-d3dkmt-l1-1-1.dll,API-MS-Win-DX-D3DKMT-L1-1-2.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Gdi32.lib
req.dll: Gdi32.dll
req.irql: 
ms.keywords: D3DKMTAcquireKeyedMutex2
req.iface: 
---

# D3DKMTAcquireKeyedMutex2 function



## -description
<p>Acquires a keyed mutex object that includes private data.</p>


## -syntax

````
EXTERN_C _Check_return_ NTSTATUS APIENTRY D3DKMTAcquireKeyedMutex2(
  _Inout_ D3DKMT_ACQUIREKEYEDMUTEX2 *pData
);
````


## -parameters
<dl>

### -param <i>pData</i> [in, out]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/hh439466">D3DKMT_ACQUIREKEYEDMUTEX2</a> structure that specifies the keyed mutex object to acquire. </p>
</dd>
</dl>

## -returns
<p>Returns one of the following values:</p><dl>
<dt><b>STATUS_SUCCESS</b></dt>
</dl><p>The keyed mutex object was successfully acquired. </p><dl>
<dt><b>STATUS_DEVICE_REMOVED</b></dt>
</dl><p>The graphics adapter was stopped or the display device was reset.</p><dl>
<dt><b>STATUS_INVALID_PARAMETER</b></dt>
</dl><p>Parameters were validated and determined to be incorrect.</p><dl>
<dt><b>STATUS_NO_MEMORY</b></dt>
</dl><p>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh439340">D3DKMTAcquireKeyedMutex2</a> could not complete because of insufficient memory.</p>

<p> </p>

<p>This function might also return other <b>NTSTATUS</b> values.</p>

## -remarks
<p><b>D3DKMTAcquireKeyedMutex2</b> behaves like the <a href="https://msdn.microsoft.com/library/windows/hardware/ff546732">D3DKMTAcquireKeyedMutex</a> function but lets the caller specify private data to associate with the keyed mutex.</p>

<p><b>D3DKMTAcquireKeyedMutex2</b> behaves like the <a href="https://msdn.microsoft.com/library/windows/hardware/ff546732">D3DKMTAcquireKeyedMutex</a> function but lets the caller specify private data to associate with the keyed mutex.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 8</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>Windows Server 2012</p>
</td>
</tr>
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
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>D3dkmthk.h (include D3dkmthk.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Gdi32.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>Gdi32.dll</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh439466">D3DKMT_ACQUIREKEYEDMUTEX2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546732">D3DKMTAcquireKeyedMutex</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3DKMTAcquireKeyedMutex2 function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>