---
UID: NF.wudfddi.IWDFDevice2.GetSystemPowerAction
title: IWDFDevice2::GetSystemPowerAction
author: windows-driver-content
description: The GetSystemPowerAction method returns the system power action, if any, that is currently occurring for the computer.
old-location: wdf\iwdfdevice2_getsystempoweraction.htm
ms.assetid: 0030d64b-3f88-4bb3-b7d2-fcdc57d4d887
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: wdf
req.header: wudfddi.h
req.include-header: Wudfddi.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 1.9
req.alt-api: IWDFDevice2.GetSystemPowerAction
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
ms.keywords: IWDFDevice2, GetSystemPowerAction, IWDFDevice2::GetSystemPowerAction
req.iface: IWDFDevice2
req.product: Windows 10 or later.
---

# IWDFDevice2::GetSystemPowerAction method



## -description
<p class="CCE_Message">[<b>Warning:</b> UMDF 2 is the latest version of UMDF and supersedes UMDF 1.  All new UMDF drivers should be written using UMDF 2.  No new features are being added to UMDF 1 and there is limited support for UMDF 1 on newer versions of Windows 10.  Universal Windows drivers must use UMDF 2.  For more info, see <a href="https://docs.microsoft.com/en-us/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2">Getting Started with UMDF</a>.]</p>
<p>The <b>GetSystemPowerAction</b> method returns the <a href="https://msdn.microsoft.com/e8ab99d4-c18d-4ba8-bfe8-8eebb881c384">system power action</a>, if any, that is currently occurring for the computer. </p>


## -syntax

````
POWER_ACTION GetSystemPowerAction();
````


## -parameters


## -returns
<p><b>GetSystemPowerAction</b> returns a <a href="https://msdn.microsoft.com/library/windows/hardware/ff560459">POWER_ACTION</a>-typed enumerator value. The value indicates the <a href="https://msdn.microsoft.com/e8ab99d4-c18d-4ba8-bfe8-8eebb881c384">system power action</a> that is currently occurring for the computer. For more information, see the following Remarks section. </p>

<p><b>GetSystemPowerAction</b> returns a <a href="https://msdn.microsoft.com/library/windows/hardware/ff560459">POWER_ACTION</a>-typed enumerator value. The value indicates the <a href="https://msdn.microsoft.com/e8ab99d4-c18d-4ba8-bfe8-8eebb881c384">system power action</a> that is currently occurring for the computer. For more information, see the following Remarks section. </p>

<p><b>GetSystemPowerAction</b> returns a <a href="https://msdn.microsoft.com/library/windows/hardware/ff560459">POWER_ACTION</a>-typed enumerator value. The value indicates the <a href="https://msdn.microsoft.com/e8ab99d4-c18d-4ba8-bfe8-8eebb881c384">system power action</a> that is currently occurring for the computer. For more information, see the following Remarks section. </p>

## -remarks
<p>The <b>GetSystemPowerAction</b> method enables a driver to determine whether a device's power transition is occurring because the device is idle (or waking up), or because the entire computer is entering (or leaving) a low-power state. </p>

<p>The driver must call <b>GetSystemPowerAction</b> only from the event callback functions that the framework calls when the device is <a href="wdf.a_device_enters_a_low_power_state">entering a low-power state</a> or <a href="wdf.a_device_returns_to_its_working_state">returning to its working state</a>. </p>

<p>The value that <b>GetSystemPowerAction</b> returns depends on the following situations:</p>

<p>If the computer is entering a low-power state when the driver calls <b>GetSystemPowerAction</b>, the method returns the reason that the computer is entering the low-power state. For example, the method returns <b>PowerActionSleep</b> if the computer is entering its S1, S2, or S3 low-power state.</p>

<p>If the computer is returning to its working (S0) state from a low-power state when the driver calls <b>GetSystemPowerAction</b>, the method returns the reason that the computer entered the low-power state. For example, the method returns <b>PowerActionSleep</b> if the computer is leaving its S1, S2, or S3 low-power state.</p>

<p>If the computer is powering up (after having been turned off) when the driver calls <b>GetSystemPowerAction</b>, the method returns <b>PowerActionNone</b>.</p>

<p>If the device is entering a low-power idle state or returning to its working (D0) state when the driver calls <b>GetSystemPowerAction</b>, while the rest of the system remains at its working (S0) state, the method returns <b>PowerActionNone</b>.</p>

<p>If the computer and the device are both in their working states when the driver calls <b>GetSystemPowerAction</b>, the method returns <b>PowerActionNone</b>.</p>

<p>For more information about low-power states, see <a href="wdf.a_device_enters_a_low_power_state">A Device Enters a Low-Power State</a>.</p>

<p>The following code example obtains the <a href="https://msdn.microsoft.com/library/windows/hardware/ff556918">IWDFDevice2</a> interface and then calls <b>GetSystemPowerAction</b>.</p>

<p>The <b>GetSystemPowerAction</b> method enables a driver to determine whether a device's power transition is occurring because the device is idle (or waking up), or because the entire computer is entering (or leaving) a low-power state. </p>

<p>The driver must call <b>GetSystemPowerAction</b> only from the event callback functions that the framework calls when the device is <a href="wdf.a_device_enters_a_low_power_state">entering a low-power state</a> or <a href="wdf.a_device_returns_to_its_working_state">returning to its working state</a>. </p>

<p>The value that <b>GetSystemPowerAction</b> returns depends on the following situations:</p>

