---
UID: NF.ks.KsCreateTopologyNode~r1
title: KsCreateTopologyNode
author: windows-driver-content
description: The KsCreateTopologyNode function creates a handle to a topology node instance. The function can only be called at PASSIVE_LEVEL.
old-location: stream\kscreatetopologynode.htm
ms.assetid: aeed8086-b413-428c-b275-d555523b5503
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: stream
req.header: ks.h
req.include-header: Ks.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: KsCreateTopologyNode
req.alt-loc: ks.lib,ks.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ks.lib
req.dll: 
req.irql: 
ms.keywords: KsCreateTopologyNode
req.iface: 
---

# KsCreateTopologyNode function



## -description
<p>The <b>KsCreateTopologyNode</b> function creates a handle to a topology node instance. The function can only be called at <b>PASSIVE_LEVEL</b>.</p>


## -syntax

````
NTSTATUS KsCreateTopologyNode(
  _In_  HANDLE         ParentHandle,
  _In_  PKSNODE_CREATE NodeCreate,
  _In_  ACCESS_MASK    DesiredAccess,
  _Out_ PHANDLE        NodeHandle
);
````


## -parameters
<dl>

### -param <i>ParentHandle</i> [in]

<dd>
<p>Specifies the handle to the parent on which the node is created.</p>
</dd>

### -param <i>NodeCreate</i> [in]

<dd>
<p>Specifies topology node create parameters.</p>
</dd>

### -param <i>DesiredAccess</i> [in]

<dd>
<p>Specifies an <a href="https://msdn.microsoft.com/library/windows/hardware/ff540466">ACCESS_MASK</a> indicating the desired access to the object. This is typically <b>GENERIC_READ</b> and/or <b>GENERIC_WRITE</b>.</p>
</dd>

### -param <i>NodeHandle</i> [out]

<dd>
<p>Location for the topology node handle.</p>
</dd>
</dl>

## -returns
<p>Returns <b>STATUS_SUCCESS</b>, or an error if unable to create a node. </p>

## -remarks
<p>The <a href="https://msdn.microsoft.com/library/windows/hardware/ff563471">KSNODE_CREATE</a> structure describes the set of information used to create the node handle.</p>

<p>The <a href="https://msdn.microsoft.com/library/windows/hardware/ff563471">KSNODE_CREATE</a> structure describes the set of information used to create the node handle.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt><a href="http://go.microsoft.com/fwlink/p/?linkid=531356" target="_blank">Universal</a></dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ks.h (include Ks.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Ks.lib</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff540466">ACCESS_MASK</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563471">KSNODE_CREATE</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [stream\stream]:%20KsCreateTopologyNode function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>