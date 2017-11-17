---
UID: NC.video.PMINIPORT_GET_REGISTRY_ROUTINE
title: PMINIPORT_GET_REGISTRY_ROUTINE
author: windows-driver-content
description: HwVidQueryNamedValueCallback processes the specified data retrieved from the registry.
old-location: display\hwvidquerynamedvaluecallback.htm
ms.assetid: 90020700-b9c8-42e6-bafa-908cbc3eb233
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: display
req.header: video.h
req.include-header: Video.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: HwVidQueryNamedValueCallback
req.alt-loc: video.h
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
ms.keywords: VHF_CONFIG, VHF_CONFIG, *PVHF_CONFIG
req.iface: 
req.product: Windows 10 or later.
---

# PMINIPORT_GET_REGISTRY_ROUTINE callback



## -description
<p><i>HwVidQueryNamedValueCallback</i> processes the specified data retrieved from the registry.</p>


## -prototype

````
PMINIPORT_GET_REGISTRY_ROUTINE HwVidQueryNamedValueCallback;

VP_STATUS HwVidQueryNamedValueCallback(
   PVOID HwDeviceExtension,
   PVOID Context,
   PWSTR ValueName,
   PVOID ValueData,
   ULONG ValueLength
)
{ ... }
````


## -parameters
<dl>

### -param <i>HwDeviceExtension</i> 

<dd>
<p>Pointer to the miniport driver's per-adapter storage area. For more information, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff543119">Device Extensions</a>.</p>
</dd>

### -param <i>Context</i> 

<dd>
<p>Pointer to a driver-determined context specified as input to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff570316">VideoPortGetRegistryParameters</a> function.</p>
</dd>

### -param <i>ValueName</i> 

<dd>
<p>Pointer to a NULL-terminated Unicode string naming the entry.</p>
</dd>

### -param <i>ValueData</i> 

<dd>
<p>Pointer to the buffered data associated with <i>ValueName</i>, supplied by <b>VideoPortGetRegistryParameters</b>.</p>
</dd>

### -param <i>ValueLength</i> 

<dd>
<p>Specifies the size in bytes of the buffer at <i>ValueData</i>.</p>
</dd>
</dl>

## -returns
<p><i>HwVidQueryNamedValueCallback</i> returns the status of the operation.</p>

## -remarks
<p><i>HwVidQueryNamedValueCallback</i> is an optional miniport driver function passed in a call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff570316">VideoPortGetRegistryParameters</a>.</p>

<p><b>VideoPortGetRegistryParameters</b> calls <i>HwVidQueryNamedValueCallback</i> after collecting available configuration information about the given <i>ValueName</i> in the <b>adapter</b> key of the registry. </p>

<p><i>HwVidFindAdapter</i> or <a href="https://msdn.microsoft.com/0e43de21-59e5-4368-8ea2-34fa52e99950">HwVidInitialize</a> can call <b>VideoPortGetRegistryParameters</b> with a driver-supplied <i>HwVidQueryNamedValueCallback</i> function, pointers to the device extension and any driver-supplied context data (which can be the <a href="https://msdn.microsoft.com/library/windows/hardware/ff570531">VIDEO_PORT_CONFIG_INFO</a> buffer), and a pointer to a Unicode string naming the value to be retrieved from the registry.</p>

<p><i>HwVidFindAdapter</i> or <i>HwVidInitialize</i> can set <b>VideoPortGetRegistryParameters</b>'s <i>IsFileNameParameter</i> argument to <b>TRUE</b> if the driver-supplied Unicode string is a named registry entry whose value is a file name. For this specification, the returned data will be the contents of the named file.</p>

<p>When <b>VideoPortGetRegistryParameters</b> calls the <i>HwVidQueryNamedValueCallback</i> function, it processes whatever configuration data is made available. For example, <i>HwVidQueryNamedValueCallback</i> might use retrieved data to determine the miniport driver's access ranges and to set up its emulator access ranges (if any), interrupt vector or interrupt IRQL (if any), and so forth in the VIDEO_PORT_CONFIG_INFO buffer, as well as in the miniport driver's device extension, before returning control to the <i>HwVidFindAdapter</i> function.</p>

