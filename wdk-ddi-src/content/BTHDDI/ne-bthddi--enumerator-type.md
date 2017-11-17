---
UID: NE.bthddi._ENUMERATOR_TYPE
title: ENUMERATOR_TYPE
author: windows-driver-content
description: The ENUMERATOR_TYPE enumeration type is used to determine whether the enumerated device is associated with a service or a protocol. The ENUMERATOR_TYPE enumeration is intended for internal use only and should not be used by profile drivers.
old-location: bltooth\enumerator_type.htm
ms.assetid: 2f8ae260-3a4c-44a5-85b7-e3ebcf21522b
ms.author: windowsdriverdev
ms.date: 10/23/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: bltooth
req.header: bthddi.h
req.include-header: Bthddi.h
req.target-type: Windows
req.target-min-winverclnt: Versions: Supported in Windows Vista, and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: ENUMERATOR_TYPE
req.alt-loc: bthddi.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: Developers should code this function to operate at either IRQL = DISPATCH_LEVEL (if the callback
   function does not access paged memory), or IRQL = PASSIVE_LEVEL (if the callback function must access
   paged memory)
ms.keywords: IBidiSpl2, UnbindDevice, IBidiSpl2::UnbindDevice
req.iface: IBidiSpl2
---

# ENUMERATOR_TYPE enumeration



## -description
<p>The ENUMERATOR_TYPE enumeration type is used to determine whether the enumerated device is associated
  with a service or a protocol. The ENUMERATOR_TYPE enumeration is intended for internal use only and should
  not be used by profile drivers.</p>


## -syntax

````
typedef enum _ENUMERATOR_TYPE { 
  ENUMERATOR_TYPE_PROTOCOL  = 0,
  ENUMERATOR_TYPE_SERVICE   = 1,
  ENUMERATOR_TYPE_MAX       = 2
} ENUMERATOR_TYPE, *PENUMERATOR_TYPE;
````


## -enum-fields
<dl>

### -field <a id="ENUMERATOR_TYPE_PROTOCOL"></a><a id="enumerator_type_protocol"></a><b>ENUMERATOR_TYPE_PROTOCOL</b>

<dd>
<p>For internal use only. Do not use.</p>
</dd>

### -field <a id="ENUMERATOR_TYPE_SERVICE"></a><a id="enumerator_type_service"></a><b>ENUMERATOR_TYPE_SERVICE</b>

<dd>
<p>This value should be specified for profile drivers. For more information about how this value is
     used, see 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff536643">BTH_ENUMERATOR_INFO</a>.</p>
</dd>

### -field <a id="ENUMERATOR_TYPE_MAX"></a><a id="enumerator_type_max"></a><b>ENUMERATOR_TYPE_MAX</b>

<dd>
<p>For internal use only. Do not use.</p>
</dd>
</dl>

## -remarks
<p>A value from this enumeration is returned as the 
    <b>EnumeratorType</b> member of the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff536643">BTH_ENUMERATOR_INFO</a> structure, which the 
    <a href="https://msdn.microsoft.com/43cd8e6b-5710-4308-a7c4-fb6f14940977">
    IOCTL_INTERNAL_BTHENUM_GET_ENUMINFO</a> returns in its output buffer.</p>

<p>A value from this enumeration is returned as the 
    <b>EnumeratorType</b> member of the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff536643">BTH_ENUMERATOR_INFO</a> structure, which the 
    <a href="https://msdn.microsoft.com/43cd8e6b-5710-4308-a7c4-fb6f14940977">
    IOCTL_INTERNAL_BTHENUM_GET_ENUMINFO</a> returns in its output buffer.</p>

<p>A value from this enumeration is returned as the 
    <b>EnumeratorType</b> member of the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff536643">BTH_ENUMERATOR_INFO</a> structure, which the 
    <a href="https://msdn.microsoft.com/43cd8e6b-5710-4308-a7c4-fb6f14940977">
    IOCTL_INTERNAL_BTHENUM_GET_ENUMINFO</a> returns in its output buffer.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Versions: Supported in Windows Vista, and later.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Bthddi.h (include Bthddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536643">BTH_ENUMERATOR_INFO</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/43cd8e6b-5710-4308-a7c4-fb6f14940977">
   IOCTL_INTERNAL_BTHENUM_GET_ENUMINFO</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [bltooth\bltooth]:%20ENUMERATOR_TYPE enumeration%20 RELEASE:%20(10/23/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>