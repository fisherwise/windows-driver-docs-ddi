---
UID: NF.rxprocs.RxReference
title: RxReference
author: windows-driver-content
description: RxReference increments the NodeReferenceCount member of a structure by one for several of the reference counted data structures used by RDBSS.
old-location: ifsk\rxreference.htm
ms.assetid: 436cd161-6984-4101-931a-221a829f40d0
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: ifsk
req.header: rxprocs.h
req.include-header: Rxprocs.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RxReference
req.alt-loc: rxprocs.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: <= APC_LEVEL
ms.keywords: RxReference
req.iface: 
req.product: Windows 10 or later.
---

# RxReference function



## -description
<p><b>RxReference</b> increments the <b>NodeReferenceCount</b> member of a structure by one for several of the reference counted data structures used by RDBSS. </p>


## -syntax

````
VOID RxReference(
  _Inout_ PVOID Instance
);
````


## -parameters
<dl>

### -param <i>Instance</i> [in, out]

<dd>
<p>A pointer to the reference-counted data structure to be referenced (incremented). </p>
</dd>
</dl>

## -returns
<p>None </p>

## -remarks
<p>The <b>RxReference</b> routine can be used to reference (increment by one) the <b>NodeReferenceCount</b> member on the following data structures used by RDBSS:</p><dl>
<dd>
<p>SRV_CALL</p>
</dd>
<dd>
<p>NET_ROOT</p>
</dd>
<dd>
<p>V_NET_ROOT</p>
</dd>
<dd>
<p>SRV_OPEN</p>
</dd>
<dd>
<p>FOBX</p>
</dd>
</dl><p>SRV_CALL</p>

<p>NET_ROOT</p>

<p>V_NET_ROOT</p>

<p>SRV_OPEN</p>

<p>FOBX</p>

<p>If <b>RxReference</b> is called with any other type of RDBSS data structure, the routine causes the system to ASSERT on checked builds. </p>

<p>The <b>RxReference</b> routine can be used to reference (increment by one) the <b>NodeReferenceCount</b> member on the following data structures used by RDBSS:</p><dl>
<dd>
<p>SRV_CALL</p>
</dd>
<dd>
<p>NET_ROOT</p>
</dd>
<dd>
<p>V_NET_ROOT</p>
</dd>
<dd>
<p>SRV_OPEN</p>
</dd>
<dd>
<p>FOBX</p>
</dd>
</dl><p>SRV_CALL</p>

<p>NET_ROOT</p>

<p>V_NET_ROOT</p>

<p>SRV_OPEN</p>

<p>FOBX</p>

<p>If <b>RxReference</b> is called with any other type of RDBSS data structure, the routine causes the system to ASSERT on checked builds. </p>

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
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Rxprocs.h (include Rxprocs.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&lt;= APC_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff554388">RxDereference</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20RxReference function%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>