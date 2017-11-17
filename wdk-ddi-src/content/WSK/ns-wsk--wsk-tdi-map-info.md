---
UID: NS.wsk._WSK_TDI_MAP_INFO
title: WSK_TDI_MAP_INFO
author: windows-driver-content
description: The WSK_TDI_MAP_INFO structure specifies a list that contains mappings of a combination of an address family, a socket type, and a protocol to the device name of a TDI transport.
old-location: netvista\wsk_tdi_map_info.htm
ms.assetid: b0b4fab4-1a3c-4075-8881-f2aa38fba15e
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: netvista
req.header: wsk.h
req.include-header: Wsk.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating
   systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: WSK_TDI_MAP_INFO
req.alt-loc: wsk.h
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
ms.keywords: WSK_TDI_MAP_INFO, WSK_TDI_MAP_INFO, *PWSK_TDI_MAP_INFO
req.iface: 
req.product: Windows 10 or later.
---

# WSK_TDI_MAP_INFO structure



## -description
<p>The WSK_TDI_MAP_INFO structure specifies a list that contains mappings of a combination of an address
  family, a socket type, and a protocol to the device name of a 
  <a href="https://msdn.microsoft.com/3878053c-388a-4bbc-a30e-feb16eda2f99">TDI</a> transport.</p>


## -syntax

````
typedef struct _WSK_TDI_MAP_INFO {
  const ULONG       ElementCount;
  const WSK_TDI_MAP *Map;
} WSK_TDI_MAP_INFO, *PWSK_TDI_MAP_INFO;
````


## -struct-fields
<dl>

### -field <b>ElementCount</b>

<dd>
<p>The number of structures contained in the array pointed to by the 
     <b>Map</b> member.</p>
</dd>

### -field <b>Map</b>

<dd>
<p>A pointer to an array of 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff571191">WSK_TDI_MAP</a> structures. Each WSK_TDI_MAP
     structure in the array contains a mapping of a particular address family, socket type, and protocol to
     the device name of a 
     <a href="https://msdn.microsoft.com/3878053c-388a-4bbc-a30e-feb16eda2f99">TDI</a> transport.</p>
</dd>
</dl>

## -remarks
<p>A WSK application passes a pointer to a WSK_TDI_MAP_INFO structure to the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff571126">WskControlClient</a> function when specifying
    
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff571190">WSK_TDI_DEVICENAME_MAPPING</a> for
    the control code.</p>

<p>If a WSK application uses the WSK_TDI_DEVICENAME_MAPPING client control operation to map combinations
    of address family, socket type, and protocol to device names of 
    <a href="https://msdn.microsoft.com/3878053c-388a-4bbc-a30e-feb16eda2f99">TDI</a> transports, it must do so before it creates any
    sockets.</p>

<p>For more information about using TDI transports, see 
    <a href="NULL">Using TDI Transports</a>.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Available in Windows Vista and later versions of the Windows operating
   systems.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wsk.h (include Wsk.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff571126">WskControlClient</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff571191">WSK_TDI_MAP</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20WSK_TDI_MAP_INFO structure%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>