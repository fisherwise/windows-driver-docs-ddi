---
UID: NF.portcls.IPortClsPower.RegisterAdapterPowerManagement
title: IPortClsPower::RegisterAdapterPowerManagement
author: windows-driver-content
description: The RegisterAdapterPowerManagement method registers the power management interface of the adapter with PortCls.
old-location: audio\iportclspower_registeradapterpowermanagement.htm
ms.assetid: f4eb9d18-4352-47e2-bd5f-256e1fa831d3
ms.author: windowsdriverdev
ms.date: 10/30/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: audio
req.header: portcls.h
req.include-header: Portcls.h
req.target-type: Universal
req.target-min-winverclnt: Available in Windows 7 and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IPortClsPower.RegisterAdapterPowerManagement
req.alt-loc: portcls.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL.
ms.keywords: IPortClsPower, RegisterAdapterPowerManagement, IPortClsPower::RegisterAdapterPowerManagement
req.iface: IPortClsPower
---

# IPortClsPower::RegisterAdapterPowerManagement method



## -description
<p>The <code>RegisterAdapterPowerManagement</code> method registers the power management interface of the adapter with PortCls.</p>


## -syntax

````
NTSTATUS RegisterAdapterPowerManagement(
  [in] PUNKNOWN       pUnknown,
  [in] PDEVICE_OBJECT DeviceObject
);
````


## -parameters
<dl>

### -param <i>pUnknown</i> [in]

<dd>
<p>Specifies a pointer to <b>IUnknown</b>. . PortCls queries this <b>IUnknown</b> object for the <a href="https://msdn.microsoft.com/library/windows/hardware/ff536485">IAdapterPowerManagement</a> or the <a href="https://msdn.microsoft.com/library/windows/hardware/ff536486">IAdapterPowerManagement2</a> interface of the adapter.</p>
</dd>

### -param <i>DeviceObject</i> [in]

<dd>
<p>Specifies a pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff543147">DEVICE_OBJECT</a> structure that represents the functional device object of the adapter.</p>
</dd>
</dl>

## -returns
<p>The <code>RegisterAdapterPowerManagement</code> method returns STATUS_SUCCESS if the call is successful. Otherwise, it returns the appropriate error code.</p>

## -remarks
<p>When the <code>RegisterAdapterPowerManagement</code> method registers the power management interface for the adapter with PortCls, it allows the adapter driver to be notified of power state change events.</p>

<p>When the <code>RegisterAdapterPowerManagement</code> method registers the power management interface for the adapter with PortCls, it allows the adapter driver to be notified of power state change events.</p>

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
<dt>Portcls.h (include Portcls.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>PASSIVE_LEVEL.</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543147">DEVICE_OBJECT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536485">IAdapterPowerManagement</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536486">IAdapterPowerManagement2</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [audio\audio]:%20IPortClsPower::RegisterAdapterPowerManagement method%20 RELEASE:%20(10/30/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>