<p><i>HwVidInitialize</i> might also call <b>VideoPortGetRegistryParameters</b> with <i>IsFileNameParameter</i> set to <b>TRUE</b> so that the miniport driver-supplied <i>HwVidQueryNamedValueCallback</i> function could use the buffered contents of a named file to set up microcode on the adapter.</p>

<p>The returned <i>ValueData</i> is on the stack, so it can be referenced locally. <i>HwVidQueryNamedValueCallback</i> can store some or all of the returned information for use by other miniport driver functions in the input <i>HwDeviceExtension</i> or use the input <i>Context</i> as a pointer to a location where the data can be stored.</p>

<p><i>HwVidQueryNamedValueCallback</i> should be made pageable.</p>

<p><i>HwVidQueryNamedValueCallback</i> is an optional miniport driver function passed in a call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff570316">VideoPortGetRegistryParameters</a>.</p>

<p><b>VideoPortGetRegistryParameters</b> calls <i>HwVidQueryNamedValueCallback</i> after collecting available configuration information about the given <i>ValueName</i> in the <b>adapter</b> key of the registry. </p>

<p><i>HwVidFindAdapter</i> or <a href="https://msdn.microsoft.com/0e43de21-59e5-4368-8ea2-34fa52e99950">HwVidInitialize</a> can call <b>VideoPortGetRegistryParameters</b> with a driver-supplied <i>HwVidQueryNamedValueCallback</i> function, pointers to the device extension and any driver-supplied context data (which can be the <a href="https://msdn.microsoft.com/library/windows/hardware/ff570531">VIDEO_PORT_CONFIG_INFO</a> buffer), and a pointer to a Unicode string naming the value to be retrieved from the registry.</p>

<p><i>HwVidFindAdapter</i> or <i>HwVidInitialize</i> can set <b>VideoPortGetRegistryParameters</b>'s <i>IsFileNameParameter</i> argument to <b>TRUE</b> if the driver-supplied Unicode string is a named registry entry whose value is a file name. For this specification, the returned data will be the contents of the named file.</p>

<p>When <b>VideoPortGetRegistryParameters</b> calls the <i>HwVidQueryNamedValueCallback</i> function, it processes whatever configuration data is made available. For example, <i>HwVidQueryNamedValueCallback</i> might use retrieved data to determine the miniport driver's access ranges and to set up its emulator access ranges (if any), interrupt vector or interrupt IRQL (if any), and so forth in the VIDEO_PORT_CONFIG_INFO buffer, as well as in the miniport driver's device extension, before returning control to the <i>HwVidFindAdapter</i> function.</p>

<p><i>HwVidInitialize</i> might also call <b>VideoPortGetRegistryParameters</b> with <i>IsFileNameParameter</i> set to <b>TRUE</b> so that the miniport driver-supplied <i>HwVidQueryNamedValueCallback</i> function could use the buffered contents of a named file to set up microcode on the adapter.</p>

<p>The returned <i>ValueData</i> is on the stack, so it can be referenced locally. <i>HwVidQueryNamedValueCallback</i> can store some or all of the returned information for use by other miniport driver functions in the input <i>HwDeviceExtension</i> or use the input <i>Context</i> as a pointer to a location where the data can be stored.</p>

<p><i>HwVidQueryNamedValueCallback</i> should be made pageable.</p>

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
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Video.h (include Video.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/8c880eff-4b4c-439e-9239-f2343c1fe084">HwVidFindAdapter</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/0e43de21-59e5-4368-8ea2-34fa52e99950">HwVidInitialize</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff570531">VIDEO_PORT_CONFIG_INFO</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff570316">VideoPortGetRegistryParameters</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff570365">VideoPortSetRegistryParameters</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20PMINIPORT_GET_REGISTRY_ROUTINE callback function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>