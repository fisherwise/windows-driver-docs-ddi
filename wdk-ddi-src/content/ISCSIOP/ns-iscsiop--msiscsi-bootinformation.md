---
UID: NS.iscsiop._MSiSCSI_BootInformation
title: MSiSCSI_BootInformation
author: windows-driver-content
description: The MSiSCSI_BootInformation structure is used with the MSiSCSI_BootInformation WMI Class to expose information about the node that contains the target boot device.
old-location: storage\msiscsi_bootinformation.htm
ms.assetid: 971bbd30-5bde-4cf6-9b94-7c21c29590d5
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: Storage
req.header: iscsiop.h
req.include-header: Iscsiop.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: MSiSCSI_BootInformation
req.alt-loc: iscsiop.h
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
ms.keywords: MSiSCSI_BootInformation, MSiSCSI_BootInformation, *PMSiSCSI_BootInformation
req.iface: 
---

# MSiSCSI_BootInformation structure



## -description
<p>The MSiSCSI_BootInformation structure is used with the <a href="https://msdn.microsoft.com/library/windows/hardware/ff562984">MSiSCSI_BootInformation WMI Class</a> to expose information about the node that contains the target boot device. </p>


## -syntax

````
typedef struct _MSiSCSI_BootInformation {
  UCHAR NodeName[223];
  ULONG SharedSecretLength;
  UCHAR SharedSecret[255];
} MSiSCSI_BootInformation, *PMSiSCSI_BootInformation;
````


## -struct-fields
<dl>

### -field <b>NodeName</b>

<dd>
<p>The name of the initiator node that contains the boot device.</p>
</dd>

### -field <b>SharedSecretLength</b>

<dd>
<p>The length, in bytes, of the shared secret for the initiator node.</p>
</dd>

### -field <b>SharedSecret</b>

<dd>
<p>The shared secret for the initiator node.</p>
</dd>
</dl>

## -remarks
<p>You must implement this class if the adapter supports iSCSI boot.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Iscsiop.h (include Iscsiop.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/a6ed673a-b5c1-4857-803a-4f0f3cf798d8">MSiSCSI_BootInformationWMI Class</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20MSiSCSI_BootInformation structure%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>