<p>If the computer is entering a low-power state when the driver calls <b>GetSystemPowerAction</b>, the method returns the reason that the computer is entering the low-power state. For example, the method returns <b>PowerActionSleep</b> if the computer is entering its S1, S2, or S3 low-power state.</p>

<p>If the computer is returning to its working (S0) state from a low-power state when the driver calls <b>GetSystemPowerAction</b>, the method returns the reason that the computer entered the low-power state. For example, the method returns <b>PowerActionSleep</b> if the computer is leaving its S1, S2, or S3 low-power state.</p>

<p>If the computer is powering up (after having been turned off) when the driver calls <b>GetSystemPowerAction</b>, the method returns <b>PowerActionNone</b>.</p>

<p>If the device is entering a low-power idle state or returning to its working (D0) state when the driver calls <b>GetSystemPowerAction</b>, while the rest of the system remains at its working (S0) state, the method returns <b>PowerActionNone</b>.</p>

<p>If the computer and the device are both in their working states when the driver calls <b>GetSystemPowerAction</b>, the method returns <b>PowerActionNone</b>.</p>

<p>For more information about low-power states, see <a href="wdf.a_device_enters_a_low_power_state">A Device Enters a Low-Power State</a>.</p>

<p>The following code example obtains the <a href="https://msdn.microsoft.com/library/windows/hardware/ff556918">IWDFDevice2</a> interface and then calls <b>GetSystemPowerAction</b>.</p>

<p>The <b>GetSystemPowerAction</b> method enables a driver to determine whether a device's power transition is occurring because the device is idle (or waking up), or because the entire computer is entering (or leaving) a low-power state. </p>

<p>The driver must call <b>GetSystemPowerAction</b> only from the event callback functions that the framework calls when the device is <a href="wdf.a_device_enters_a_low_power_state">entering a low-power state</a> or <a href="wdf.a_device_returns_to_its_working_state">returning to its working state</a>. </p>

<p>The value that <b>GetSystemPowerAction</b> returns depends on the following situations:</p>

<p>If the computer is entering a low-power state when the driver calls <b>GetSystemPowerAction</b>, the method returns the reason that the computer is entering the low-power state. For example, the method returns <b>PowerActionSleep</b> if the computer is entering its S1, S2, or S3 low-power state.</p>

<p>If the computer is returning to its working (S0) state from a low-power state when the driver calls <b>GetSystemPowerAction</b>, the method returns the reason that the computer entered the low-power state. For example, the method returns <b>PowerActionSleep</b> if the computer is leaving its S1, S2, or S3 low-power state.</p>

<p>If the computer is powering up (after having been turned off) when the driver calls <b>GetSystemPowerAction</b>, the method returns <b>PowerActionNone</b>.</p>

<p>If the device is entering a low-power idle state or returning to its working (D0) state when the driver calls <b>GetSystemPowerAction</b>, while the rest of the system remains at its working (S0) state, the method returns <b>PowerActionNone</b>.</p>

<p>If the computer and the device are both in their working states when the driver calls <b>GetSystemPowerAction</b>, the method returns <b>PowerActionNone</b>.</p>

<p>For more information about low-power states, see <a href="wdf.a_device_enters_a_low_power_state">A Device Enters a Low-Power State</a>.</p>

<p>The following code example obtains the <a href="https://msdn.microsoft.com/library/windows/hardware/ff556918">IWDFDevice2</a> interface and then calls <b>GetSystemPowerAction</b>.</p>

<p>The <b>GetSystemPowerAction</b> method enables a driver to determine whether a device's power transition is occurring because the device is idle (or waking up), or because the entire computer is entering (or leaving) a low-power state. </p>

<p>The driver must call <b>GetSystemPowerAction</b> only from the event callback functions that the framework calls when the device is <a href="wdf.a_device_enters_a_low_power_state">entering a low-power state</a> or <a href="wdf.a_device_returns_to_its_working_state">returning to its working state</a>. </p>

<p>The value that <b>GetSystemPowerAction</b> returns depends on the following situations:</p>

<p>If the computer is entering a low-power state when the driver calls <b>GetSystemPowerAction</b>, the method returns the reason that the computer is entering the low-power state. For example, the method returns <b>PowerActionSleep</b> if the computer is entering its S1, S2, or S3 low-power state.</p>

<p>If the computer is returning to its working (S0) state from a low-power state when the driver calls <b>GetSystemPowerAction</b>, the method returns the reason that the computer entered the low-power state. For example, the method returns <b>PowerActionSleep</b> if the computer is leaving its S1, S2, or S3 low-power state.</p>

<p>If the computer is powering up (after having been turned off) when the driver calls <b>GetSystemPowerAction</b>, the method returns <b>PowerActionNone</b>.</p>

<p>If the device is entering a low-power idle state or returning to its working (D0) state when the driver calls <b>GetSystemPowerAction</b>, while the rest of the system remains at its working (S0) state, the method returns <b>PowerActionNone</b>.</p>

<p>If the computer and the device are both in their working states when the driver calls <b>GetSystemPowerAction</b>, the method returns <b>PowerActionNone</b>.</p>

<p>For more information about low-power states, see <a href="wdf.a_device_enters_a_low_power_state">A Device Enters a Low-Power State</a>.</p>

<p>The following code example obtains the <a href="https://msdn.microsoft.com/library/windows/hardware/ff556918">IWDFDevice2</a> interface and then calls <b>GetSystemPowerAction</b>.</p>

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
<p>1.9</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wudfddi.h (include Wudfddi.h)</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff556918">IWDFDevice2</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20IWDFDevice2::GetSystemPowerAction method%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>