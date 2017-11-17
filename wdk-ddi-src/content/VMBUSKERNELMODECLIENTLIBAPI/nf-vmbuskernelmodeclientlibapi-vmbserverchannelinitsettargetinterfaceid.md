---
UID: NF.vmbuskernelmodeclientlibapi.VmbServerChannelInitSetTargetInterfaceId
title: VmbServerChannelInitSetTargetInterfaceId
author: windows-driver-content
description: The VmbServerChannelInitSetTargetInterfaceId function sets the target interface type GUID and instance GUID of the channel offer.
old-location: netvista\vmbserverchannelinitsettargetinterfaceid.htm
ms.assetid: 09123845-F734-48B6-A593-0368CD195379
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: netvista
req.header: vmbuskernelmodeclientlibapi.h
req.include-header: VmbusKernelModeClientLibApi.h
req.target-type: Windows
req.target-min-winverclnt: Windows 8.1
req.target-min-winversvr: Windows Server 2012 R2
req.kmdf-ver: 1.13
req.umdf-ver: 2.0
req.alt-api: VmbServerChannelInitSetTargetInterfaceId
req.alt-loc: VmbusKernelModeClientLibApi.h
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
ms.keywords: VmbServerChannelInitSetTargetInterfaceId
req.iface: 
req.product: Windows 10 or later.
---

# VmbServerChannelInitSetTargetInterfaceId function



## -description
<p class="CCE_Message">[Some information relates to pre-released product which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.]</p>
<p>The <b>VmbServerChannelInitSetTargetInterfaceId</b> function sets the target interface type GUID and instance GUID of the channel offer.  </p>


## -syntax

````
NTSTATUS
 VmbServerChannelInitSetTargetInterfaceId(
  _In_ VMBCHANNEL Channel,
  _In_ GUID       InterfaceType,
  _In_ GUID       InterfaceInstance
);
````


## -parameters
<dl>

### -param <i>Channel</i> [in]

<dd>
<p>A handle for a channel.  </p>
</dd>

### -param <i>InterfaceType</i> [in]

<dd>
<p>A pointer to the interface type GUID.
</p>
</dd>

### -param <i>InterfaceInstance</i> [in]

<dd>
<p>A pointer to the instance type GUID.</p>
</dd>
</dl>

## -remarks
<p>The <i>InterfaceType</i>
GUID identifies the type of channel and, specifically, the protocol that is used with
the channel.  If the VMBus in the child partition is creating a Physical Device Object
(PDO) that is associated with this channel, this GUID is the basis of the PDO's hardware
ID reported to the PnP Manager.  </p>

<p>The <i>InterfaceInstance</i> GUID identifies a specific instance
of the service.  For instance, If you have two paravirtual network interfaces, they
have the same interface type, but different interface instance values. </p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 8.1</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>Windows Server 2012 R2</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum KMDF version</p>
</th>
<td width="70%">
<p>1.13</p>
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
<dt>VmbusKernelModeClientLibApi.h (include VmbusKernelModeClientLibApi.h)</dt>
</dl>
</td>
</tr>
</table>