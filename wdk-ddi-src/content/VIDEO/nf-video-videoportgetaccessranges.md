---
UID: NF.video.VideoPortGetAccessRanges
title: VideoPortGetAccessRanges
author: windows-driver-content
description: The VideoPortGetAccessRanges function retrieves bus-relative configuration information and, if possible, claims these hardware resources in the registry for the caller.
old-location: display\videoportgetaccessranges.htm
ms.assetid: 7a858b32-408e-4926-9aba-44046b0266e2
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: display
req.header: video.h
req.include-header: Video.h
req.target-type: Desktop
req.target-min-winverclnt: Available in Windows 2000 and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: VideoPortGetAccessRanges
req.alt-loc: Videoprt.sys
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Videoprt.lib
req.dll: Videoprt.sys
req.irql: PASSIVE_LEVEL
ms.keywords: VideoPortGetAccessRanges
req.iface: 
req.product: Windows 10 or later.
---

# VideoPortGetAccessRanges function



## -description
<p>The <b>VideoPortGetAccessRanges</b> function retrieves bus-relative configuration information and, if possible, claims these hardware resources in the registry for the caller.</p>


## -syntax

````
VP_STATUS VideoPortGetAccessRanges(
           PVOID                   HwDeviceExtension,
           ULONG                   NumRequestedResources,
  _In_opt_ PIO_RESOURCE_DESCRIPTOR RequestedResources,
           ULONG                   NumAccessRanges,
  _Out_    PVIDEO_ACCESS_RANGE     AccessRanges,
           PVOID                   VendorId,
           PVOID                   DeviceId,
           PULONG                  Slot
);
````


## -parameters
<dl>

### -param <i>HwDeviceExtension</i> 

<dd>
<p>Pointer to the miniport driver's device extension.</p>
</dd>

### -param <i>NumRequestedResources</i> 

<dd>
<p>Specifies the number of elements in the <i>RequestedResources</i> array.</p>
</dd>

### -param <i>RequestedResources</i> [in, optional]

<dd>
<p>An array of IO_RESOURCE_DESCRIPTOR-type elements. Each descriptor specifies a single hardware resource that the miniport driver needs, prefers, or can use as an alternative to that specified in another array element. For detailed information about this structure, see the description of <a href="https://msdn.microsoft.com/library/windows/hardware/ff548285">IoAssignResources</a>.</p>
</dd>

### -param <i>NumAccessRanges</i> 

<dd>
<p>Specifies the number of elements in the <i>AccessRanges</i> array.</p>
</dd>

### -param <i>AccessRanges</i> [out]

<dd>
<p>Pointer to an area on the stack or to a static structure in the miniport driver to which <b>VideoPortGetAccessRanges</b> returns an array of <a href="https://msdn.microsoft.com/library/windows/hardware/ff570498">VIDEO_ACCESS_RANGE</a> elements filled with the bus-relative device memory ranges for the adapter.</p>
</dd>

### -param <i>VendorId</i> 

<dd>
<p>Should be set to <b>NULL</b>.</p>
</dd>

### -param <i>DeviceId</i> 

<dd>
<p>Should be set to <b>NULL</b>.</p>
</dd>

### -param <i>Slot</i> 

<dd>
<p>Pointer to a memory location in which the video port driver stores the slot number for the device, or is <b>NULL</b>. </p>
<p>For Plug and Play devices, if this is a valid pointer, the video port driver stores the slot number at the memory location specified by the pointer. If a <b>NULL</b> value is passed in the call, the video port driver does not store a value in the location.</p>
</dd>
</dl>

## -returns
<p><b>VideoPortGetAccessRanges</b> returns NO_ERROR if it successfully filled in the <i>AccessRanges</i> information or returned configuration information at <i>RequestedResources</i>.</p>

## -remarks
<p>Every video miniport driver either must use access ranges returned by <b>VideoPortGetAccessRanges</b>, or must call <a href="https://msdn.microsoft.com/library/windows/hardware/ff570377">VideoPortVerifyAccessRanges</a> before attempting to access a video adapter during the driver (and system) initialization process.</p>

<p><b>VideoPortGetAccessRanges</b> can be called only from a miniport driver's <a href="https://msdn.microsoft.com/8c880eff-4b4c-439e-9239-f2343c1fe084">HwVidFindAdapter</a> function.</p>

<p>For most miniport drivers, <b>VideoPortGetAccessRanges</b> can retrieve, verify, and claim the bus-relative access ranges and any interrupt and/or DMA channel/port used by a particular video adapter, while <a href="https://msdn.microsoft.com/library/windows/hardware/ff570377">VideoPortVerifyAccessRanges</a> can only verify and claim miniport driver-specified resources. That is, for all configuration information that it returns, <b>VideoPortGetAccessRanges</b> claims the corresponding hardware resources in the registry for the caller. A miniport driver need not call <b>VideoPortVerifyAccessRanges</b> with the returned bus-relative configuration information, unless the miniport driver attempts to modify any of the returned values.</p>

<p>Each successful call to <b>VideoPortGetAccessRanges</b> or <b>VideoPortVerifyAccessRanges</b> for a particular adapter overwrites the miniport driver's preceding claim on hardware resources in the registry.</p>

<p>After a successful call to <b>VideoPortGetAccessRanges</b>, the miniport driver must map the returned bus-relative ranges to logical ranges with <a href="https://msdn.microsoft.com/53665c1d-8c0b-45c7-8d23-13c0964eda39">VideoPortGetDeviceBase </a><i>before</i> calling the appropriate <b>VideoPortRead/Write</b><i>Xxx</i> function to communicate with the adapter.</p>

