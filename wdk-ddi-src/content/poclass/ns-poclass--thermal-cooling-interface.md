---
UID: NS.poclass._THERMAL_COOLING_INTERFACE
title: THERMAL_COOLING_INTERFACE
author: windows-driver-content
description: The THERMAL_COOLING_INTERFACE structure enables the operating system to control the thermal management settings of a device.
old-location: kernel\thermal_cooling_interface.htm
ms.assetid: 1636CA34-7F5F-4690-B2AB-2882F0E91D74
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: kernel
req.header: poclass.h
req.include-header: Poclass.h
req.target-type: Windows
req.target-min-winverclnt: Supported starting with Windows 8.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: THERMAL_COOLING_INTERFACE
req.alt-loc: Poclass.h
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
ms.keywords: THERMAL_COOLING_INTERFACE, THERMAL_COOLING_INTERFACE, *PTHERMAL_COOLING_INTERFACE
req.iface: 
---

# THERMAL_COOLING_INTERFACE structure



## -description
<p>The <b>THERMAL_COOLING_INTERFACE</b> structure enables the operating system to control the thermal management settings of a device.</p>


## -syntax

````
typedef struct _THERMAL_COOLING_INTERFACE {
  USHORT                  Size;
  USHORT                  Version;
  PVOID                   Context;
  PINTERFACE_REFERENCE    InterfaceReference;
  PINTERFACE_DEREFERENCE  InterfaceDereference;
  ULONG                   Flags;
  PDEVICE_ACTIVE_COOLING  ActiveCooling;
  PDEVICE_PASSIVE_COOLING PassiveCooling;
} THERMAL_COOLING_INTERFACE, *PTHERMAL_COOLING_INTERFACE;
````


## -struct-fields
<dl>

### -field <b>Size</b>

<dd>
<p>The size, in bytes, of this structure. Set this member to <b>sizeof</b>(<b>THERMAL_COOLING_INTERFACE</b>).</p>
</dd>

### -field <b>Version</b>

<dd>
<p>The interface version number. The current version is specified by the THERMAL_COOLING_INTERFACE_VERSION constant in the Poclass.h header file. For more information, see Remarks.</p>
</dd>

### -field <b>Context</b>

<dd>
<p>A pointer to interface-specific context information. During a callback to any of the driver-implemented routines pointed to by this structure, the caller passes this context pointer to the routine as the first parameter value.</p>
</dd>

### -field <b>InterfaceReference</b>

<dd>
<p> A pointer to an <a href="https://msdn.microsoft.com/library/windows/hardware/ff547833">InterfaceReference</a> routine that increments the interface's reference count.</p>
</dd>

### -field <b>InterfaceDereference</b>

<dd>
<p>A pointer to an <a href="https://msdn.microsoft.com/library/windows/hardware/ff547829">InterfaceDereference</a> routine that decrements the interface's reference count.</p>
</dd>

### -field <b>Flags</b>

<dd>
<p>Reserved. Set to zero.</p>
</dd>

### -field <b>ActiveCooling</b>

<dd>
<p>A pointer to an <a href="https://msdn.microsoft.com/library/windows/hardware/hh698235">ActiveCooling</a> routine that engages or disengages active cooling (for example, by turning a fan on or off). A device that does not support active cooling sets this member to <b>NULL</b>.</p>
</dd>

### -field <b>PassiveCooling</b>

<dd>
<p>A pointer to an <a href="https://msdn.microsoft.com/library/windows/hardware/hh698270">PassiveCooling</a> routine that controls the degree to which the operation of the device must be throttled to reduce the heat generated by the device. A device that does not support passive cooling sets this member to <b>NULL</b>.</p>
</dd>
</dl>

## -remarks
<p>The <b>THERMAL_COOLING_INTERFACE</b> structure is an extension of the <a href="https://msdn.microsoft.com/library/windows/hardware/dn895657">INTERFACE</a> structure.</p>

<p>Starting with Windows 8, the operating system calls the routines pointed to by the <b>THERMAL_COOLING_INTERFACE</b> structure to control the thermal levels of the devices in a hardware platform. For more information, see <a href="https://msdn.microsoft.com/library/windows/hardware/hh698236">Device-Level Thermal Management</a>.</p>

<p>All implementations of the <a href="https://msdn.microsoft.com/library/windows/hardware/hh698265">GUID_THERMAL_COOLING_INTERFACE</a> driver interface must supply <i>InterfaceReference</i> and <i>InterfaceDereference</i> routines. In addition, an implementation must supply either an <i>ActiveCooling</i> routine or a <i>PassiveCooling</i> routine, and can supply both.</p>

<p>The driver for a device that provides an active cooling function (for example, a fan) implements an <i>ActiveCooling</i> routine. The operating system calls this routine to engage and disengage the active cooling function. Initially, before the first call to this routine, the device is configured so that the active cooling function is disengaged (turned off).</p>

<p>The driver for a device that provides a passive cooling function implements a <i>PassiveCooling</i> routine. The operating system calls this routine to control the degree to which the device is throttled. Throttling a device decreases its performance level to enable the device to cool. Initially, before the first call to this routine, the device is configured to operate at its full performance level, with no cooling restrictions.</p>

<p>For more information, see <a href="https://msdn.microsoft.com/library/windows/hardware/hh698271">Passive and Active Cooling Modes</a>.</p>

<p>When a device driver receives an <a href="https://msdn.microsoft.com/library/windows/hardware/ff551687">IRP_MN_QUERY_INTERFACE</a> request for the GUID_THERMAL_COOLING_INTERFACE driver interface, the input parameters for this request are contained in the <b>Parameters.QueryInterface</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff550659">IO_STACK_LOCATION</a> structure. The <b>Size</b> and <b>Version</b> input parameters specify which version of the interface is being requested. If the device driver that handles this request supports the specified version, this driver should set the <b>Size</b> and <b>Version</b> members of the <b>THERMAL_COOLING_INTERFACE</b> structure to the same values as the <b>Size</b> and <b>Version</b> input parameters. A device driver that does not support the specified interface version should complete the request with status code STATUS_NOT_SUPPORTED.</p>

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
<dt>Poclass.h (include Poclass.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh698235">ActiveCooling</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh698265">GUID_THERMAL_COOLING_INTERFACE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/dn895657">INTERFACE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547829">InterfaceDereference</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547833">InterfaceReference</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550659">IO_STACK_LOCATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551687">IRP_MN_QUERY_INTERFACE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh698270">PassiveCooling</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20THERMAL_COOLING_INTERFACE structure%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>