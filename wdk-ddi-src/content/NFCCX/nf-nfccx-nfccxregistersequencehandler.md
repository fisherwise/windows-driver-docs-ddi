---
UID: NF.nfccx.NfcCxRegisterSequenceHandler
title: NfcCxRegisterSequenceHandler
author: windows-driver-content
description: Called by the client driver during initialization to register for handling specific sequences.
old-location: nfpdrivers\_nfccxregistersequencehandler.htm
ms.assetid: 30957475-D02B-434D-9FAB-BBCD5732DCA5
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: nfpdrivers
req.header: nfccx.h
req.include-header: Ncidef.h
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: None supported
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NfcCxRegisterSequenceHandler
req.alt-loc: NfcCx.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Nfccxstub.lib
req.dll: NfcCx.dll
req.irql: 
ms.keywords: NfcCxRegisterSequenceHandler
req.iface: 
---

# NfcCxRegisterSequenceHandler function



## -description
<p>Called by the client driver during initialization to register for handling specific sequences.</p>


## -syntax

````
NTSTATUS NfcCxRegisterSequenceHandler(
   WDFDEVICE                   Device,
   NFC_CX_SEQUENCE             Sequence,
   PFN_NFC_CX_SEQUENCE_HANDLER EvtNfcCxSequenceHandler
);
````


## -parameters
<dl>

### -param <i>Device</i> 

<dd>
<p>A handle to a framework device object.</p>
</dd>

### -param <i>Sequence</i> 

<dd>
<p>An <a href="https://msdn.microsoft.com/library/windows/hardware/dn905563">NFC_CX_SEQUENCE</a>-typed enumerator.</p>
</dd>

### -param <i>EvtNfcCxSequenceHandler</i> 

<dd>
<p>A pointer to an <a href="https://msdn.microsoft.com/6EB96A37-06B9-4655-AD69-375EE770F4DF">EvtNfcCxSequenceHandler</a> callback function. </p>
</dd>
</dl>

## -returns
<p>If the operation succeeds, the function returns STATUS_SUCCESS.

</p>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 10</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>None supported</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Nfccx.h (include Ncidef.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Nfccxstub.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>NfcCx.dll</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt><a href="http://go.microsoft.com/fwlink/p/?LinkID=785320">Near field communication (NFC) design guide</a></dt>
<dt><a href="https://msdn.microsoft.com/windows/hardware/drivers/nfc/nfc-class-extension-">NFC class extension design guide</a></dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [nfpdrivers\nfpdrivers]:%20NfcCxRegisterSequenceHandler method%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>