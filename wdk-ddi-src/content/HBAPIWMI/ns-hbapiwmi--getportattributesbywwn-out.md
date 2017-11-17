---
UID: NS.hbapiwmi._GetPortAttributesByWWN_OUT
title: GetPortAttributesByWWN_OUT
author: windows-driver-content
description: The GetPortAttributesByWWN_OUT structure is used to report the output parameter data of the GetPortAttributesByWWN WMI method to the WMI client.
old-location: storage\getportattributesbywwn_out.htm
ms.assetid: 9a4d04de-2c44-4f13-ac6f-32e2fe879e4e
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: Storage
req.header: hbapiwmi.h
req.include-header: Hbapiwmi.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: GetPortAttributesByWWN_OUT
req.alt-loc: hbapiwmi.h
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
ms.keywords: GetPortAttributesByWWN_OUT, GetPortAttributesByWWN_OUT, *PGetPortAttributesByWWN_OUT
req.iface: 
---

# GetPortAttributesByWWN_OUT structure



## -description
<p>The GetPortAttributesByWWN_OUT structure is used to report the output parameter data of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff554965">GetPortAttributesByWWN</a> WMI method to the WMI client.</p>


## -syntax

````
typedef struct _GetPortAttributesByWWN_OUT {
  ULONG                         HBAStatus;
  MSFC_HBAPortAttributesResults PortAttributes;
} GetPortAttributesByWWN_OUT, *PGetPortAttributesByWWN_OUT;
````


## -struct-fields
<dl>

### -field <b>HBAStatus</b>

<dd>
<p>Contains a value associated with the WMI class qualifier <a href="https://msdn.microsoft.com/library/windows/hardware/ff557233">HBA_STATUS</a> that indicates the result of an HBA query operation.</p>
</dd>

### -field <b>PortAttributes</b>

<dd>
<p>Contains a structure of type <a href="https://msdn.microsoft.com/library/windows/hardware/ff562510">MSFC_HBAPortAttributesResults</a> that holds the port attributes to be reported.</p>
</dd>
</dl>

## -remarks
<p>The WMI tool suite generates a declaration of the GetPortAttributesByWWN_OUT structure in <i>Hbapiwmi.h </i>when it compiles the <a href="https://msdn.microsoft.com/library/windows/hardware/ff562506">MSFC_HBAAdapterMethods WMI Class</a>.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Hbapiwmi.h (include Hbapiwmi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554965">GetPortAttributesByWWN</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff557233">HBA_STATUS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562510">MSFC_HBAPortAttributesResults</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20GetPortAttributesByWWN_OUT structure%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>