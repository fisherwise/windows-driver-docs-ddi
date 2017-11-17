---
UID: NF.d3dkmthk.D3DKMTOpenKeyedMutex2
title: D3DKMTOpenKeyedMutex2
author: windows-driver-content
description: Opens a keyed mutex object that includes private data.
old-location: display\d3dkmtopenkeyedmutex2.htm
ms.assetid: 33140445-e312-4495-990a-033a87598fa1
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
req.alt-api: D3DKMTOpenKeyedMutex2
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
ms.keywords: D3DKMTOpenKeyedMutex2
req.iface: 
---

# D3DKMTOpenKeyedMutex2 function



## -description
<p>Opens a keyed mutex object that includes private data.</p>


## -syntax

````
EXTERN_C _Check_return_ NTSTATUS APIENTRY D3DKMTOpenKeyedMutex2(
  _Inout_ D3DKMT_OPENKEYEDMUTEX2 *pData
);
````


## -parameters
<dl>

### -param <i>pData</i> [in, out]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/hh406490">D3DKMT_OPENKEYEDMUTEX2</a> structure that describes a keyed mutex object that includes private data.</p>
</dd>
</dl>

## -returns
<p>Returns one of the following values:</p><dl>
<dt><b>STATUS_SUCCESS</b></dt>
</dl><p>The keyed mutex object was successfully opened. </p><dl>
<dt><b>STATUS_DEVICE_REMOVED</b></dt>
</dl><p>The graphics adapter was stopped or the display device was reset.</p><dl>
<dt><b>STATUS_INVALID_PARAMETER</b></dt>
</dl><p>Parameters were validated and determined to be incorrect.</p><dl>
<dt><b>STATUS_NO_MEMORY</b></dt>
</dl><p>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh439405">D3DKMTOpenKeyedMutex2</a> could not complete because of insufficient memory.</p>

<p> </p>

<p>This function might also return other NTSTATUS values.</p>

## -remarks
<p><b>D3DKMTOpenKeyedMutex2</b> behaves like the <a href="https://msdn.microsoft.com/library/windows/hardware/ff547054">D3DKMTOpenKeyedMutex</a> function but lets the caller specify private data to associate with the keyed mutex.</p>

<p><b>D3DKMTOpenKeyedMutex2</b> behaves like the <a href="https://msdn.microsoft.com/library/windows/hardware/ff547054">D3DKMTOpenKeyedMutex</a> function but lets the caller specify private data to associate with the keyed mutex.</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/hh406490">D3DKMT_OPENKEYEDMUTEX2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547054">D3DKMTOpenKeyedMutex</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3DKMTOpenKeyedMutex2 function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>