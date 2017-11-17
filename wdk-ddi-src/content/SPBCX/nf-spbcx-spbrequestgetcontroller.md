---
UID: NF.spbcx.SpbRequestGetController
title: SpbRequestGetController
author: windows-driver-content
description: The SpbRequestGetController method returns the WDFDEVICE handle to the device object for the SPB controller that the specified I/O request was sent to.
old-location: spb\spbrequestgetcontroller.htm
ms.assetid: 0CD692E2-B2D6-4786-8C0B-C0DCAFCF6259
ms.author: windowsdriverdev
ms.date: 10/23/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: SPB
req.header: spbcx.h
req.include-header: 
req.target-type: Universal
req.target-min-winverclnt: Available starting with Windows 8.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: SpbRequestGetController
req.alt-loc: Spbcx.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: <= DISPATCH_LEVEL
ms.keywords: SpbRequestGetController
req.iface: 
req.product: Windows 10 or later.
---

# SpbRequestGetController function



## -description
<p>The <b>SpbRequestGetController</b> method returns the WDFDEVICE handle to the device object for the SPB controller that the specified I/O request was sent to.</p>


## -syntax

````
WDFDEVICE SpbRequestGetController(
  [in] SPBREQUEST SpbRequest
);
````


## -parameters
<dl>

### -param <i>SpbRequest</i> [in]

<dd>
<p>The <a href="buses.spbrequest_object_handle">SPBREQUEST</a> handle to the I/O request from which to retrieve the WDFDEVICE handle. The SPB controller driver previously received this handle through one of its registered <a href="https://msdn.microsoft.com/1DA1FF41-FB01-45CC-B0C1-EAF2C81D0CDA">event callback functions</a>.</p>
</dd>
</dl>

## -returns
<p><b>SpbRequestGetController</b> returns the WDFDEVICE handle that the I/O request was sent to.</p>

## -remarks


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
<p>Available starting with Windows 8.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Spbcx.h</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&lt;= DISPATCH_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="buses.spbrequest_object_handle">SPBREQUEST</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [SPB\buses]:%20SpbRequestGetController method%20 RELEASE:%20(10/23/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>