---
UID: NS.wsk._WSK_CLIENT_STREAM_DISPATCH
title: WSK_CLIENT_STREAM_DISPATCH
author: windows-driver-content
description: The WSK_CLIENT_STREAM_DISPATCH structure specifies a WSK application's dispatch table of event callback functions for a stream socket.
old-location: netvista\wsk_client_stream_dispatch.htm
ms.assetid: 7E682868-1D39-4677-A4EC-E7C9F841EC82
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: netvista
req.header: wsk.h
req.include-header: Wsk.h
req.target-type: Windows
req.target-min-winverclnt: Windows 10, version 1703
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: WSK_CLIENT_STREAM_DISPATCH
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
ms.keywords: WSK_CLIENT_STREAM_DISPATCH, WSK_CLIENT_STREAM_DISPATCH, *PWSK_CLIENT_STREAM_DISPATCH
req.iface: 
req.product: Windows 10 or later.
---

# WSK_CLIENT_STREAM_DISPATCH structure



## -description
<p>The WSK_CLIENT_STREAM_DISPATCH structure specifies a WSK application's dispatch table of event callback functions for a stream socket. Because a stream socket can act either as a listening socket or a connection-oriented socket, this structure allows a stream socket to access the dispatch tables for both the WSK_CLIENT_LISTEN_DISPATCH structure and the WSK_CLIENT_CONNECTION_DISPATCH structure.
  </p>


## -syntax

````
typedef struct _WSK_CLIENT_STREAM_DISPATCH {
  CONST WSK_CLIENT_LISTEN_DISPATCH*     Listen;
  CONST WSK_CLIENT_CONNECTION_DISPATCH* Connect;
} WSK_CLIENT_STREAM_DISPATCH, *PWSK_CLIENT_STREAM_DISPATCH;
````


## -struct-fields
<dl>

### -field <b>Listen</b>

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff571162">WSK_CLIENT_LISTEN_DISPATCH</a> structure, which specifies a WSK application's dispatch table of event
  callback functions for a stream socket which is acting as a listening socket.</p>
</dd>

### -field <b>Connect</b>

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff571156">WSK_CLIENT_CONNECTION_DISPATCH</a> structure, which specifies a WSK application's dispatch table of event
  callback functions for a stream socket which is acting as a connection-oriented socket.</p>
</dd>
</dl>

## -remarks
<p>A WSK application passes a pointer to a <b>WSK_CLIENT_STREAM_DISPATCH</b> structure to the WSK subsystem when
    the WSK application calls the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff571149">WskSocket</a> function to create a stream
    socket.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Windows 10, version 1703</p>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff571149">WskSocket</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff571156">WSK_CLIENT_CONNECTION_DISPATCH</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff571162">WSK_CLIENT_LISTEN_DISPATCH</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/A10B901E-9987-40E9-976B-4CD9455E0AEE">WSK_PROVIDER_STREAM_DISPATCH</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20WSK_CLIENT_STREAM_DISPATCH structure%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>