---
UID: NF.wudfddi.IWDFIoRequest.CompleteWithInformation
title: IWDFIoRequest::CompleteWithInformation
author: windows-driver-content
description: The CompleteWithInformation method completes a request with the supplied information.
old-location: wdf\iwdfiorequest_completewithinformation.htm
ms.assetid: 43089473-3255-4016-8d51-f5ad4261bd8d
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: wdf
req.header: wudfddi.h
req.include-header: Wudfddi.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 1.5
req.alt-api: IWDFIoRequest.CompleteWithInformation
req.alt-loc: WUDFx.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: Unavailable in UMDF 2.0 and later.
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: WUDFx.dll
req.irql: <= DISPATCH_LEVEL
ms.keywords: IWDFIoRequest, CompleteWithInformation, IWDFIoRequest::CompleteWithInformation
req.iface: IWDFIoRequest
req.product: Windows 10 or later.
---

# IWDFIoRequest::CompleteWithInformation method



## -description
<p class="CCE_Message">[<b>Warning:</b> UMDF 2 is the latest version of UMDF and supersedes UMDF 1.  All new UMDF drivers should be written using UMDF 2.  No new features are being added to UMDF 1 and there is limited support for UMDF 1 on newer versions of Windows 10.  Universal Windows drivers must use UMDF 2.  For more info, see <a href="https://docs.microsoft.com/en-us/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2">Getting Started with UMDF</a>.]</p>
<p>The <b>CompleteWithInformation</b> method completes a request with the supplied information.</p>


## -syntax

````
void CompleteWithInformation(
  [in] HRESULT CompletionStatus,
  [in] SIZE_T  Information
);
````


## -parameters
<dl>

### -param <i>CompletionStatus</i> [in]

<dd>
<p>A status value to complete the request with. </p>
</dd>

### -param <i>Information</i> [in]

<dd>
<p>Additional driver-supplied information that is related to the I/O operation.</p>
<p>For read, write, and device I/O control operations, the driver should supply the number of bytes that are transferred.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>For more information about completing an I/O request, see <a href="wdf.completing_i_o_requests">Completing I/O Requests</a>.</p>

<p>For a code example of how to use the <b>CompleteWithInformation</b> method, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff559149">IWDFIoRequest::Send</a>.</p>

<p>For more information about completing an I/O request, see <a href="wdf.completing_i_o_requests">Completing I/O Requests</a>.</p>

<p>For a code example of how to use the <b>CompleteWithInformation</b> method, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff559149">IWDFIoRequest::Send</a>.</p>

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
<p>End of support</p>
</th>
<td width="70%">
<p>Unavailable in UMDF 2.0 and later.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum UMDF version</p>
</th>
<td width="70%">
<p>1.5</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wudfddi.h (include Wudfddi.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>WUDFx.dll</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff558985">IWDFIoRequest</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff559070">IWDFIoRequest::Complete</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff559149">IWDFIoRequest::Send</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20IWDFIoRequest::CompleteWithInformation method%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>