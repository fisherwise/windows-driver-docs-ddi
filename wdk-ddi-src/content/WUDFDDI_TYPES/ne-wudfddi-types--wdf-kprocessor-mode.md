---
UID: NE.wudfddi_types._WDF_KPROCESSOR_MODE
title: WDF_KPROCESSOR_MODE
author: windows-driver-content
description: The WDF_KPROCESSOR_MODE enumeration type identifies the processor modes in which a thread can execute.
old-location: wdf\wdf_kprocessor_mode.htm
ms.assetid: b50be4c2-4575-42b9-953d-9ddb3c3e696c
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: wdf
req.header: wudfddi_types.h
req.include-header: Wudfddi.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 1.9
req.alt-api: WDF_KPROCESSOR_MODE
req.alt-loc: Wudfddi_types.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: Unavailable in UMDF 2.0 and later.
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: 
ms.keywords: WRITE_REGISTER_USHORT
req.iface: 
req.product: Windows 10 or later.
---

# WDF_KPROCESSOR_MODE enumeration



## -description
<p class="CCE_Message">[<b>Warning:</b> UMDF 2 is the latest version of UMDF and supersedes UMDF 1.  All new UMDF drivers should be written using UMDF 2.  No new features are being added to UMDF 1 and there is limited support for UMDF 1 on newer versions of Windows 10.  Universal Windows drivers must use UMDF 2.  For more info, see <a href="https://docs.microsoft.com/en-us/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2">Getting Started with UMDF</a>.]</p>
<p>The <b>WDF_KPROCESSOR_MODE</b> enumeration type identifies the processor modes in which a thread can execute.</p>


## -syntax

````
typedef enum _WDF_KPROCESSOR_MODE { 
  WdfKProcessorModeInvalid  = 0,
  WdfKernelMode             = 1,
  WdfUserMode               = 2,
  WdfKProcessorModeMaximum  = 3
} WDF_KPROCESSOR_MODE, *PWDF_KPROCESSOR_MODE;
````


## -enum-fields
<dl>

### -field <a id="WdfKProcessorModeInvalid"></a><a id="wdfkprocessormodeinvalid"></a><a id="WDFKPROCESSORMODEINVALID"></a><b>WdfKProcessorModeInvalid</b>

<dd>
<p>Reserved for system use.</p>
</dd>

### -field <a id="WdfKernelMode"></a><a id="wdfkernelmode"></a><a id="WDFKERNELMODE"></a><b>WdfKernelMode</b>

<dd>
<p>The processor mode is kernel mode.</p>
</dd>

### -field <a id="WdfUserMode"></a><a id="wdfusermode"></a><a id="WDFUSERMODE"></a><b>WdfUserMode</b>

<dd>
<p>The processor mode is user mode.</p>
</dd>

### -field <a id="WdfKProcessorModeMaximum"></a><a id="wdfkprocessormodemaximum"></a><a id="WDFKPROCESSORMODEMAXIMUM"></a><b>WdfKProcessorModeMaximum</b>

<dd>
<p>Valid enumeration values were exceeded.</p>
</dd>
</dl>

## -remarks
<p>The <b>WDF_KPROCESSOR_MODE</b> enumeration type is return type for <a href="https://msdn.microsoft.com/library/windows/hardware/ff559002">IWDFIoRequest2::GetRequestorMode</a>.</p>

<p>The <b>WDF_KPROCESSOR_MODE</b> enumeration type is return type for <a href="https://msdn.microsoft.com/library/windows/hardware/ff559002">IWDFIoRequest2::GetRequestorMode</a>.</p>

<p>The <b>WDF_KPROCESSOR_MODE</b> enumeration type is return type for <a href="https://msdn.microsoft.com/library/windows/hardware/ff559002">IWDFIoRequest2::GetRequestorMode</a>.</p>

## -requirements
<table>
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
<p>1.9</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wudfddi_types.h (include Wudfddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff559002">IWDFIoRequest2::GetRequestorMode</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WDF_KPROCESSOR_MODE enumeration%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>