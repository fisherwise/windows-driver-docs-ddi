---
UID: NF.wdm.KeQueryHighestNodeNumber
title: KeQueryHighestNodeNumber
author: windows-driver-content
description: The KeQueryHighestNodeNumber routine returns the highest node number in a multiprocessor system that has a non-uniform memory access (NUMA) architecture.
old-location: kernel\kequeryhighestnodenumber.htm
ms.assetid: e92387db-0c35-40c8-8342-4b1bf498aa1a
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: Available in Windows 7 and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: KeQueryHighestNodeNumber
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: Any level
ms.keywords: KeQueryHighestNodeNumber
req.iface: 
req.product: Windows 10 or later.
---

# KeQueryHighestNodeNumber function



## -description
<p>The <b>KeQueryHighestNodeNumber</b> routine returns the highest node number in a multiprocessor system that has a non-uniform memory access (NUMA) architecture. </p>


## -syntax

````
USHORT KeQueryHighestNodeNumber(void);
````


## -parameters


## -returns
<p><b>KeQueryHighestNodeNumber</b> returns the highest node number.</p>

<p><b>KeQueryHighestNodeNumber</b> returns the highest node number.</p>

<p><b>KeQueryHighestNodeNumber</b> returns the highest node number.</p>

## -remarks
<p>In a non-uniform memory access (NUMA) multiprocessor architecture, a node is a collection of processors that share fast access to a region of memory. Memory access is non-uniform because a processor can access the memory in its node faster than it can access the memory in other nodes.</p>

<p>If a NUMA multiprocessor system contains <i>n</i> nodes, the nodes are numbered from 0 to <i>n</i>-1, and <b>KeQueryHighestNodeNumber</b> returns <i>n</i>-1. If a system contains one node, <b>KeQueryHighestNodeNumber</b> returns zero.</p>

<p>If a system does not have a NUMA architecture, <b>KeQueryHighestNodeNumber</b> returns zero. An example of non-NUMA architecture is a symmetric multiprocessor system (SMP).</p>

<p>When Windows initializes a NUMA multiprocessor system, it assigns logical processors to nodes and counts the number of resulting nodes. Windows defines the capacity of a node as the number of processors that are present when the system starts in addition to any other logical processors that can be added to the node while the system is running. If, during initialization, Windows encounters a NUMA hardware node that contains more logical processors than will fit into a group, Windows splits the node into smaller, logical nodes. Each of these nodes does not exceed the maximum group size. The value that is returned by <b>KeQueryHighestNodeNumber</b> indicates the number of logical nodes in the system.</p>

<p>After the system has been initialized, the node count remains fixed while the system continues to run. This count might include memory-only nodes, which are nodes that contain memory but no active logical processors.</p>

<p>In a non-uniform memory access (NUMA) multiprocessor architecture, a node is a collection of processors that share fast access to a region of memory. Memory access is non-uniform because a processor can access the memory in its node faster than it can access the memory in other nodes.</p>

<p>If a NUMA multiprocessor system contains <i>n</i> nodes, the nodes are numbered from 0 to <i>n</i>-1, and <b>KeQueryHighestNodeNumber</b> returns <i>n</i>-1. If a system contains one node, <b>KeQueryHighestNodeNumber</b> returns zero.</p>

<p>If a system does not have a NUMA architecture, <b>KeQueryHighestNodeNumber</b> returns zero. An example of non-NUMA architecture is a symmetric multiprocessor system (SMP).</p>

<p>When Windows initializes a NUMA multiprocessor system, it assigns logical processors to nodes and counts the number of resulting nodes. Windows defines the capacity of a node as the number of processors that are present when the system starts in addition to any other logical processors that can be added to the node while the system is running. If, during initialization, Windows encounters a NUMA hardware node that contains more logical processors than will fit into a group, Windows splits the node into smaller, logical nodes. Each of these nodes does not exceed the maximum group size. The value that is returned by <b>KeQueryHighestNodeNumber</b> indicates the number of logical nodes in the system.</p>

<p>After the system has been initialized, the node count remains fixed while the system continues to run. This count might include memory-only nodes, which are nodes that contain memory but no active logical processors.</p>

<p>In a non-uniform memory access (NUMA) multiprocessor architecture, a node is a collection of processors that share fast access to a region of memory. Memory access is non-uniform because a processor can access the memory in its node faster than it can access the memory in other nodes.</p>

<p>If a NUMA multiprocessor system contains <i>n</i> nodes, the nodes are numbered from 0 to <i>n</i>-1, and <b>KeQueryHighestNodeNumber</b> returns <i>n</i>-1. If a system contains one node, <b>KeQueryHighestNodeNumber</b> returns zero.</p>

<p>If a system does not have a NUMA architecture, <b>KeQueryHighestNodeNumber</b> returns zero. An example of non-NUMA architecture is a symmetric multiprocessor system (SMP).</p>

<p>When Windows initializes a NUMA multiprocessor system, it assigns logical processors to nodes and counts the number of resulting nodes. Windows defines the capacity of a node as the number of processors that are present when the system starts in addition to any other logical processors that can be added to the node while the system is running. If, during initialization, Windows encounters a NUMA hardware node that contains more logical processors than will fit into a group, Windows splits the node into smaller, logical nodes. Each of these nodes does not exceed the maximum group size. The value that is returned by <b>KeQueryHighestNodeNumber</b> indicates the number of logical nodes in the system.</p>

<p>After the system has been initialized, the node count remains fixed while the system continues to run. This count might include memory-only nodes, which are nodes that contain memory but no active logical processors.</p>

<p>In a non-uniform memory access (NUMA) multiprocessor architecture, a node is a collection of processors that share fast access to a region of memory. Memory access is non-uniform because a processor can access the memory in its node faster than it can access the memory in other nodes.</p>

<p>If a NUMA multiprocessor system contains <i>n</i> nodes, the nodes are numbered from 0 to <i>n</i>-1, and <b>KeQueryHighestNodeNumber</b> returns <i>n</i>-1. If a system contains one node, <b>KeQueryHighestNodeNumber</b> returns zero.</p>

<p>If a system does not have a NUMA architecture, <b>KeQueryHighestNodeNumber</b> returns zero. An example of non-NUMA architecture is a symmetric multiprocessor system (SMP).</p>

<p>When Windows initializes a NUMA multiprocessor system, it assigns logical processors to nodes and counts the number of resulting nodes. Windows defines the capacity of a node as the number of processors that are present when the system starts in addition to any other logical processors that can be added to the node while the system is running. If, during initialization, Windows encounters a NUMA hardware node that contains more logical processors than will fit into a group, Windows splits the node into smaller, logical nodes. Each of these nodes does not exceed the maximum group size. The value that is returned by <b>KeQueryHighestNodeNumber</b> indicates the number of logical nodes in the system.</p>

<p>After the system has been initialized, the node count remains fixed while the system continues to run. This count might include memory-only nodes, which are nodes that contain memory but no active logical processors.</p>

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
<p>Version</p>
</th>
<td width="70%">
<p>Available in Windows 7 and later versions of Windows.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdm.h (include Wdm.h, Ntddk.h, or Ntifs.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>NtosKrnl.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>NtosKrnl.exe</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>Any level</p>
</td>
</tr>
</table>