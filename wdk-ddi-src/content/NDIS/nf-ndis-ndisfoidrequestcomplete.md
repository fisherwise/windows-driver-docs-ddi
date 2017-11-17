---
UID: NF.ndis.NdisFOidRequestComplete
title: NdisFOidRequestComplete
author: windows-driver-content
description: Filter drivers call the NdisFOidRequestComplete function to return the final status of an OID request for which the driver's FilterOidRequest function returned NDIS_STATUS_PENDING.
old-location: netvista\ndisfoidrequestcomplete.htm
ms.assetid: 1d72e8e3-1053-4731-a16c-fc3e4f7460e9
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: netvista
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Desktop
req.target-min-winverclnt: Supported in NDIS 6.0 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NdisFOidRequestComplete
req.alt-loc: ndis.lib,ndis.dll
req.ddi-compliance: Irql_OID_Function
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ndis.lib
req.dll: 
req.irql: <= DISPATCH_LEVEL
ms.keywords: NdisFOidRequestComplete
req.iface: 
---

# NdisFOidRequestComplete function



## -description
<p>Filter drivers call the 
  <b>NdisFOidRequestComplete</b> function to return the final status of an OID request for which the driver's 
  <a href="https://msdn.microsoft.com/238bfa21-a971-4fe4-a774-6ba834efc3c5">FilterOidRequest</a> function returned
  NDIS_STATUS_PENDING.</p>


## -syntax

````
VOID NdisFOidRequestComplete(
  _In_ NDIS_HANDLE       NdisFilterHandle,
  _In_ PNDIS_OID_REQUEST OidRequest,
  _In_ NDIS_STATUS       Status
);
````


## -parameters
<dl>

### -param <i>NdisFilterHandle</i> [in]

<dd>
<p>The NDIS handle that identifies this filter module. NDIS passed the handle to the filter driver in
     a call to the 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff540442">FilterAttach</a> function.</p>
</dd>

### -param <i>OidRequest</i> [in]

<dd>
<p>A pointer to a buffer formatted as an 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff566710">NDIS_OID_REQUEST</a> structure. The filter
     driver obtained this pointer as an input parameter to its 
     <a href="https://msdn.microsoft.com/238bfa21-a971-4fe4-a774-6ba834efc3c5">FilterOidRequest</a> function.</p>
</dd>

### -param <i>Status</i> [in]

<dd>
<p>The final status of the request operation, either NDIS_STATUS_SUCCESS or any driver-determined
     NDIS_STATUS_<i>XXX</i> value except NDIS_STATUS_PENDING.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>A filter driver that returns NDIS_STATUS_PENDING from its 
    <a href="https://msdn.microsoft.com/238bfa21-a971-4fe4-a774-6ba834efc3c5">FilterOidRequest</a> function must call
    the 
    <b>NdisFOidRequestComplete</b> function after the driver has finished the request operation.</p>

<p>If an overlying driver originated the OID request, NDIS calls the request complete function of the
    overlying driver after the filter driver calls 
    <b>NdisFOidRequestComplete</b>.</p>

<p>A filter driver that returns NDIS_STATUS_PENDING from its 
    <a href="https://msdn.microsoft.com/238bfa21-a971-4fe4-a774-6ba834efc3c5">FilterOidRequest</a> function must call
    the 
    <b>NdisFOidRequestComplete</b> function after the driver has finished the request operation.</p>

<p>If an overlying driver originated the OID request, NDIS calls the request complete function of the
    overlying driver after the filter driver calls 
    <b>NdisFOidRequestComplete</b>.</p>

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
<p>&lt;= DISPATCH_LEVEL</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547990">Irql_OID_Function</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff540442">FilterAttach</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/238bfa21-a971-4fe4-a774-6ba834efc3c5">FilterOidRequest</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff566710">NDIS_OID_REQUEST</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NdisFOidRequestComplete function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>