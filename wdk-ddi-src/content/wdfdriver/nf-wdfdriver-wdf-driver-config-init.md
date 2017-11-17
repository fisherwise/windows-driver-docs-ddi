---
UID: NF.wdfdriver.WDF_DRIVER_CONFIG_INIT
title: WDF_DRIVER_CONFIG_INIT
author: windows-driver-content
description: The WDF_DRIVER_CONFIG_INIT function initializes a driver's WDF_DRIVER_CONFIG structure.
old-location: wdf\wdf_driver_config_init.htm
ms.assetid: d7520300-9345-4681-a10d-acf34838199a
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: wdf
req.header: wdfdriver.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 2.0
req.alt-api: WDF_DRIVER_CONFIG_INIT
req.alt-loc: wdfdriver.h
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
ms.keywords: WDF_DRIVER_CONFIG_INIT
req.iface: 
req.product: Windows 10 or later.
---

# WDF_DRIVER_CONFIG_INIT function



## -description
<p class="CCE_Message">[Applies to KMDF and UMDF]</p>
<p>The WDF_DRIVER_CONFIG_INIT function initializes a driver's <a href="https://msdn.microsoft.com/library/windows/hardware/ff551300">WDF_DRIVER_CONFIG</a> structure.</p>


## -syntax

````
VOID WDF_DRIVER_CONFIG_INIT(
  _Out_    PWDF_DRIVER_CONFIG        Config,
  _In_opt_ PFN_WDF_DRIVER_DEVICE_ADD EvtDriverDeviceAdd
);
````


## -parameters
<dl>

### -param <i>Config</i> [out]

<dd>
<p>A pointer to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff551300">WDF_DRIVER_CONFIG</a> structure that the function will initialize.</p>
</dd>

### -param <i>EvtDriverDeviceAdd</i> [in, optional]

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/b20db029-ee2c-4fb1-bd69-ccd2e37fdc9a">EvtDriverDeviceAdd</a> callback function.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>The WDF_DRIVER_CONFIG_INIT function is available in version 1.0 and later versions of KMDF.</p>

<p>For a code example that uses WDF_DRIVER_CONFIG_INIT, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff547175">WdfDriverCreate</a>.</p>

<p>The WDF_DRIVER_CONFIG_INIT function is available in version 1.0 and later versions of KMDF.</p>

<p>For a code example that uses WDF_DRIVER_CONFIG_INIT, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff547175">WdfDriverCreate</a>.</p>

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
<p>Minimum KMDF version</p>
</th>
<td width="70%">
<p>1.0</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum UMDF version</p>
</th>
<td width="70%">
<p>2.0</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdfdriver.h (include Wdf.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/b20db029-ee2c-4fb1-bd69-ccd2e37fdc9a">EvtDriverDeviceAdd</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551300">WDF_DRIVER_CONFIG</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547175">WdfDriverCreate</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WDF_DRIVER_CONFIG_INIT function%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>