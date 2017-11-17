---
UID: NS.dbgeng._DEBUG_PROCESSOR_IDENTIFICATION_X86
title: DEBUG_PROCESSOR_IDENTIFICATION_X86
author: windows-driver-content
description: Identifies an x86 processor.
old-location: debugger\debug_processor_identification_x86.htm
ms.assetid: B5AD9CE8-B0F0-49BC-984E-4372FD3BF93B
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: debugger
req.header: dbgeng.h
req.include-header: DbgEng.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DEBUG_PROCESSOR_IDENTIFICATION_X86
req.alt-loc: DbgEng.h
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
ms.keywords: DEBUG_PROCESSOR_IDENTIFICATION_X86, DEBUG_PROCESSOR_IDENTIFICATION_X86, *PDEBUG_PROCESSOR_IDENTIFICATION_X86
req.iface: IDebugSystemObjects4
---

# DEBUG_PROCESSOR_IDENTIFICATION_X86 structure



## -description
<p>Identifies an x86 processor. </p>


## -syntax

````
typedef struct _DEBUG_PROCESSOR_IDENTIFICATION_X86 {
  ULONG Family;
  ULONG Model;
  ULONG Stepping;
  CHAR  VendorString[16];
} DEBUG_PROCESSOR_IDENTIFICATION_X86, *PDEBUG_PROCESSOR_IDENTIFICATION_X86;
````


## -struct-fields
<dl>

### -field <b>Family</b>

<dd>
<p>The family of the processor.</p>
</dd>

### -field <b>Model</b>

<dd>
<p>The model of the processor.</p>
</dd>

### -field <b>Stepping</b>

<dd>
<p>The stepping value of the processor.</p>
</dd>

### -field <b>VendorString</b>

<dd>
<p>A vendor specified string.</p>
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
<dt>DbgEng.h (include DbgEng.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/2C4C03BC-0D84-4151-B1A1-FE76F0355CD6">DEBUG_PROCESSOR_IDENTIFICATION_ALL</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [debugger\debugger]:%20DEBUG_PROCESSOR_IDENTIFICATION_X86 structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>