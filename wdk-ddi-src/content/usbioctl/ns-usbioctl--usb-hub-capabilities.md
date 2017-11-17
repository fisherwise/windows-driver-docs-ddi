---
UID: NS.usbioctl._USB_HUB_CAPABILITIES
title: USB_HUB_CAPABILITIES
author: windows-driver-content
description: The USB_HUB_CAPABILITIES structure has been deprecated. Use USB_HUB_CAPABILITIES_EX instead.
old-location: buses\usb_hub_capabilities.htm
ms.assetid: a87f747f-474d-401d-9757-0820680e5c8e
ms.author: windowsdriverdev
ms.date: 11/3/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: usbref
req.header: usbioctl.h
req.include-header: Usbioctl.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: USB_HUB_CAPABILITIES
req.alt-loc: usbioctl.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: <=DISPATCH_LEVEL
ms.keywords: USB_HUB_CAPABILITIES, USB_HUB_CAPABILITIES, *PUSB_HUB_CAPABILITIES
req.iface: 
req.product: Windows 10 or later.
---

# USB_HUB_CAPABILITIES structure



## -description
<p>The <b>USB_HUB_CAPABILITIES</b> structure has been deprecated. Use <a href="https://msdn.microsoft.com/library/windows/hardware/ff539329">USB_HUB_CAPABILITIES_EX</a> instead.</p>


## -syntax

````
typedef struct _USB_HUB_CAPABILITIES {
  ULONG HubIs2xCapable  :1;
} USB_HUB_CAPABILITIES, *PUSB_HUB_CAPABILITIES;
````


## -struct-fields
<dl>

### -field <b>HubIs2xCapable</b>

<dd>
<p>If <b>TRUE</b>, the hub is capable of running at high speed.</p>
</dd>
</dl>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Usbioctl.h (include Usbioctl.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff537312">IOCTL_USB_GET_HUB_CAPABILITIES</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539330">USB_HUB_CAP_FLAGS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff539329">USB_HUB_CAPABILITIES_EX</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff540160">USB Structures</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [usbref\buses]:%20USB_HUB_CAPABILITIES structure%20 RELEASE:%20(11/3/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>