<p>Generally, the miniport driver of a PCI device should have its <a href="https://msdn.microsoft.com/8c880eff-4b4c-439e-9239-f2343c1fe084">HwVidFindAdapter</a> function call <b>VideoPortGetAccessRanges</b>, rather than attempt to manipulate the nondevice-specific PCI_COMMON_CONFIG information returned by a call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff570306">VideoPortGetBusData</a>. This miniport driver can typically call <b>VideoPortGetAccessRanges</b> with a <b>NULL</b><i>RequestedResources</i> pointer. The video port driver then uses the configuration space of the PCI bus to determine the resources for the video adapter. The miniport driver can call <b>VideoPortGetAccessRanges</b>, using a set of driver-supplied <i>RequestedResources</i> specifications, if its original call fails to return valid configuration data for the adapter.</p>

<p>Note that miniport drivers of adapters on other types of I/O buses also can call <b>VideoPortGetAccessRanges</b>. These drivers should call <b>VideoPortGetAccessRanges</b> using a <i>RequestedResources</i> pointer to a driver-supplied array of I/O resource descriptors.</p>

<p>If the <i>HwVidFindAdapter</i> function claims bus-relative access ranges and possibly other hardware resources for an adapter, but then determines that it does not support the adapter, then the miniport driver must relinquish its claims on hardware resources in the registry by calling <b>VideoPortGetAccessRanges</b> or <b>VideoPortVerifyAccessRanges</b> with the <i>NumAccessRanges</i> parameter set to zero.</p>

<p>Every video miniport driver either must use access ranges returned by <b>VideoPortGetAccessRanges</b>, or must call <a href="https://msdn.microsoft.com/library/windows/hardware/ff570377">VideoPortVerifyAccessRanges</a> before attempting to access a video adapter during the driver (and system) initialization process.</p>

<p><b>VideoPortGetAccessRanges</b> can be called only from a miniport driver's <a href="https://msdn.microsoft.com/8c880eff-4b4c-439e-9239-f2343c1fe084">HwVidFindAdapter</a> function.</p>

<p>For most miniport drivers, <b>VideoPortGetAccessRanges</b> can retrieve, verify, and claim the bus-relative access ranges and any interrupt and/or DMA channel/port used by a particular video adapter, while <a href="https://msdn.microsoft.com/library/windows/hardware/ff570377">VideoPortVerifyAccessRanges</a> can only verify and claim miniport driver-specified resources. That is, for all configuration information that it returns, <b>VideoPortGetAccessRanges</b> claims the corresponding hardware resources in the registry for the caller. A miniport driver need not call <b>VideoPortVerifyAccessRanges</b> with the returned bus-relative configuration information, unless the miniport driver attempts to modify any of the returned values.</p>

<p>Each successful call to <b>VideoPortGetAccessRanges</b> or <b>VideoPortVerifyAccessRanges</b> for a particular adapter overwrites the miniport driver's preceding claim on hardware resources in the registry.</p>

<p>After a successful call to <b>VideoPortGetAccessRanges</b>, the miniport driver must map the returned bus-relative ranges to logical ranges with <a href="https://msdn.microsoft.com/53665c1d-8c0b-45c7-8d23-13c0964eda39">VideoPortGetDeviceBase </a><i>before</i> calling the appropriate <b>VideoPortRead/Write</b><i>Xxx</i> function to communicate with the adapter.</p>

<p>Generally, the miniport driver of a PCI device should have its <a href="https://msdn.microsoft.com/8c880eff-4b4c-439e-9239-f2343c1fe084">HwVidFindAdapter</a> function call <b>VideoPortGetAccessRanges</b>, rather than attempt to manipulate the nondevice-specific PCI_COMMON_CONFIG information returned by a call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff570306">VideoPortGetBusData</a>. This miniport driver can typically call <b>VideoPortGetAccessRanges</b> with a <b>NULL</b><i>RequestedResources</i> pointer. The video port driver then uses the configuration space of the PCI bus to determine the resources for the video adapter. The miniport driver can call <b>VideoPortGetAccessRanges</b>, using a set of driver-supplied <i>RequestedResources</i> specifications, if its original call fails to return valid configuration data for the adapter.</p>

<p>Note that miniport drivers of adapters on other types of I/O buses also can call <b>VideoPortGetAccessRanges</b>. These drivers should call <b>VideoPortGetAccessRanges</b> using a <i>RequestedResources</i> pointer to a driver-supplied array of I/O resource descriptors.</p>

<p>If the <i>HwVidFindAdapter</i> function claims bus-relative access ranges and possibly other hardware resources for an adapter, but then determines that it does not support the adapter, then the miniport driver must relinquish its claims on hardware resources in the registry by calling <b>VideoPortGetAccessRanges</b> or <b>VideoPortVerifyAccessRanges</b> with the <i>NumAccessRanges</i> parameter set to zero.</p>

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
<p>Available in Windows 2000 and later versions of the Windows operating systems.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Video.h (include Video.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Videoprt.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>Videoprt.sys</dt>
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
<a href="https://msdn.microsoft.com/8c880eff-4b4c-439e-9239-f2343c1fe084">HwVidFindAdapter</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548285">IoAssignResources</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff537455">PCI_COMMON_CONFIG</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff558790">PCI_SLOT_NUMBER</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff570531">VIDEO_PORT_CONFIG_INFO</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff570306">VideoPortGetBusData</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff570310">VideoPortGetDeviceBase</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff570361">VideoPortSetBusData</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff570377">VideoPortVerifyAccessRanges</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20VideoPortGetAccessRanges function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>