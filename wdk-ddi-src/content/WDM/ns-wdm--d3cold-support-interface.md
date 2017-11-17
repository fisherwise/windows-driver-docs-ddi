---
UID: NS.wdm._D3COLD_SUPPORT_INTERFACE
title: D3COLD_SUPPORT_INTERFACE
author: windows-driver-content
description: The D3COLD_SUPPORT_INTERFACE interface structure contains pointers to the routines in the GUID_D3COLD_SUPPORT_INTERFACE driver interface.
old-location: kernel\d3cold_support_interface.htm
ms.assetid: 5B681719-FBCC-417A-9FEB-ACB386FA3BE2
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: Wdm.h
req.target-type: Windows
req.target-min-winverclnt: Supported starting with Windows 8.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3COLD_SUPPORT_INTERFACE
req.alt-loc: Wdm.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL (see Remarks section)
ms.keywords: D3COLD_SUPPORT_INTERFACE, D3COLD_SUPPORT_INTERFACE, *PD3COLD_SUPPORT_INTERFACE
req.iface: 
req.product: Windows 10 or later.
---

# D3COLD_SUPPORT_INTERFACE structure



## -description
<p>The <b>D3COLD_SUPPORT_INTERFACE</b> interface structure contains pointers to the routines in the <a href="https://msdn.microsoft.com/library/windows/hardware/hh967714">GUID_D3COLD_SUPPORT_INTERFACE</a> driver interface.</p>


## -syntax

````
typedef struct _D3COLD_SUPPORT_INTERFACE {
  USHORT                             Size;
  USHORT                             Version;
  PVOID                              Context;
  PINTERFACE_REFERENCE               InterfaceReference;
  PINTERFACE_DEREFERENCE             InterfaceDereference;
  PSET_D3COLD_SUPPORT                SetD3ColdSupport;
  PGET_IDLE_WAKE_INFO                GetIdleWakeInfo;
  PGET_D3COLD_CAPABILITY             GetD3ColdCapability;
  PGET_D3COLD_CAPABILITY             GetBusDriverD3ColdSupport;
  PGET_D3COLD_LAST_TRANSITION_STATUS GetLastTransitionStatus;
} D3COLD_SUPPORT_INTERFACE, *PD3COLD_SUPPORT_INTERFACE;
````


## -struct-fields
<dl>

### -field <b>Size</b>

<dd>
<p>The size, in bytes, of this structure.</p>
</dd>

### -field <b>Version</b>

<dd>
<p>The driver-defined interface version. The current version of this interface is D3COLD_SUPPORT_INTERFACE_VERSION.</p>
</dd>

### -field <b>Context</b>

<dd>
<p>A pointer to interface-specific context information.</p>
</dd>

### -field <b>InterfaceReference</b>

<dd>
<p>A pointer to an <a href="https://msdn.microsoft.com/library/windows/hardware/ff547833">InterfaceReference</a> routine that increments the interface's reference count.</p>
</dd>

### -field <b>InterfaceDereference</b>

<dd>
<p>A pointer to an <a href="https://msdn.microsoft.com/library/windows/hardware/ff547829">InterfaceDereference</a> routine that decrements the interface's reference count.</p>
</dd>

### -field <b>SetD3ColdSupport</b>

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/hh967716">SetD3ColdSupport</a> routine that enables or disables transitions to the D3cold device power state.</p>
</dd>

### -field <b>GetIdleWakeInfo</b>

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/hh967712">GetIdleWakeInfo</a> routine that the device driver calls to discover the device power states from which this device can signal wake events to the processor.</p>
</dd>

### -field <b>GetD3ColdCapability</b>

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/hh967711">GetD3ColdCapability</a> routine that reports whether this device is capable of entering the D3cold device power state.</p>
</dd>

### -field <b>GetBusDriverD3ColdSupport</b>

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/hh967710">GetBusDriverD3ColdSupport</a> routine that reports whether the underlying bus driver and ACPI system firmware support D3cold for this device.</p>
</dd>

### -field <b>GetLastTransitionStatus</b>

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/hh967713">GetLastTransitionStatus</a> routine that reports whether this device's most recent transition to D3hot was followed by a transition to D3cold.</p>
</dd>
</dl>

## -remarks
<p>A device driver that successfully queries for the GUID_D3COLD_SUPPORT_INTERFACE interface receives a pointer to a <b>D3COLD_SUPPORT_INTERFACE</b> structure in which the pointers to the routines in the interface are all non-NULL and valid.</p>

<p>The <b>D3COLD_SUPPORT_INTERFACE</b> structure is an extended version of the <a href="https://msdn.microsoft.com/library/windows/hardware/dn895657">INTERFACE</a> structure.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Supported starting with Windows 8.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdm.h (include Wdm.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547833">InterfaceReference</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547829">InterfaceDereference</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh967716">SetD3ColdSupport</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh967712">GetIdleWakeInfo</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh967711">GetD3ColdCapability</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh967710">GetBusDriverD3ColdSupport</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh967713">GetLastTransitionStatus</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/dn895657">INTERFACE</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20D3COLD_SUPPORT_INTERFACE structure%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>