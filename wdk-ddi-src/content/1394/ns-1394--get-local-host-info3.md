---
UID: NS.1394._GET_LOCAL_HOST_INFO3
title: GET_LOCAL_HOST_INFO3
author: windows-driver-content
description: The GET_LOCAL_HOST_INFO3 structure contains the data returned by a REQUEST_GET_LOCAL_HOST_INFO request using u.GetLocalHostInformation.nLevel = GET_POWER_SUPPLIED.
old-location: ieee\get_local_host_info3.htm
ms.assetid: 49c24328-dfd9-4d4d-a40f-a375f1384a5c
ms.author: windowsdriverdev
ms.date: 10/23/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: IEEE
req.header: 1394.h
req.include-header: 1394.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: GET_LOCAL_HOST_INFO3
req.alt-loc: 1394.h
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
ms.keywords: GET_LOCAL_HOST_INFO3, GET_LOCAL_HOST_INFO3, *PGET_LOCAL_HOST_INFO3
---

# GET_LOCAL_HOST_INFO3 structure



## -description
<p>The GET_LOCAL_HOST_INFO3 structure contains the data returned by a <a href="https://msdn.microsoft.com/library/windows/hardware/ff537644">REQUEST_GET_LOCAL_HOST_INFO</a> request using <b>u.GetLocalHostInformation.nLevel</b> = GET_POWER_SUPPLIED.</p>


## -syntax

````
typedef struct _GET_LOCAL_HOST_INFO3 {
  ULONG deciWattsSupplied;
  ULONG Voltage;
} GET_LOCAL_HOST_INFO3, *PGET_LOCAL_HOST_INFO3;
````


## -struct-fields
<dl>

### -field <b>deciWattsSupplied</b>

<dd>
<p>Specifies the wattage supplied, in tenths of a watt.</p>
</dd>

### -field <b>Voltage</b>

<dd>
<p>Specifies the voltage, in tenths of a volt.</p>
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
<dt>1394.h (include 1394.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff537644">REQUEST_GET_LOCAL_HOST_INFO</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [IEEE\buses]:%20GET_LOCAL_HOST_INFO3 structure%20 RELEASE:%20(10/23/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>