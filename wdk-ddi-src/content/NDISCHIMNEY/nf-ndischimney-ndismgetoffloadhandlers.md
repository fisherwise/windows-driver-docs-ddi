---
UID: NF.ndischimney.NdisMGetOffloadHandlers
title: NdisMGetOffloadHandlers
author: windows-driver-content
description: This function obtains the entry points of the NDIS functions for a particular chimney type.
old-location: netvista\ndismgetoffloadhandlers.htm
ms.assetid: a78acf5d-07ec-487c-97bd-daca8d08863c
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: netvista
req.header: ndischimney.h
req.include-header: Ndischimney.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NdisMGetOffloadHandlers
req.alt-loc: ndischimney.h
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
ms.keywords: NdisMGetOffloadHandlers
req.iface: 
---

# NdisMGetOffloadHandlers function



## -description
<p class="CCE_Message">[The TCP chimney offload feature is deprecated and should not be used.]</p>
<p>This function obtains the entry points of the NDIS functions for a particular chimney type.</p>


## -syntax

````
NDIS_STATUS NdisMGetOffloadHandlers(
  _In_  NDIS_HANDLE                  NdisMiniportHandle,
  _In_  NDIS_CHIMNEY_OFFLOAD_TYPE    ChimneyType,
  _Out_ PNDIS_OFFLOAD_EVENT_HANDLERS *OffloadHandlers
);
````


## -parameters
<dl>

### -param <i>NdisMiniportHandle</i> [in]

<dd>
<p>The handle to a context area that is offload target-allocated in which the offload target
     maintains state information about this instance of the adapter. The offload target provided this handle
     to NDIS when calling 
     <a href="https://msdn.microsoft.com/861626af-23ea-40dc-a91a-7da42d4b0a1c">
     NdisMSetMiniportAttributes</a> from its 
     <a href="https://msdn.microsoft.com/b146fa81-005b-4a6c-962d-4cb023ea790e">
     MiniportInitializeEx</a> function.</p>
</dd>

### -param <i>ChimneyType</i> [in]

<dd>
<p>A chimney type that is one of the following NDIS_CHIMNEY_OFFLOAD_TYPE values:
     </p>
<p></p>
<dl>

### -param <a id="NdisTcpChimneyOffload"></a><a id="ndistcpchimneyoffload"></a><a id="NDISTCPCHIMNEYOFFLOAD"></a><b>NdisTcpChimneyOffload</b>

<dd>
<p>The TCP chimney offload type.</p>
</dd>
</dl>
<p>All other NDIS_CHIMNEY_OFFLOAD_TYPE values are currently reserved.</p>
</dd>

### -param <i>OffloadHandlers</i> [out]

<dd>
<p>A pointer to a variable supplied by the offload target. The size of this variable is 
     sizeof(PNDIS_OFFLOAD_EVENT_HANDLERS). If the call to the 
     <b>NdisMGetOffloadHandlers</b> function succeeds, the function returns, in this variable, a pointer to an
     NDIS_OFFLOAD_EVENT_HANDLERS structure. This structure serves as a header for the chimney-specific
     structure that contains the entry points. The NDIS_OFFLOAD_EVENT_HANDLERS structure is formatted as
     follows:
     </p>
<div class="code"><span codelanguage=""><table>
<tr>
<th></th>
</tr>
<tr>
<td>
<pre>typedef struct _NDIS_OFFLOAD_EVENT_HANDLERS {
  NDIS_OBJECT_HEADER  Header;
} NDIS_OFFLOAD_EVENT_HANDLERS, *PNDIS_OFFLOAD_EVENT_HANDLERS;</pre>
</td>
</tr>
</table></span></div>
<p>This structure contains the following member:</p>
<p></p>
<dl>

### -param <a id="Header"></a><a id="header"></a><a id="HEADER"></a><b>Header</b>

<dd>
<p>Specifies an NDIS object header, which is formatted as an 
       <a href="https://msdn.microsoft.com/library/windows/hardware/ff566588">NDIS_OBJECT_HEADER</a> structure.</p>
</dd>
</dl>
</dd>
</dl>

## -returns
<p><b>NdisMGetOffloadHandlers</b> can return either of the following:</p><dl>
<dt><b>STATUS_SUCCESS</b></dt>
</dl><p>The call succeeded. The returned NDIS entry points are valid for the specified chimney
       type.</p><dl>
<dt><b>STATUS_NOT_SUPPORTED</b></dt>
</dl><p>NDIS does not support the chimney type specified by the offload target. In this case, NDIS does
       not return a valid 
       <i>OffloadHandlers</i> pointer.</p>

<p> </p>

