---
UID: NF.irb.AtaPortReleaseQueueTag
title: AtaPortReleaseQueueTag
author: windows-driver-content
description: The AtaPortReleaseQueueTag routine releases the specified queue tag.Note  The ATA port driver and ATA miniport driver models may be altered or unavailable in the future.
old-location: storage\ataportreleasequeuetag.htm
ms.assetid: 54399050-740f-4af8-ad85-cd3060f14af4
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: Storage
req.header: irb.h
req.include-header: Ata.h, Irb.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: AtaPortReleaseQueueTag
req.alt-loc: ataport.lib,ataport.dll,pciidex.lib,pciidex.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ataport.lib; 
Pciidex.lib
req.dll: 
req.irql: 
ms.keywords: AtaPortReleaseQueueTag
req.iface: 
---

# AtaPortReleaseQueueTag function



## -description
<p>The <b>AtaPortReleaseQueueTag</b> routine releases the specified queue tag.</p>


## -syntax

````
VOID AtaPortReleaseQueueTag(
  _In_ PVOID ChannelExtension,
  _In_ UCHAR TargetId,
  _In_ UCHAR Lun,
  _In_ UCHAR QueueTag
);
````


## -parameters
<dl>

### -param <i>ChannelExtension</i> [in]

<dd>
<p>A pointer to the channel extension.</p>
</dd>

### -param <i>TargetId</i> [in]

<dd>
<p>Specifies the target identifier of the device.</p>
</dd>

### -param <i>Lun</i> [in]

<dd>
<p>Specifies the logical unit number of the device.</p>
</dd>

### -param <i>QueueTag</i> [in]

<dd>
<p>Specifies the queue tag to be freed.</p>
</dd>
</dl>

## -returns
<p>None </p>

## -remarks
<p>The miniport driver should call <b>AtaPortReleaseQueueTag</b> to free allocated queue tags by using <a href="https://msdn.microsoft.com/library/windows/hardware/ff550144">AtaPortAllocateQueueTag</a>. </p>

<p>The miniport driver should call <b>AtaPortReleaseQueueTag</b> to free allocated queue tags by using <a href="https://msdn.microsoft.com/library/windows/hardware/ff550144">AtaPortAllocateQueueTag</a>. </p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt>Desktop</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Irb.h (include Ata.h or Irb.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Ataport.lib; </dt>
<dt>Pciidex.lib</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550144">AtaPortAllocateQueueTag</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550168">AtaPortInitializeQueueTag</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20AtaPortReleaseQueueTag routine%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>