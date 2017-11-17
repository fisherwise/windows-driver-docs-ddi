---
UID: NF.winsplp.RouterFreeBidiResponseContainer
title: RouterFreeBidiResponseContainer
author: windows-driver-content
description: RouterFreeBidiResponseContainer frees a BIDI_RESPONSE_CONTAINER structure previously allocated by RouterAllocBidiResponseContainer.
old-location: print\routerfreebidiresponsecontainer.htm
ms.assetid: 3998eed5-398e-4835-b917-54f5ae814ddf
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: print
req.header: winsplp.h
req.include-header: Winsplp.h
req.target-type: Desktop
req.target-min-winverclnt: This function is available in Windows XP and later operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RouterFreeBidiResponseContainer
req.alt-loc: WinSpool.drv
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: WinSpool.lib
req.dll: WinSpool.drv
req.irql: 
ms.keywords: RouterFreeBidiResponseContainer
req.iface: 
req.product: Windows 10 or later.
---

# RouterFreeBidiResponseContainer function



## -description
<p><code>RouterFreeBidiResponseContainer</code> frees a <a href="https://msdn.microsoft.com/library/windows/hardware/ff545202">BIDI_RESPONSE_CONTAINER</a> structure previously allocated by <a href="https://msdn.microsoft.com/library/windows/hardware/ff562001">RouterAllocBidiResponseContainer</a>.</p>


## -syntax

````
DWORD RouterFreeBidiResponseContainer(
  _In_ PBIDI_RESPONSE_CONTAINER pData
);
````


## -parameters
<dl>

### -param <i>pData</i> [in]

<dd>
<p>Pointer to the BIDI_RESPONSE_CONTAINER structure to be freed.</p>
</dd>
</dl>

## -returns
<p><code>RouterFreeBidiResponseContainer</code> normally returns ERROR_SUCCESS, unless it throws an exception. In that case it returns an appropriate error code.</p>

## -remarks


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
<p>Version</p>
</th>
<td width="70%">
<p>This function is available in Windows XP and later operating systems.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Winsplp.h (include Winsplp.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>WinSpool.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>WinSpool.drv</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545202">BIDI_RESPONSE_CONTAINER</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562001">RouterAllocBidiResponseContainer</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [print\print]:%20RouterFreeBidiResponseContainer function%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>