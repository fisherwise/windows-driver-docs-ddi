---
UID: NF.portcls.PcForwardContentToInterface
title: PcForwardContentToInterface
author: windows-driver-content
description: The PcForwardContentToInterface function accepts a pointer to the COM interface of an object to which the caller intends to forward protected content.
old-location: audio\pcforwardcontenttointerface.htm
ms.assetid: 5aa6aa90-ef41-467e-a096-5ab660b3f357
ms.author: windowsdriverdev
ms.date: 10/30/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: audio
req.header: portcls.h
req.include-header: Portcls.h
req.target-type: Universal
req.target-min-winverclnt: The PortCls system driver implements the PcForwardContentToInterface function in Microsoft Windows XP and later operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: PcForwardContentToInterface
req.alt-loc: Portcls.lib,Portcls.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Portcls.lib
req.dll: 
req.irql: 
ms.keywords: PcForwardContentToInterface
req.iface: 
---

# PcForwardContentToInterface function



## -description
<p>The <b>PcForwardContentToInterface</b> function accepts a pointer to the COM interface of an object to which the caller intends to forward protected content. Note that this function call is identical in operation to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff536353">DrmForwardContentToInterface</a> function, and its parameter definitions and return value are also identical.</p>


## -syntax

````
PORTCLASSAPI NTSTATUS NTAPI  PcForwardContentToInterface(void);
````


## -parameters


## -returns
<p>See return value definition in <a href="https://msdn.microsoft.com/library/windows/hardware/ff536353">DrmForwardContentToInterface</a>.</p>

<p>See return value definition in <a href="https://msdn.microsoft.com/library/windows/hardware/ff536353">DrmForwardContentToInterface</a>.</p>

<p>See return value definition in <a href="https://msdn.microsoft.com/library/windows/hardware/ff536353">DrmForwardContentToInterface</a>.</p>

## -remarks
<p>For more information, see the comments in <a href="https://msdn.microsoft.com/library/windows/hardware/ff536353">DrmForwardContentToInterface</a>.</p>

<p>For more information, see the comments in <a href="https://msdn.microsoft.com/library/windows/hardware/ff536353">DrmForwardContentToInterface</a>.</p>

<p>For more information, see the comments in <a href="https://msdn.microsoft.com/library/windows/hardware/ff536353">DrmForwardContentToInterface</a>.</p>

<p>For more information, see the comments in <a href="https://msdn.microsoft.com/library/windows/hardware/ff536353">DrmForwardContentToInterface</a>.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt><a href="http://go.microsoft.com/fwlink/p/?linkid=531356" target="_blank">Universal</a></dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>The PortCls system driver implements the <b>PcForwardContentToInterface</b> function in Microsoft Windows XP and later operating systems.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Portcls.h (include Portcls.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Portcls.lib</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536353">DrmForwardContentToInterface</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [audio\audio]:%20PcForwardContentToInterface function%20 RELEASE:%20(10/30/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>