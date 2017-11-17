---
UID: NF.wiautil.wiauDbgLegacyError2
title: wiauDbgLegacyError2
author: windows-driver-content
description: The wiauDbgLegacyError2 function logs an error message.
old-location: image\wiaudbglegacyerror2.htm
ms.assetid: 981fef6c-65a7-4ba1-ad6a-c7c9c2795feb
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: image
req.header: wiautil.h
req.include-header: Wiautil.h
req.target-type: Desktop
req.target-min-winverclnt: Available in Windows XP and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: wiauDbgLegacyError2
req.alt-loc: Wiautil.h
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
ms.keywords: wiauDbgLegacyError2
req.iface: 
req.product: Windows 10 or later.
---

# wiauDbgLegacyError2 function



## -description
<p>The <b>wiauDbgLegacyError2</b> function logs an error message.</p>


## -syntax

````
inline void __stdcall wiauDbgLegacyError2(
   HINSTANCE   hInstance,
   LPCSTR      fmt, ...
);
````


## -parameters
<dl>

### -param <i>hInstance</i> 

<dd>
<p>Specifies the handle to the DLL instance.</p>
</dd>

### -param <i>fmt, ...</i> 

<dd>
<p>Pointer to a format string that specifies a variable argument list, which starts with an ANSI format string containing the message and any conversion specifiers. </p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>The <b>wiauDbgLegacyError2</b> function is identical to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff549633">wiauDbgError</a> function except that the former has a parameter that specifies the handle to the DLL instance and the latter has a parameter used to identify the function or method that is active when the function is called.</p>

<p>The <b>wiauDbgLegacyError2</b> function is identical to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff549633">wiauDbgError</a> function except that the former has a parameter that specifies the handle to the DLL instance and the latter has a parameter used to identify the function or method that is active when the function is called.</p>

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
<p>Available in Windows XP and later.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wiautil.h (include Wiautil.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549633">wiauDbgError</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [image\image]:%20wiauDbgLegacyError2 function%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>