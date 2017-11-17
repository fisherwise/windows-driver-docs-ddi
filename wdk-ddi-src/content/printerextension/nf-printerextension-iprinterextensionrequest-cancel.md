---
UID: NF.printerextension.IPrinterExtensionRequest.Cancel
title: IPrinterExtensionRequest::Cancel
author: windows-driver-content
description: Completes the extension event with a cancellation.
old-location: print\iprinterextensionrequest_cancel.htm
ms.assetid: CE5C2999-37D7-4702-B94D-E3131AE34E78
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: print
req.header: printerextension.h
req.include-header: 
req.target-type: Desktop
req.target-min-winverclnt: Windows 8
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IPrinterExtensionRequest.Cancel
req.alt-loc: Printerextension.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: <= APC_LEVEL
ms.keywords: IPrinterExtensionRequest, Cancel, IPrinterExtensionRequest::Cancel
req.iface: IPrinterExtensionRequest
req.product: Windows 10 or later.
---

# IPrinterExtensionRequest::Cancel method



## -description
<p>Completes the extension event with a cancellation.</p>


## -syntax

````
HRESULT Cancel(
  [in] HRESULT hr,
  [in] BSTR    bstrLogMessage
);
````


## -parameters
<dl>

### -param <i>hr</i> [in]

<dd>
<p>The operation result.</p>
</dd>

### -param <i>bstrLogMessage</i> [in]

<dd>
<p>The log message.</p>
</dd>
</dl>

## -returns
<p>This method returns an <b>HRESULT</b> value.</p>

## -remarks


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
<p>Version</p>
</th>
<td width="70%">
<p>Windows 8</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Printerextension.h</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh439517">IPrinterExtensionRequest</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [print\print]:%20IPrinterExtensionRequest::Cancel method%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>