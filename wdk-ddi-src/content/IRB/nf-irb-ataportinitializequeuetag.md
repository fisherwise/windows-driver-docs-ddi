---
UID: NF.irb.AtaPortInitializeQueueTag
title: AtaPortInitializeQueueTag
author: windows-driver-content
description: The AtaPortInitializeQueueTag routine initializes the queue tag list for the specified device.Note  The ATA port driver and ATA miniport driver models may be altered or unavailable in the future.
old-location: storage\ataportinitializequeuetag.htm
ms.assetid: f6d40f3e-4bc9-4b30-97ac-600a33280305
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
req.alt-api: AtaPortInitializeQueueTag
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
ms.keywords: AtaPortInitializeQueueTag
req.iface: 
---

# AtaPortInitializeQueueTag function



## -description
<p>The <b>AtaPortInitializeQueueTag</b> routine initializes the queue tag list for the specified device.</p>


## -syntax

````
BOOLEAN AtaPortInitializeQueueTag(
  _In_ PVOID ChannelExtension,
  _In_ UCHAR TargetId,
  _In_ UCHAR Lun,
  _In_ UCHAR MaxQueueTag
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
<p>Specifies the logical unit number (LUN) of the device.</p>
</dd>

### -param <i>MaxQueueTag</i> [in]

<dd>
<p>Specifies the maximum allowed value for the queue tag.</p>
</dd>
</dl>

## -returns
<p><b>AtaPortInitializeQueueTag</b> returns <b>TRUE</b> if the operation succeeds. Otherwise, it returns <b>FALSE</b>. </p>

## -remarks
<p>The miniport driver should call <b>AtaPortInitializeQueueTag</b> before it uses <a href="https://msdn.microsoft.com/library/windows/hardware/ff550144">AtaPortAllocateQueueTag</a> and <a href="https://msdn.microsoft.com/library/windows/hardware/ff550214">AtaPortReleaseQueueTag</a> to allocate and release queue tags respectively. </p>

<p>The values in the <i>TargetId</i> and <i>Lun</i> parameters specify the device to which the queue tag belongs. To generate channel specific queue tags, the miniport driver should set the <i>TargetId</i> and <i>Lun</i> parameters to IDE_UNTAGGED. </p>

<p>The miniport driver should call <b>AtaPortInitializeQueueTag</b> before it uses <a href="https://msdn.microsoft.com/library/windows/hardware/ff550144">AtaPortAllocateQueueTag</a> and <a href="https://msdn.microsoft.com/library/windows/hardware/ff550214">AtaPortReleaseQueueTag</a> to allocate and release queue tags respectively. </p>

<p>The values in the <i>TargetId</i> and <i>Lun</i> parameters specify the device to which the queue tag belongs. To generate channel specific queue tags, the miniport driver should set the <i>TargetId</i> and <i>Lun</i> parameters to IDE_UNTAGGED. </p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550214">AtaPortReleaseQueueTag</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20AtaPortInitializeQueueTag routine%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>