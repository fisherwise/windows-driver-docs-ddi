---
UID: NS:usbioctl._USB_PROTOCOLS
title: "_USB_PROTOCOLS"
author: windows-driver-content
description: The USB_PROTOCOLS union is used to report the Universal Serial Bus (USB) signaling protocols that are supported by the port.
old-location: buses\usb_protocols.htm
old-project: usbref
ms.assetid: F970A7FB-DF6F-414B-8B4B-C7E4C5C620B1
ms.author: windowsdriverdev
ms.date: 3/29/2018
ms.keywords: "*PUSB_PROTOCOLS, PUSB_PROTOCOLS, PUSB_PROTOCOLS union pointer [Buses], USB_PROTOCOLS, USB_PROTOCOLS union [Buses], _USB_PROTOCOLS, buses.usb_protocols, usbioctl/PUSB_PROTOCOLS, usbioctl/USB_PROTOCOLS"
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: usbioctl.h
req.include-header: Usbioctl.h
req.target-type: Windows
req.target-min-winverclnt: Windows 8
req.target-min-winversvr: None supported
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: "<=DISPATCH_LEVEL"
topic_type:
-	APIRef
-	kbSyntax
api_type:
-	HeaderDef
api_location:
-	usbioctl.h
api_name:
-	USB_PROTOCOLS
product:
- Windows
targetos: Windows
req.typenames: USB_PROTOCOLS, *PUSB_PROTOCOLS
req.product: Windows 10 or later.
---

# _USB_PROTOCOLS structure


## -description


The <b>USB_PROTOCOLS</b> union is used to report the Universal Serial Bus (USB) signaling protocols that are supported by the port.

The  supported protocols are retrieved in the <a href="https://msdn.microsoft.com/library/windows/hardware/hh406295">USB_NODE_CONNECTION_INFORMATION_EX_V2</a> structure by the <a href="https://msdn.microsoft.com/library/windows/hardware/hh450861">IOCTL_USB_GET_NODE_CONNECTION_INFORMATION_EX_V2</a> I/O control request.

In the <a href="https://msdn.microsoft.com/library/windows/hardware/hh450861">IOCTL_USB_GET_NODE_CONNECTION_INFORMATION_EX_V2</a> request, the caller specifies a bitwise <b>OR</b> of one or more flags defined in <b>USB_PROTOCOLS</b>. Upon successful completion, the request retrieves flags, which indicate the protocols that are actually supported by the port.


## -struct-fields




### -field ul

A bitmask that indicates the USB signaling protocols that are supported by the port.


#### - ReservedMBZ

Reserved. Do not use.


#### - Usb110

If <b>TRUE</b>, the port supports the protocols that are defined in the USB 1.1 Specification. This indicates that the port supports full-speed and low-speed operations.  <b>Usb110</b> is always TRUE for high-speed ports because those ports support full-speed and low-speed operations through split transactions and transaction translators.


#### - Usb200

If <b>TRUE</b>, the port supports the protocols that are defined USB 2.0 Specification. This indicates that the port supports high-speed operations.


#### - Usb300

If <b>TRUE</b>, the port supports the protocols that are defined USB 3.0 Specification. This indicates that the port supports SuperSpeed operations.


## -see-also




<a href="https://msdn.microsoft.com/library/windows/hardware/hh450861">IOCTL_USB_GET_NODE_CONNECTION_INFORMATION_EX_V2</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/hh406295">USB_NODE_CONNECTION_INFORMATION_EX_V2</a>
 

 

