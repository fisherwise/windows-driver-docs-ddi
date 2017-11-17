---
UID: NF.wudfddi.IWDFDeviceInitialize.RetrieveDeviceInstanceId
title: IWDFDeviceInitialize::RetrieveDeviceInstanceId
author: windows-driver-content
description: The RetrieveDeviceInstanceId method retrieves the identifier of an instance of a device.
old-location: wdf\iwdfdeviceinitialize_retrievedeviceinstanceid.htm
ms.assetid: 5f1651f9-4952-4e87-90fc-3f79948b8457
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
req.alt-api: IWDFDeviceInitialize.RetrieveDeviceInstanceId
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
ms.keywords: IWDFDeviceInitialize, RetrieveDeviceInstanceId, IWDFDeviceInitialize::RetrieveDeviceInstanceId
req.iface: IWDFDeviceInitialize
req.product: Windows 10 or later.
---

# IWDFDeviceInitialize::RetrieveDeviceInstanceId method



## -description
<p class="CCE_Message">[<b>Warning:</b> UMDF 2 is the latest version of UMDF and supersedes UMDF 1.  All new UMDF drivers should be written using UMDF 2.  No new features are being added to UMDF 1 and there is limited support for UMDF 1 on newer versions of Windows 10.  Universal Windows drivers must use UMDF 2.  For more info, see <a href="https://docs.microsoft.com/en-us/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2">Getting Started with UMDF</a>.]</p>
<p>The <a href="https://msdn.microsoft.com/224277b4-447f-4981-aabf-90a10322c0df">RetrieveDeviceInstanceId</a> method retrieves the identifier of an instance of a device.</p>


## -syntax

````
HRESULT RetrieveDeviceInstanceId(
  [out, optional] PWSTR Buffer,
  [in, out]       DWORD *pdwSizeInChars
);
````


## -parameters
<dl>

### -param <i>Buffer</i> [out, optional]

<dd>
<p>A pointer to a buffer that receives a <b>NULL</b>-terminated string that represents the identifier of an instance of a device if the supplied buffer is non-<b>NULL</b> and <a href="https://msdn.microsoft.com/224277b4-447f-4981-aabf-90a10322c0df">RetrieveDeviceInstanceId</a> is successful. </p>
</dd>

### -param <i>pdwSizeInChars</i> [in, out]

<dd>
<p>A pointer to a variable that receives the number of characters, including the <b>NULL</b> character, in the string that <i>Buffer</i> points to.</p>
<p>If <i>Buffer</i> is <b>NULL</b>, the value that the driver supplies is zero. The framework then returns the size, in characters, that is required for the identifier string.</p>
<p>If <i>Buffer</i> is non-<b>NULL</b>, the framework returns the size, in characters, of the identifier string. </p>
</dd>
</dl>

## -returns
<p>
<a href="https://msdn.microsoft.com/224277b4-447f-4981-aabf-90a10322c0df">RetrieveDeviceInstanceId</a> returns S_OK for the following scenarios: </p>

<p>
<ul>
<li>
<p>The buffer that the <i>Buffer</i> parameter pointed to was non-<b>NULL</b> and large enough to hold the identifier string, including the <b>NULL</b> character, and the framework successfully copied the string into the supplied buffer and set the variable that was pointed to by the <i>pdwSizeInChars</i> parameter to the number of characters in the string.</p>
</li>
<li>
<p>The buffer at <i>Buffer</i> was <b>NULL</b>, the driver preset the variable at <i>pdwSizeInChars</i> to 0, and the framework set the variable at <i>pdwSizeInChars</i> to the number of characters that are required for the string.</p>
</li>
</ul>
<a href="https://msdn.microsoft.com/224277b4-447f-4981-aabf-90a10322c0df">RetrieveDeviceInstanceId</a> returns HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER) to indicate that the supplied buffer is non-<b>NULL</b> and does not contain enough space to hold the identifier string. The framework sets the variable at <i>pdwSizeInChars</i> to the number of characters that are required for the string.

</p>

<p>The buffer that the <i>Buffer</i> parameter pointed to was non-<b>NULL</b> and large enough to hold the identifier string, including the <b>NULL</b> character, and the framework successfully copied the string into the supplied buffer and set the variable that was pointed to by the <i>pdwSizeInChars</i> parameter to the number of characters in the string.</p>

<p>The buffer at <i>Buffer</i> was <b>NULL</b>, the driver preset the variable at <i>pdwSizeInChars</i> to 0, and the framework set the variable at <i>pdwSizeInChars</i> to the number of characters that are required for the string.</p>

<p>
<a href="https://msdn.microsoft.com/224277b4-447f-4981-aabf-90a10322c0df">RetrieveDeviceInstanceId</a> might also return other HRESULT values.
</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff556965">IWDFDeviceInitialize</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20IWDFDeviceInitialize::RetrieveDeviceInstanceId method%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>