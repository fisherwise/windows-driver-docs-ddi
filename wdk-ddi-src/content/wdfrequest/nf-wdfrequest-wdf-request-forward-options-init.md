---
UID: NF.wdfrequest.WDF_REQUEST_FORWARD_OPTIONS_INIT
title: WDF_REQUEST_FORWARD_OPTIONS_INIT
author: windows-driver-content
description: The WDF_REQUEST_FORWARD_OPTIONS_INIT function initializes a WDF_REQUEST_FORWARD_OPTIONS structure.
old-location: wdf\wdf_request_forward_options_init.htm
ms.assetid: 301b4b63-0337-4f78-a4f8-6b2d2b168663
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: wdf
req.header: wdfrequest.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.9
req.umdf-ver: 
req.alt-api: WDF_REQUEST_FORWARD_OPTIONS_INIT
req.alt-loc: wdfrequest.h
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
ms.keywords: WDF_REQUEST_FORWARD_OPTIONS_INIT
req.iface: 
req.product: Windows 10 or later.
---

# WDF_REQUEST_FORWARD_OPTIONS_INIT function



## -description
<p class="CCE_Message">[Applies to KMDF only]</p>
<p>The <b>WDF_REQUEST_FORWARD_OPTIONS_INIT</b> function initializes a <a href="https://msdn.microsoft.com/library/windows/hardware/ff552459">WDF_REQUEST_FORWARD_OPTIONS</a> structure.</p>


## -syntax

````
VOID WDF_REQUEST_FORWARD_OPTIONS_INIT(
  _Out_ PWDF_REQUEST_FORWARD_OPTIONS ForwardOptions
);
````


## -parameters
<dl>

### -param <i>ForwardOptions</i> [out]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff552459">WDF_REQUEST_FORWARD_OPTIONS</a> structure.</p>
</dd>
</dl>

## -returns
<p>None.</p>

## -remarks
<p>Before a driver calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff549959">WdfRequestForwardToParentDeviceIoQueue</a>, it must call <b>WDF_REQUEST_FORWARD_OPTIONS_INIT</b> to initialize a <a href="https://msdn.microsoft.com/library/windows/hardware/ff552459">WDF_REQUEST_FORWARD_OPTIONS</a> structure.</p>

<p>The <b>WDF_REQUEST_FORWARD_OPTIONS_INIT</b> function zeros the specified <a href="https://msdn.microsoft.com/library/windows/hardware/ff552459">WDF_REQUEST_FORWARD_OPTIONS</a> structure and sets the structure's <b>Size</b> member. Then the function sets the <a href="https://msdn.microsoft.com/6161bfd3-482c-4571-bd88-2e25d32b34a0">WDF_REQUEST_FORWARD_OPTION_SEND_AND_FORGET</a> flag.</p>

<p>For a code example that uses <b>WDF_REQUEST_FORWARD_OPTIONS_INIT</b>, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff549959">WdfRequestForwardToParentDeviceIoQueue</a>.</p>

<p>Before a driver calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff549959">WdfRequestForwardToParentDeviceIoQueue</a>, it must call <b>WDF_REQUEST_FORWARD_OPTIONS_INIT</b> to initialize a <a href="https://msdn.microsoft.com/library/windows/hardware/ff552459">WDF_REQUEST_FORWARD_OPTIONS</a> structure.</p>

<p>The <b>WDF_REQUEST_FORWARD_OPTIONS_INIT</b> function zeros the specified <a href="https://msdn.microsoft.com/library/windows/hardware/ff552459">WDF_REQUEST_FORWARD_OPTIONS</a> structure and sets the structure's <b>Size</b> member. Then the function sets the <a href="https://msdn.microsoft.com/6161bfd3-482c-4571-bd88-2e25d32b34a0">WDF_REQUEST_FORWARD_OPTION_SEND_AND_FORGET</a> flag.</p>

<p>For a code example that uses <b>WDF_REQUEST_FORWARD_OPTIONS_INIT</b>, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff549959">WdfRequestForwardToParentDeviceIoQueue</a>.</p>

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
<p>Minimum KMDF version</p>
</th>
<td width="70%">
<p>1.9</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdfrequest.h (include Wdf.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552459">WDF_REQUEST_FORWARD_OPTIONS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549959">WdfRequestForwardToParentDeviceIoQueue</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WDF_REQUEST_FORWARD_OPTIONS_INIT function%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>