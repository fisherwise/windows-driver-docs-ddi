---
UID: NF.ndis.NdisGetRoutineAddress
title: NdisGetRoutineAddress
author: windows-driver-content
description: The NdisGetRoutineAddress function returns the address of a routine given the routine's name.
old-location: netvista\ndisgetroutineaddress.htm
ms.assetid: 98257b56-e586-41e7-80c3-f9f96d471125
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: netvista
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Universal
req.target-min-winverclnt: Supported for NDIS 6.0 and NDIS 5.1 drivers (see 
   NdisGetRoutineAddress (NDIS
   5.1)) in Windows Vista. Supported for NDIS 5.1 drivers (see 
   NdisGetRoutineAddress (NDIS
   5.1)) in Windows XP.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NdisGetRoutineAddress
req.alt-loc: ndis.lib,ndis.dll
req.ddi-compliance: Irql_Miscellaneous_Function
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ndis.lib
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: NdisGetRoutineAddress
req.iface: 
---

# NdisGetRoutineAddress function



## -description
<p>The 
  <b>NdisGetRoutineAddress</b> function returns the address of a routine given the routine's name.</p>


## -syntax

````
PVOID NdisGetRoutineAddress(
  _In_ PNDIS_STRING NdisRoutineName
);
````


## -parameters
<dl>

### -param <i>NdisRoutineName</i> [in]

<dd>
<p>A pointer to a 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff564879">UNICODE_STRING</a> structure that specifies the
     string that contains the name of a routine.</p>
</dd>
</dl>

## -returns
<p>Returns the address of the routine whose name is specified at 
     <i>NdisRoutineName</i> if the routine is available; otherwise, <b>NULL</b>.</p>

## -remarks
<p>An NDIS driver can use 
    <b>NdisGetRoutineAddress</b> to obtain the address of an exported NDIS routine. The driver can then use
    this address to call the NDIS routine.</p>

<p>An NDIS driver can use 
    <b>NdisGetRoutineAddress</b> if the driver must remain backward compatible. For example, if such a driver
    imports an NDIS routine that is not exported by the version of NDIS that is currently running, the I/O
    manager will not load the driver on the operating system. However, the driver can first use 
    <b>NdisGetRoutineAddress</b> to determine whether the routine is available in the version of NDIS that is
    currently running. If available, the address of the routine is returned. The driver can then use the
    address to call the routine. If not available, <b>NULL</b> is returned. The driver cannot call the routine, but
    the driver still loads on the operating system.</p>

<p>No performance improvement is gained by using the address that is returned by 
    <b>NdisGetRoutineAddress</b> instead of calling the specified routine by name. Therefore, do not write an
    NDIS driver to use 
    <b>NdisGetRoutineAddress</b> if you know that the NDIS version with which the driver will run exports the
    specified routine.</p>

<p>Typically, an NDIS driver calls 
    <b>NdisGetRoutineAddress</b> in its 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff552644">DriverEntry</a> routine.</p>

<p>An NDIS driver can use 
    <b>NdisGetRoutineAddress</b> to obtain the address of an exported NDIS routine. The driver can then use
    this address to call the NDIS routine.</p>

<p>An NDIS driver can use 
    <b>NdisGetRoutineAddress</b> if the driver must remain backward compatible. For example, if such a driver
    imports an NDIS routine that is not exported by the version of NDIS that is currently running, the I/O
    manager will not load the driver on the operating system. However, the driver can first use 
    <b>NdisGetRoutineAddress</b> to determine whether the routine is available in the version of NDIS that is
    currently running. If available, the address of the routine is returned. The driver can then use the
    address to call the routine. If not available, <b>NULL</b> is returned. The driver cannot call the routine, but
    the driver still loads on the operating system.</p>

<p>No performance improvement is gained by using the address that is returned by 
    <b>NdisGetRoutineAddress</b> instead of calling the specified routine by name. Therefore, do not write an
    NDIS driver to use 
    <b>NdisGetRoutineAddress</b> if you know that the NDIS version with which the driver will run exports the
    specified routine.</p>

<p>Typically, an NDIS driver calls 
    <b>NdisGetRoutineAddress</b> in its 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff552644">DriverEntry</a> routine.</p>

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
<p>Supported for NDIS 6.0 and NDIS 5.1 drivers (see 
   <a href="https://msdn.microsoft.com/40f173ec-86a1-4ff9-b035-ba68351ce28e">NdisGetRoutineAddress (NDIS
   5.1)</a>) in Windows Vista. Supported for NDIS 5.1 drivers (see 
   <b>NdisGetRoutineAddress (NDIS
   5.1)</b>) in Windows XP.</p>
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
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Ndis.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>PASSIVE_LEVEL</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547982">Irql_Miscellaneous_Function</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552644">DriverEntry</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564879">UNICODE_STRING</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NdisGetRoutineAddress function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>