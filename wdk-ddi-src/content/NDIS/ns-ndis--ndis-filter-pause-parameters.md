---
UID: NS.ndis._NDIS_FILTER_PAUSE_PARAMETERS
title: NDIS_FILTER_PAUSE_PARAMETERS
author: windows-driver-content
description: The NDIS_FILTER_PAUSE_PARAMETERS structure defines the pause parameters for the filter module.
old-location: netvista\ndis_filter_pause_parameters.htm
ms.assetid: 070c6d5d-9942-4bff-8894-9aa69d5e7983
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: netvista
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Windows
req.target-min-winverclnt: Supported in NDIS 6.0 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NDIS_FILTER_PAUSE_PARAMETERS
req.alt-loc: ndis.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: See Remarks section
ms.keywords: NDIS_FILTER_PAUSE_PARAMETERS, NDIS_FILTER_PAUSE_PARAMETERS, *PNDIS_FILTER_PAUSE_PARAMETERS
req.iface: 
---

# NDIS_FILTER_PAUSE_PARAMETERS structure



## -description
<p>The NDIS_FILTER_PAUSE_PARAMETERS structure defines the pause parameters for the filter module.</p>


## -syntax

````
typedef struct _NDIS_FILTER_PAUSE_PARAMETERS {
  NDIS_OBJECT_HEADER Header;
  ULONG              Flags;
  ULONG              PauseReason;
} NDIS_FILTER_PAUSE_PARAMETERS, *PNDIS_FILTER_PAUSE_PARAMETERS;
````


## -struct-fields
<dl>

### -field <b>Header</b>

<dd>
<p>The 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff566588">NDIS_OBJECT_HEADER</a> structure for the
     NDIS_FILTER_PAUSE_PARAMETERS structure. NDIS sets the 
     <b>Type</b> member of the structure that 
     <b>Header</b> specifies to NDIS_OBJECT_TYPE_FILTER_PAUSE_PARAMETERS, the 
     <b>Revision</b> member to NDIS_FILTER_PAUSE_PARAMETERS_REVISION_1, and the 
     <b>Size</b> member to NDIS_SIZEOF_FILTER_PAUSE_PARAMETERS_REVISION_1.</p>
</dd>

### -field <b>Flags</b>

<dd>
<p>Reserved.</p>
</dd>

### -field <b>PauseReason</b>

<dd>
<div class="alert"><b>Note</b>  This member is deprecated for NDIS 6.40 and later drivers.</div>
<div> </div>
<p>The value will always be NDIS_PAUSE_NDIS_INTERNAL.</p>
</dd>
</dl>

## -remarks
<p>To define filter module pause parameters, NDIS passes a pointer to an NDIS_FILTER_PAUSE_PARAMETERS
    structure to the 
    <a href="https://msdn.microsoft.com/a239889e-ec39-48fc-9e82-c8bc3d7ca51a">FilterPause</a> function.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Supported in NDIS 6.0 and later.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ndis.h (include Ndis.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/a239889e-ec39-48fc-9e82-c8bc3d7ca51a">FilterPause</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff566588">NDIS_OBJECT_HEADER</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NDIS_FILTER_PAUSE_PARAMETERS structure%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>