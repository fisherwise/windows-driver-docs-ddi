---
UID: NS.iscsiop._SetGenerationalGuid_IN
title: SetGenerationalGuid_IN
author: windows-driver-content
description: The SetGenerationalGuid_IN structure holds the input data for the SetGenerationalGuid method.
old-location: storage\setgenerationalguid_in.htm
ms.assetid: 24568c37-9641-4e3e-b788-f71db4f3f70f
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
req.alt-api: SetGenerationalGuid_IN
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
ms.keywords: SetGenerationalGuid_IN, SetGenerationalGuid_IN, *PSetGenerationalGuid_IN
req.iface: 
---

# SetGenerationalGuid_IN structure



## -description
<p>The SetGenerationalGuid_IN structure holds the input data for the <a href="https://msdn.microsoft.com/library/windows/hardware/ff565678">SetGenerationalGuid</a> method.</p>


## -syntax

````
typedef struct _SetGenerationalGuid_IN {
  UCHAR GenerationalGuid[16];
} SetGenerationalGuid_IN, *PSetGenerationalGuid_IN;
````


## -struct-fields
<dl>

### -field <b>GenerationalGuid</b>

<dd>
<p>A 16-byte GUID that identifies the version of the information that is currently in the initiator cache. </p>
</dd>
</dl>

## -remarks
<p>You must implement this method.</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff565678">SetGenerationalGuid</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff565687">SetGenerationalGuid_OUT</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20SetGenerationalGuid_IN structure%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>