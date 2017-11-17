---
UID: NF.ks.KsFilterFactoryGetOuterUnknown
title: KsFilterFactoryGetOuterUnknown
author: windows-driver-content
description: The KsFilterFactoryGetOuterUnknown function returns the outer IUnknown of the specified filter factory.
old-location: stream\ksfilterfactorygetouterunknown.htm
ms.assetid: 65244091-6089-4d0c-abf4-1178cf0bf1b5
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: stream
req.header: ks.h
req.include-header: Ks.h
req.target-type: Desktop
req.target-min-winverclnt: Available in Microsoft Windows XP and later operating systems and DirectX 8.0 and later DirectX versions.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: KsFilterFactoryGetOuterUnknown
req.alt-loc: ks.h
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
ms.keywords: KsFilterFactoryGetOuterUnknown
req.iface: 
---

# KsFilterFactoryGetOuterUnknown function



## -description
<p>The<b> KsFilterFactoryGetOuterUnknown </b>function returns the outer <b>IUnknown</b> of the specified filter factory.</p>


## -syntax

````
PUNKNOWN __inline KsFilterFactoryGetOuterUnknown(
  _In_ PKSFILTERFACTORY FilterFactory
);
````


## -parameters
<dl>

### -param <i>FilterFactory</i> [in]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff562530">KSFILTERFACTORY</a> for which to return the outer unknown interface.</p>
</dd>
</dl>

## -returns
<p><b>KsFilterFactoryGetOuterUnknown </b>returns the outer <b>IUnknown</b> of <i>FilterFactory</i>. The minidriver can then use it to query for other interfaces.</p>

## -remarks
<p>This call is an inline function call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff562655">KsGetOuterUnknown</a>.</p>

<p>For more information, see <a href="NULL">AVStream Overview</a>
</p>

<p>This call is an inline function call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff562655">KsGetOuterUnknown</a>.</p>

<p>For more information, see <a href="NULL">AVStream Overview</a>
</p>

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
<p>Available in Microsoft Windows XP and later operating systems and DirectX 8.0 and later DirectX versions.</p>
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
<p>IRQL</p>
</th>
<td width="70%">
<p>PASSIVE_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562655">KsGetOuterUnknown</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff566767">KsRegisterAggregatedClientUnknown</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562549">KsFilterRegisterAggregatedClientUnknown</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562547">KsFilterGetOuterUnknown</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563515">KsPinGetOuterUnknown</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff559766">IKsControl</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [stream\stream]:%20KsFilterFactoryGetOuterUnknown function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>