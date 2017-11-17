---
UID: NE.ntddk._BDCB_CALLBACK_TYPE
title: BDCB_CALLBACK_TYPE
author: windows-driver-content
description: The BDCB_CALLBACK_TYPE enumeration specifies whether the callback being passed to a BOOT_DRIVER_CALLBACK_FUNCTION routine is a status update or a boot-start driver initialization notification.
old-location: kernel\bdcb_callback_type.htm
ms.assetid: 22698DF4-7B8C-40B8-9B07-EEDCC03D0D0F
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: kernel
req.header: ntddk.h
req.include-header: Ntddk.h
req.target-type: Windows
req.target-min-winverclnt: Available starting with  Windows 8.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: BDCB_CALLBACK_TYPE
req.alt-loc: ntddk.h
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
ms.keywords: FILTER_INITIALIZATION_DATA, FILTER_INITIALIZATION_DATA, *PFILTER_INITIALIZATION_DATA
req.iface: 
---

# BDCB_CALLBACK_TYPE enumeration



## -description
<p>The BDCB_CALLBACK_TYPE enumeration specifies  whether the callback being passed to a <a href="https://msdn.microsoft.com/28BA4B54-F493-4D79-89DF-D890EBCF1E9C">BOOT_DRIVER_CALLBACK_FUNCTION</a> routine is a status update or a boot-start driver initialization notification.</p>


## -syntax

````
typedef enum _BDCB_CALLBACK_TYPE { 
  BdCbStatusUpdate,
  BdCbInitializeImage
} BDCB_CALLBACK_TYPE;
````


## -enum-fields
<dl>

### -field <a id="BdCbStatusUpdate"></a><a id="bdcbstatusupdate"></a><a id="BDCBSTATUSUPDATE"></a><b>BdCbStatusUpdate</b>

<dd>
<p>A status update provided by the system to a boot-start driver.</p>
</dd>

### -field <a id="BdCbInitializeImage"></a><a id="bdcbinitializeimage"></a><a id="BDCBINITIALIZEIMAGE"></a><b>BdCbInitializeImage</b>

<dd>
<p>A boot image is about to be initialized. During this callback, boot-start drivers may classify a boot image as a known good image or a known bad image.</p>
</dd>
</dl>

## -remarks
<p>The two callback types have unique context structures that provide additional information specific to the callback.</p>

<p>BdCbStatusUpdate</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh406367">BDCB_STATUS_UPDATE_TYPE</a>
</p>

<p>BdCbInitializeImage</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh406355">BDCB_CLASSIFICATION</a>
</p>

<p> </p>

<p>The two callback types have unique context structures that provide additional information specific to the callback.</p>

<p>BdCbStatusUpdate</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh406367">BDCB_STATUS_UPDATE_TYPE</a>
</p>

<p>BdCbInitializeImage</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh406355">BDCB_CLASSIFICATION</a>
</p>

<p> </p>

<p>The two callback types have unique context structures that provide additional information specific to the callback.</p>

<p>BdCbStatusUpdate</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh406367">BDCB_STATUS_UPDATE_TYPE</a>
</p>

<p>BdCbInitializeImage</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh406355">BDCB_CLASSIFICATION</a>
</p>

<p> </p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Available starting with  Windows 8.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntddk.h (include Ntddk.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/28BA4B54-F493-4D79-89DF-D890EBCF1E9C">BOOT_DRIVER_CALLBACK_FUNCTION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh406367">BDCB_STATUS_UPDATE_TYPE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh406355">BDCB_CLASSIFICATION</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20BDCB_CALLBACK_TYPE enumeration%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>