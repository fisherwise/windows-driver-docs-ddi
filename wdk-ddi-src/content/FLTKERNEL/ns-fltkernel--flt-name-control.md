---
UID: NS.fltkernel._FLT_NAME_CONTROL
title: FLT_NAME_CONTROL
author: windows-driver-content
description: A minifilter that provides file names for the Filter Manager's name cache can use the FLT_NAME_CONTROL structure to manage its name buffers.
old-location: ifsk\flt_name_control.htm
ms.assetid: 0f796ad1-e4b4-4113-b076-ed6c9ea711c9
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: ifsk
req.header: fltkernel.h
req.include-header: Fltkernel.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FLT_NAME_CONTROL
req.alt-loc: fltkernel.h
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
ms.keywords: FLT_NAME_CONTROL, FLT_NAME_CONTROL, *PFLT_NAME_CONTROL
req.iface: 
---

# FLT_NAME_CONTROL structure



## -description
<p>A minifilter that provides file names for the Filter Manager's name cache can use the FLT_NAME_CONTROL structure to manage its name buffers. </p>


## -syntax

````
typedef struct _FLT_NAME_CONTROL {
  UNICODE_STRING Name;
} FLT_NAME_CONTROL, *PFLT_NAME_CONTROL;
````


## -struct-fields
<dl>

### -field <b>Name</b>

<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564879">UNICODE_STRING</a> structure that contains the file name string. </p>
</dd>
</dl>

## -remarks
<p>Minifilters must not attempt to free or replace the buffer in the <a href="https://msdn.microsoft.com/library/windows/hardware/ff564879">UNICODE_STRING</a> structure  that the <b>Name</b> member points to directly. Instead, minifilters should call <a href="https://msdn.microsoft.com/library/windows/hardware/ff541829">FltCheckAndGrowNameControl</a> to obtain a larger name control buffer. </p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Fltkernel.h (include Fltkernel.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541829">FltCheckAndGrowNameControl</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543030">FltGetFileNameFormat</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543032">FltGetFileNameInformation</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543035">FltGetFileNameInformationUnsafe</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543040">FltGetFileNameQueryMethod</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564879">UNICODE_STRING</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20FLT_NAME_CONTROL structure%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>