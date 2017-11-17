---
UID: NE.pcivirt._SRIOV_PF_EVENT
title: SRIOV_PF_EVENT
author: windows-driver-content
description: Defines event values for the SR-IOV device.
old-location: pci\sriov_pf_event.htm
ms.assetid: e2b40a9d-57e6-49b1-839a-d34acb108807
ms.author: windowsdriverdev
ms.date: 10/23/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: PCI
req.header: pcivirt.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: SRIOV_PF_EVENT
req.alt-loc: Pcivirt.h
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
ms.keywords: PARCLASS_INFORMATION, PARCLASS_INFORMATION, *PPARCLASS_INFORMATION
req.iface: 
---

# SRIOV_PF_EVENT enumeration



## -description
<p>Defines event values for the SR-IOV device.</p>


## -syntax

````
typedef enum _SRIOV_PF_EVENT { 
  SriovEventPfQueryStopDevice,
  SriovEventPfRestart,
  SriovEventPfMaximum
} SRIOV_PF_EVENT;
````


## -enum-fields
<dl>

### -field <a id="SriovEventPfQueryStopDevice"></a><a id="srioveventpfquerystopdevice"></a><a id="SRIOVEVENTPFQUERYSTOPDEVICE"></a><b>SriovEventPfQueryStopDevice</b>

<dd>
<p>The SR-IOV device is stopped.</p>
</dd>

### -field <a id="SriovEventPfRestart"></a><a id="srioveventpfrestart"></a><a id="SRIOVEVENTPFRESTART"></a><b>SriovEventPfRestart</b>

<dd>
<p>The SR-IOV device is restarted</p>
</dd>

### -field <a id="SriovEventPfMaximum"></a><a id="srioveventpfmaximum"></a><a id="SRIOVEVENTPFMAXIMUM"></a><b>SriovEventPfMaximum</b>

<dd>
<p>Reserved.</p>
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
<dt>Pcivirt.h</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="buses.ioctl_sriov_notification">IOCTL_SRIOV_NOTIFICATION</a>
</dt>
<dt>
<a href="buses.ioctl_sriov_event_complete">IOCTL_SRIOV_EVENT_COMPLETE</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [PCI\buses]:%20SRIOV_PF_EVENT enumeration%20 RELEASE:%20(10/23/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>