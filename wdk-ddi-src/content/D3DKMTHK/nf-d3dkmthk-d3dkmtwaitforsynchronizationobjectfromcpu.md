---
UID: NF.d3dkmthk.D3DKMTWaitForSynchronizationObjectFromCpu
title: D3DKMTWaitForSynchronizationObjectFromCpu
author: windows-driver-content
description: D3DKMTWaitForSynchronizationObjectFromCpu waits for a monitored fence to reach a certain value.
old-location: display\d3dkmtwaitforsynchronizationobjectfromcpu.htm
ms.assetid: C65880F7-DFCA-4DF9-ABF1-95A82D1D43ED
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmthk.h
req.include-header: D3dkmthk.h
req.target-type: Universal
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3DKMTWaitForSynchronizationObjectFromCpu
req.alt-loc: GDI32.dll,API-MS-Win-DX-D3DKMT-L1-1-1.dll,GDI32.dll,API-MS-Win-DX-D3DKMT-L1-1-2.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: GDI32.lib
req.dll: GDI32.dll
req.irql: 
ms.keywords: D3DKMTWaitForSynchronizationObjectFromCpu
req.iface: 
---

# D3DKMTWaitForSynchronizationObjectFromCpu function



## -description
<p><b>D3DKMTWaitForSynchronizationObjectFromCpu</b> waits for a monitored fence to reach a certain value.</p>


## -syntax

````
EXTERN_C _Check_return_ NTSTATUS APIENTRY D3DKMTWaitForSynchronizationObjectFromCpu(
  _In_ const D3DKMT_WAITFORSYNCHRONIZATIONOBJECTFROMCPU *pData
);
````


## -parameters
<dl>

### -param <i>pData</i> [in]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/dn906810">D3DKMT_WAITFORSYNCHRONIZATIONOBJECTFROMCPU</a> structure that describes the operation.</p>
</dd>
</dl>

## -returns
<p>Returns one of the following values:</p><dl>
<dt><b>STATUS_SUCCESS</b></dt>
</dl><p>The operation was performed successfully.</p><dl>
<dt><b>STATUS_INVALID_PARAMETER </b></dt>
</dl><p>
         Parameters were validated and determined to be incorrect.</p>

<p> </p>

<p>This function might also return other <b>NTSTATUS</b> values.</p>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 10</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>Windows Server 2016</p>
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
<dt>GDI32.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>GDI32.dll</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/dn906810">D3DKMT_WAITFORSYNCHRONIZATIONOBJECTFROMCPU</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3DKMTWaitForSynchronizationObjectFromCpu function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>