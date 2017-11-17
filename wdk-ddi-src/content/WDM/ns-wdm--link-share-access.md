---
UID: NS.wdm._LINK_SHARE_ACCESS
title: LINK_SHARE_ACCESS
author: windows-driver-content
description: The share access structure used by file systems for only link files.
old-location: kernel\link_share_access.htm
ms.assetid: CD9E3356-45C3-4F56-9EB3-45FB4B3F054B
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: LINK_SHARE_ACCESS
req.alt-loc: Wdm.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL (see Remarks section)
ms.keywords: LINK_SHARE_ACCESS, LINK_SHARE_ACCESS, *PLINK_SHARE_ACCESS
req.iface: 
req.product: Windows 10 or later.
---

# LINK_SHARE_ACCESS structure



## -description
<p>The share access structure used by file systems for only link files. </p>


## -syntax

````
typedef struct _LINK_SHARE_ACCESS {
  ULONG  OpenCount;
  ULONG  Deleters;
  ULONG  SharedDelete;
} LINK_SHARE_ACCESS, *PLINK_SHARE_ACCESS;
````


## -struct-fields
<dl>

### -field <b> OpenCount</b>

<dd>
<p>The number of open requests to the file.</p>
</dd>

### -field <b> Deleters</b>

<dd>
<p>File associated with the file object has been 
      opened for delete access.</p>
</dd>

### -field <b> SharedDelete</b>

<dd>
<p>File associated with the file object has been opened for delete sharing access.</p>
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
<dt>Wdm.h</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/1C34237E-D4AF-4F12-9FF2-9382BADCC9D3">IoCheckLinkShareAccess</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/206D74F6-09D5-4C04-8A0A-A7765E64BB27">IoSetLinkShareAccess</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20LINK_SHARE_ACCESS structure%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>