## -remarks
<p>The offload target calls this function from its 
    <a href="https://msdn.microsoft.com/b146fa81-005b-4a6c-962d-4cb023ea790e">MiniportInitializeEx</a> function to
    get the entry points of the NDIS functions for a particular chimney type. The offload target calls 
    <b>NdisMGetOffloadHandlers</b> once for each chimney type that it supports. In each call, the offload
    target specifies a different chimney type.</p>

<p>If the call to the 
    <b>NdisMGetOffloadHandlers</b> function succeeds, NDIS supplies a valid 
    <i>OffloadHandlers</i> pointer, which points to an NDIS_OFFLOAD_EVENT_HANDLERS structure. This structure
    contains an 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff566588">NDIS_OBJECT_HEADER</a> structure. The offload
    target examines the 
    <b>Type</b>, 
    <b>Revision</b>, and 
    <b>Size</b> members of the NDIS_OBJECT_HEADER structure. These members specify the structure that contains
    the chimney-specific entry points, the revision number of this structure, and the size of this structure
    in bytes. The 
    <b>Type</b> value is the same value that the offload target supplied for the 
    <i>ChimneyType</i> parameter.</p>

<p>If the offload target supports the specified 
    <b>Revision</b> number, it casts the 
    <i>OffloadHandlers</i> pointer to a pointer to the appropriate chimney-specific structure type. The
    following table indicates the chimney-specific structure for each chimney type.</p>

<p><b>NdisTcpChimneyOffload</b></p>

<p>
<a href="https://msdn.microsoft.com/72863a3e-9907-43e1-ad83-831a972ab823">
        NDIS_TCP_OFFLOAD_EVENT_HANDLERS</a>
</p>

<p> </p>

<p>For example, for the 
    <b>NdisTcpChimneyOffload</b> chimney type, the offload target casts the 
    <i>OffloadHandlers</i> pointer to *PNDIS_TCP_OFFLOAD_EVENT_HANDLERS.</p>

<p>The chimney-specific handlers structure contains the same NDIS_OBJECT_HEADER structure as the
    NDIS_OFFLOAD_EVENT_HANDLERS structure.</p>

<p>The offload target copies the entry points from the chimney-specific structure into its own internal
    data structure and then returns.</p>

<p>The offload target calls this function from its 
    <a href="https://msdn.microsoft.com/b146fa81-005b-4a6c-962d-4cb023ea790e">MiniportInitializeEx</a> function to
    get the entry points of the NDIS functions for a particular chimney type. The offload target calls 
    <b>NdisMGetOffloadHandlers</b> once for each chimney type that it supports. In each call, the offload
    target specifies a different chimney type.</p>

<p>If the call to the 
    <b>NdisMGetOffloadHandlers</b> function succeeds, NDIS supplies a valid 
    <i>OffloadHandlers</i> pointer, which points to an NDIS_OFFLOAD_EVENT_HANDLERS structure. This structure
    contains an 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff566588">NDIS_OBJECT_HEADER</a> structure. The offload
    target examines the 
    <b>Type</b>, 
    <b>Revision</b>, and 
    <b>Size</b> members of the NDIS_OBJECT_HEADER structure. These members specify the structure that contains
    the chimney-specific entry points, the revision number of this structure, and the size of this structure
    in bytes. The 
    <b>Type</b> value is the same value that the offload target supplied for the 
    <i>ChimneyType</i> parameter.</p>

<p>If the offload target supports the specified 
    <b>Revision</b> number, it casts the 
    <i>OffloadHandlers</i> pointer to a pointer to the appropriate chimney-specific structure type. The
    following table indicates the chimney-specific structure for each chimney type.</p>

<p><b>NdisTcpChimneyOffload</b></p>

<p>
<a href="https://msdn.microsoft.com/72863a3e-9907-43e1-ad83-831a972ab823">
        NDIS_TCP_OFFLOAD_EVENT_HANDLERS</a>
</p>

<p> </p>

<p>For example, for the 
    <b>NdisTcpChimneyOffload</b> chimney type, the offload target casts the 
    <i>OffloadHandlers</i> pointer to *PNDIS_TCP_OFFLOAD_EVENT_HANDLERS.</p>

<p>The chimney-specific handlers structure contains the same NDIS_OBJECT_HEADER structure as the
    NDIS_OFFLOAD_EVENT_HANDLERS structure.</p>

<p>The offload target copies the entry points from the chimney-specific structure into its own internal
    data structure and then returns.</p>

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
<dt>Ndischimney.h (include Ndischimney.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/b146fa81-005b-4a6c-962d-4cb023ea790e">MiniportInitializeEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563672">NdisMSetMiniportAttributes</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff566588">NDIS_OBJECT_HEADER</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/72863a3e-9907-43e1-ad83-831a972ab823">
   NDIS_TCP_OFFLOAD_EVENT_HANDLERS</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NdisMGetOffloadHandlers function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>