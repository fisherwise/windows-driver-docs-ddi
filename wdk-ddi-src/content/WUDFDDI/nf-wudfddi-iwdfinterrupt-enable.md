---
UID: NF.wudfddi.IWDFInterrupt.Enable
title: IWDFInterrupt::Enable
author: windows-driver-content
description: The Enable method enables a specified device interrupt by calling the driver's OnInterruptEnable callback function.
old-location: wdf\iwdfinterrupt_enable.htm
ms.assetid: 605C58C2-9A4F-4185-BB5C-95C9F5180C05
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: wdf
req.header: wudfddi.h
req.include-header: 
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 1.11
req.alt-api: IWDFInterrupt.Enable
req.alt-loc: WUDFx.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: Unavailable in UMDF 2.0 and later.
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: WUDFx.dll
req.irql: <= DISPATCH_LEVEL
ms.keywords: IWDFInterrupt, Enable, IWDFInterrupt::Enable
req.iface: IWDFInterrupt
req.product: Windows 10 or later.
---

# IWDFInterrupt::Enable method



## -description
<p class="CCE_Message">[<b>Warning:</b> UMDF 2 is the latest version of UMDF and supersedes UMDF 1.  All new UMDF drivers should be written using UMDF 2.  No new features are being added to UMDF 1 and there is limited support for UMDF 1 on newer versions of Windows 10.  Universal Windows drivers must use UMDF 2.  For more info, see <a href="https://docs.microsoft.com/en-us/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2">Getting Started with UMDF</a>.]</p>
<p>The <b>Enable</b> method enables a specified device interrupt by calling the driver's <a href="https://msdn.microsoft.com/6C091427-59FF-4101-ACD6-353C959794F6">OnInterruptEnable</a> callback function.</p>


## -syntax

````
void Enable();
````


## -parameters


## -returns
<p>This method does not return a value.</p>

<p>This method does not return a value.</p>

<p>This method does not return a value.</p>

## -remarks
<p>Most UMDF drivers do not need to call <b>IWDFInterrupt::Enable</b>, because the framework calls the driver's <a href="https://msdn.microsoft.com/6C091427-59FF-4101-ACD6-353C959794F6">OnInterruptEnable</a> callback function each time the device enters its working (D0) state.

</p>

<p>For more information about handling interrupts in UMDF drivers, see <a href="wdf.accessing_hardware_and_handling_interrupts">Accessing Hardware and Handling Interrupts</a>.</p>

<p>The following code example enables the device interrupt that is associated with a specified interrupt object.</p>

<p>Most UMDF drivers do not need to call <b>IWDFInterrupt::Enable</b>, because the framework calls the driver's <a href="https://msdn.microsoft.com/6C091427-59FF-4101-ACD6-353C959794F6">OnInterruptEnable</a> callback function each time the device enters its working (D0) state.

</p>

<p>For more information about handling interrupts in UMDF drivers, see <a href="wdf.accessing_hardware_and_handling_interrupts">Accessing Hardware and Handling Interrupts</a>.</p>

<p>The following code example enables the device interrupt that is associated with a specified interrupt object.</p>

<p>Most UMDF drivers do not need to call <b>IWDFInterrupt::Enable</b>, because the framework calls the driver's <a href="https://msdn.microsoft.com/6C091427-59FF-4101-ACD6-353C959794F6">OnInterruptEnable</a> callback function each time the device enters its working (D0) state.

</p>

<p>For more information about handling interrupts in UMDF drivers, see <a href="wdf.accessing_hardware_and_handling_interrupts">Accessing Hardware and Handling Interrupts</a>.</p>

<p>The following code example enables the device interrupt that is associated with a specified interrupt object.</p>

<p>Most UMDF drivers do not need to call <b>IWDFInterrupt::Enable</b>, because the framework calls the driver's <a href="https://msdn.microsoft.com/6C091427-59FF-4101-ACD6-353C959794F6">OnInterruptEnable</a> callback function each time the device enters its working (D0) state.

</p>

<p>For more information about handling interrupts in UMDF drivers, see <a href="wdf.accessing_hardware_and_handling_interrupts">Accessing Hardware and Handling Interrupts</a>.</p>

<p>The following code example enables the device interrupt that is associated with a specified interrupt object.</p>

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
<p>End of support</p>
</th>
<td width="70%">
<p>Unavailable in UMDF 2.0 and later.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum UMDF version</p>
</th>
<td width="70%">
<p>1.11</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wudfddi.h</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>WUDFx.dll</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh451283">IWDFInterrupt</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/D87C868D-9538-4752-AEBD-2A15E53628CF">IWDFInterrupt::Disable</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20IWDFInterrupt::Enable method%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>