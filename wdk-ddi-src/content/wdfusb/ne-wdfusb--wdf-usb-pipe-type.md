---
UID: NE.wdfusb._WDF_USB_PIPE_TYPE
title: WDF_USB_PIPE_TYPE
author: windows-driver-content
description: The WDF_USB_PIPE_TYPE enumeration identifies the types of USB pipes.
old-location: wdf\wdf_usb_pipe_type.htm
ms.assetid: ae230ff0-4fd9-417b-8ee0-80e3ca5a30ff
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: wdf
req.header: wdfusb.h
req.include-header: Wdfusb.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 2.0
req.alt-api: WDF_USB_PIPE_TYPE
req.alt-loc: wdfusb.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: WDF_TIMER_CONFIG, WDF_TIMER_CONFIG, *PWDF_TIMER_CONFIG
req.iface: 
req.product: Windows 10 or later.
---

# WDF_USB_PIPE_TYPE enumeration



## -description
<p class="CCE_Message">[Applies to KMDF and UMDF]</p>
<p>The <b>WDF_USB_PIPE_TYPE</b> enumeration identifies the types of USB pipes.</p>


## -syntax

````
typedef enum _WDF_USB_PIPE_TYPE { 
  WdfUsbPipeTypeInvalid      = 0,
  WdfUsbPipeTypeControl      = 1,
  WdfUsbPipeTypeIsochronous  = 2,
  WdfUsbPipeTypeBulk         = 3,
  WdfUsbPipeTypeInterrupt    = 4
} WDF_USB_PIPE_TYPE;
````


## -enum-fields
<dl>

### -field <a id="WdfUsbPipeTypeInvalid"></a><a id="wdfusbpipetypeinvalid"></a><a id="WDFUSBPIPETYPEINVALID"></a><b>WdfUsbPipeTypeInvalid</b>

<dd>
<p>Reserved for internal use.</p>
</dd>

### -field <a id="WdfUsbPipeTypeControl"></a><a id="wdfusbpipetypecontrol"></a><a id="WDFUSBPIPETYPECONTROL"></a><b>WdfUsbPipeTypeControl</b>

<dd>
<p>The pipe is a control pipe.</p>
</dd>

### -field <a id="WdfUsbPipeTypeIsochronous"></a><a id="wdfusbpipetypeisochronous"></a><a id="WDFUSBPIPETYPEISOCHRONOUS"></a><b>WdfUsbPipeTypeIsochronous</b>

<dd>
<p>The pipe is an isochronous pipe. </p>
</dd>

### -field <a id="WdfUsbPipeTypeBulk"></a><a id="wdfusbpipetypebulk"></a><a id="WDFUSBPIPETYPEBULK"></a><b>WdfUsbPipeTypeBulk</b>

<dd>
<p>The pipe is a bulk pipe.</p>
</dd>

### -field <a id="WdfUsbPipeTypeInterrupt"></a><a id="wdfusbpipetypeinterrupt"></a><a id="WDFUSBPIPETYPEINTERRUPT"></a><b>WdfUsbPipeTypeInterrupt</b>

<dd>
<p>The pipe is an interrupt pipe.</p>
</dd>
</dl>

## -remarks
<p>The <b>WDF_USB_PIPE_TYPE</b> enumeration is used in the <a href="https://msdn.microsoft.com/library/windows/hardware/ff553037">WDF_USB_PIPE_INFORMATION</a> structure.</p>

<p>The <b>WDF_USB_PIPE_TYPE</b> enumeration is used in the <a href="https://msdn.microsoft.com/library/windows/hardware/ff553037">WDF_USB_PIPE_INFORMATION</a> structure.</p>

<p>The <b>WDF_USB_PIPE_TYPE</b> enumeration is used in the <a href="https://msdn.microsoft.com/library/windows/hardware/ff553037">WDF_USB_PIPE_INFORMATION</a> structure.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum KMDF version</p>
</th>
<td width="70%">
<p>1.0</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum UMDF version</p>
</th>
<td width="70%">
<p>2.0</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdfusb.h (include Wdfusb.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553037">WDF_USB_PIPE_INFORMATION</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WDF_USB_PIPE_TYPE enumeration%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>