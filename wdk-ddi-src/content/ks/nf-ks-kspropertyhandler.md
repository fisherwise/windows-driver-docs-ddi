---
UID: NF.ks.KsPropertyHandler
title: KsPropertyHandler
author: windows-driver-content
description: Drivers call KsPropertyHandler function for IRP handling.
old-location: stream\kspropertyhandler.htm
ms.assetid: af94f36f-6e1a-4ac5-be6d-64a9a8dade9e
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
req.alt-api: KsPropertyHandler
req.alt-loc: Ks.lib,Ks.dll
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
ms.keywords: KsPropertyHandler
req.iface: 
---

# KsPropertyHandler function



## -description
<p>Drivers call <b>KsPropertyHandler</b> function for IRP handling.</p>


## -syntax

````
NTSTATUS KsPropertyHandler(
  _In_       PIRP           Irp,
  _In_       ULONG          PropertySetsCount,
  _In_ const KSPROPERTY_SET *PropertySet
);
````


## -parameters
<dl>

### -param <i>Irp</i> [in]

<dd>
<p>Specifies the IRP with the property request being handled.</p>
</dd>

### -param <i>PropertySetsCount</i> [in]

<dd>
<p>Specifies the number of property sets being passed.</p>
</dd>

### -param <i>PropertySet</i> [in]

<dd>
<p>Points to an array of <a href="https://msdn.microsoft.com/library/windows/hardware/ff565617">KSPROPERTY_SET</a> structures. The driver should provide one structure for each property set it wants KsPropertyHandler to handle.</p>
</dd>
</dl>

## -returns
<p>The <b>KsPropertyHandler </b>function returns STATUS_SUCCESS if successful, or an error specific to the property being handled if unsuccessful. The function sets the <a href="https://msdn.microsoft.com/library/windows/hardware/ff550694">IRP</a>-&gt;<a href="https://msdn.microsoft.com/library/windows/hardware/ff550671">IO_STATUS_BLOCK</a>.Information member, either through setting it to zero because of an internal error, or through a property handler setting it. The function does not set the lrp-&gt;IoStatus.Status member nor does it complete the IRP.</p>

## -remarks
<p><b>KsPropertyHandler</b> responds to all property identifiers defined by the sets, and can only be called at PASSIVE_LEVEL.</p>

<p>Each <a href="https://msdn.microsoft.com/library/windows/hardware/ff565617">KSPROPERTY_SET</a> entry contains a pointer to an array of <a href="https://msdn.microsoft.com/library/windows/hardware/ff565176">KSPROPERTY_ITEM</a> structures in its PropertyItem member. For driver-specific processing, KsPropertyHandler hands off each request to one of the driver-supplied callbacks within PropertyItem. KsPropertyHandler takes care of any IRP processing required.</p>

<p>KsPropertyHandler does not use the FastIoTable member of its <a href="https://msdn.microsoft.com/library/windows/hardware/ff565617">KSPROPERTY_SET</a> structure. If the driver needs to support Fast I/O handling of requests, the same KSPROPERTY_SET structure should be passed to the KsFastPropertyHandler routine.</p>

<p>The owner of the property sets can perform prefiltering or postfiltering of property handling. Basic property structure access exceptions are handled by the <b>KsPropertyHandler </b>function, though cleanup for specific exceptions must be covered by the property handler.</p>

<p><b>KsPropertyHandler</b> places a pointer to the relevant KSPROPERTY_SET structure in the <b>Irp-&gt;Tail.Overlay.DriverContext</b> parameter in the IRP. The minidriver can use the KSPROPERTY_SET_IRP_STORAGE macro, defined in <i>ks.h</i>, to access this pointer.</p>

<p><b>KsPropertyHandler</b> responds to all property identifiers defined by the sets, and can only be called at PASSIVE_LEVEL.</p>

<p>Each <a href="https://msdn.microsoft.com/library/windows/hardware/ff565617">KSPROPERTY_SET</a> entry contains a pointer to an array of <a href="https://msdn.microsoft.com/library/windows/hardware/ff565176">KSPROPERTY_ITEM</a> structures in its PropertyItem member. For driver-specific processing, KsPropertyHandler hands off each request to one of the driver-supplied callbacks within PropertyItem. KsPropertyHandler takes care of any IRP processing required.</p>

<p>KsPropertyHandler does not use the FastIoTable member of its <a href="https://msdn.microsoft.com/library/windows/hardware/ff565617">KSPROPERTY_SET</a> structure. If the driver needs to support Fast I/O handling of requests, the same KSPROPERTY_SET structure should be passed to the KsFastPropertyHandler routine.</p>

<p>The owner of the property sets can perform prefiltering or postfiltering of property handling. Basic property structure access exceptions are handled by the <b>KsPropertyHandler </b>function, though cleanup for specific exceptions must be covered by the property handler.</p>

<p><b>KsPropertyHandler</b> places a pointer to the relevant KSPROPERTY_SET structure in the <b>Irp-&gt;Tail.Overlay.DriverContext</b> parameter in the IRP. The minidriver can use the KSPROPERTY_SET_IRP_STORAGE macro, defined in <i>ks.h</i>, to access this pointer.</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff561946">KsFastPropertyHandler</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564264">KsPropertyHandlerWithAllocator</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [stream\stream]:%20KsPropertyHandler function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>