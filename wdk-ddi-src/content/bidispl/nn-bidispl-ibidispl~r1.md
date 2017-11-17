---
UID: NN.bidispl.IBidiSpl~r1
title: IBidiSpl
author: windows-driver-content
description: The IBidiSpl interface allows an application or other objects to send a single bidi request or a list of bidi requests.
old-location: print\ibidispl.htm
ms.assetid: 7e4a30b2-ac3a-475a-b818-455cdb7a91bf
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: interface
ms.prod: windows-hardware
ms.technology: print
req.header: bidispl.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows XP
req.target-min-winversvr: Windows Server 2003
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IBidiSpl
req.alt-loc: Bidispl.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: IBidiSpl2, UnbindDevice, IBidiSpl2::UnbindDevice
req.iface: IBidiSpl2
---

# IBidiSpl interface



## -description
<p>The <b>IBidiSpl</b> interface allows an application or other objects to send a single bidi request or a list of bidi requests.</p>


## -inheritance
<p>The <b xmlns:loc="http://microsoft.com/wdcml/l10n">IBidiSpl</b> interface inherits from the <a href="com.iunknown" xmlns:loc="http://microsoft.com/wdcml/l10n"><b>IUnknown</b></a> interface. <b>IBidiSpl</b> also has these types of members:</p>

<p>The <b>IBidiSpl</b> interface has these methods.</p>

<p>Binds a printer to a bidi request.</p>

<p>Sends a list of bidi requests.</p>

<p>Sends a bidi request.</p>

<p>Unbinds a printer.</p>

<p> </p>

## -members
<p>The <b>IBidiSpl</b> interface has these methods.</p><table class="members" id="memberListMethods">
<tr>
<th align="left" width="37%">Method</th>
<th align="left" width="63%">Description</th>
</tr>
<tr data="declared;">
<td align="left" width="37%">
<a href="https://msdn.microsoft.com/880ff314-c79d-4395-83ad-ce61bb8da5b5">BindDevice</a>
</td>
<td align="left" width="63%">
<p>Binds a printer to a bidi request.</p>
</td>
</tr>
<tr data="declared;">
<td align="left" width="37%">
<a href="https://msdn.microsoft.com/d61d7f58-281c-4c82-a579-aaedbf507bae">MultiSendRecv</a>
</td>
<td align="left" width="63%">
<p>Sends a list of bidi requests.</p>
</td>
</tr>
<tr data="declared;">
<td align="left" width="37%">
<a href="https://msdn.microsoft.com/0c91abd0-5e49-4e23-a50f-9d1dacf9d868">SendRecv</a>
</td>
<td align="left" width="63%">
<p>Sends a bidi request.</p>
</td>
</tr>
<tr data="declared;">
<td align="left" width="37%">
<a href="https://msdn.microsoft.com/4c294d1d-5a37-4ea4-b50f-447260e885b1">UnbindDevice</a>
</td>
<td align="left" width="63%">
<p>Unbinds a printer.</p>
</td>
</tr>
</table><p>Binds a printer to a bidi request.</p>

<p>Sends a list of bidi requests.</p>

<p>Sends a bidi request.</p>

<p>Unbinds a printer.</p>

<p> </p>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows XP</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>Windows Server 2003</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Bidispl.h</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545163">Bidirectional Communication Interfaces</a>
</dt>
<dt>
<a href="NULL">Bidirectional Communication Schema</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/dd144980">IBidiSpl</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [print\print]:%20IBidiSpl interface%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>