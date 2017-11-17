---
UID: NF.storport.StorPortCompleteRequest
title: StorPortCompleteRequest
author: windows-driver-content
description: The StorPortCompleteRequest routine completes all outstanding requests setting the SRB status value to SrbStatus.
old-location: storage\storportcompleterequest.htm
ms.assetid: 20ee0633-a743-46e8-a094-37099b8e4427
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: Storage
req.header: storport.h
req.include-header: Storport.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: StorPortCompleteRequest
req.alt-loc: Storport.lib,Storport.dll
req.ddi-compliance: StorPortCompleteRequest, StorPortDDIsPortOnly
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Storport.lib
req.dll: 
req.irql: 
ms.keywords: StorPortCompleteRequest
req.iface: 
req.product: Windows 10 or later.
---

# StorPortCompleteRequest function



## -description
<p>The <b>StorPortCompleteRequest</b> routine completes all outstanding requests setting the SRB status value to <b>SrbStatus</b>. </p>


## -syntax

````
STORPORT_API VOID StorPortCompleteRequest(
  _In_ PVOID HwDeviceExtension,
  _In_ UCHAR PathId,
  _In_ UCHAR TargetId,
  _In_ UCHAR Lun,
  _In_ UCHAR SrbStatus
);
````


## -parameters
<dl>

### -param <i>HwDeviceExtension</i> [in]

<dd>
<p>A pointer to the hardware device extension. This is a per HBA storage area that the port driver allocates and initializes on behalf of the miniport driver. Miniport drivers usually store HBA-specific information in this extension, such as the state of the HBA and the mapped access ranges for the HBA. This area is available to the miniport driver immediately after the miniport driver calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff567108">StorPortInitialize</a>. The port driver frees this memory when it removes the device. </p>
</dd>

### -param <i>PathId</i> [in]

<dd>
<p>Identifies the SCSI bus. A value of SP_UNTAGGED indicates all buses controlled by the HBA. </p>
</dd>

### -param <i>TargetId</i> [in]

<dd>
<p>Identifies the target controller or device on the given buses. A value of SP_UNTAGGED indicates all targets on the bus. </p>
</dd>

### -param <i>Lun</i> [in]

<dd>
<p>Identifies the logical unit for the given target controller or device. A value of SP_UNTAGGED indicates all logical units for the given target controllers on the given buses. Full-duplex miniport drivers must not assign a value of SP_UNTAGGED to this member.</p>
</dd>

### -param <i>SrbStatus</i> [in]

<dd>
<p>Specifies the completion status to be set in the <b>SrbStatus</b>member of each SRB.</p>
</dd>
</dl>

## -returns
<p>None </p>

## -remarks
<p>We do not recommend that writers of Storport miniport drivers use this particular Storport interface routine. Instead, the miniport driver should call StorPortNotification( RequestComplete ) for each outstanding request.</p>

<p>We do not recommend that writers of Storport miniport drivers use this particular Storport interface routine. Instead, the miniport driver should call StorPortNotification( RequestComplete ) for each outstanding request.</p>

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
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Storport.h (include Storport.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Storport.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567042">StorPortCompleteRequest</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh454262">StorPortDDIsPortOnly</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564608">ScsiPortCompleteRequest</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20StorPortCompleteRequest routine%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>