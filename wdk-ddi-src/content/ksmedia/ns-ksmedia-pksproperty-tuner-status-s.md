---
UID: NS.ksmedia.PKSPROPERTY_TUNER_STATUS_S
title: PKSPROPERTY_TUNER_STATUS_S
author: windows-driver-content
description: The KSPROPERTY_TUNER_STATUS_S structure describes the progress of a tuning operation for TV and radio tuner devices, including present tuning frequency.
old-location: stream\ksproperty_tuner_status_s.htm
ms.assetid: 5e1b37f2-f567-4c03-b0f4-cc1dbd568907
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: stream
req.header: ksmedia.h
req.include-header: Ksmedia.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: KSPROPERTY_TUNER_STATUS_S
req.alt-loc: ksmedia.h
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
ms.keywords: PKSPROPERTY_TUNER_STATUS_S, KSPROPERTY_TUNER_STATUS_S, *PKSPROPERTY_TUNER_STATUS_S
req.iface: 
---

# PKSPROPERTY_TUNER_STATUS_S structure



## -description
<p>The KSPROPERTY_TUNER_STATUS_S structure describes the progress of a tuning operation for TV and radio tuner devices, including present tuning frequency.</p>


## -syntax

````
typedef struct {
  KSPROPERTY Property;
  ULONG      CurrentFrequency;
  ULONG      PLLOffset;
  ULONG      SignalStrength;
  ULONG      Busy;
} KSPROPERTY_TUNER_STATUS_S, *PKSPROPERTY_TUNER_STATUS_S;
````


## -struct-fields
<dl>

### -field <b>Property</b>

<dd>
<p>Specifies an initialized <a href="https://msdn.microsoft.com/library/windows/hardware/ff564262">KSPROPERTY</a> structure that describes the property set, property ID, and request type. </p>
</dd>

### -field <b>CurrentFrequency</b>

<dd>
<p>Specifies the current tuner frequency. This value is in hertz (Hz).</p>
</dd>

### -field <b>PLLOffset</b>

<dd>
<p>Specifies the phase locked loop (PLL) offset in multiples of the tuning granularity. This is used if the tuner strategy is KS_TUNER_STRATEGY_PLL. If the tuner strategy is not KS_TUNER_STRATEGY_PLL, this value has no meaning. The following table demonstrates the value to be returned by the minidriver for various tuning conditions, assuming the tuning granularity is 62.5kHz:</p>
<table>
<tr>
<th>Frequency Offset</th>
<th>PLLOffset</th>
</tr>
<tr>
<td>
<p>+125,000</p>
</td>
<td>
<p>+2</p>
</td>
</tr>
<tr>
<td>
<p>+62,500</p>
</td>
<td>
<p>+1</p>
</td>
</tr>
<tr>
<td>
<p>Perfectly tuned</p>
</td>
<td>
<p>0</p>
</td>
</tr>
<tr>
<td>
<p>-62,500</p>
</td>
<td>
<p>-1</p>
</td>
</tr>
<tr>
<td>
<p>-125,000</p>
</td>
<td>
<p>-2</p>
</td>
</tr>
</table>
<p> </p>
</dd>

### -field <b>SignalStrength</b>

<dd>
<p>Specifies the amplitude of the signal. This is used if the tuner strategy is KS_TUNER_STRATEGY_SIGNAL_STRENGTH. Regardless of the tuning strategy supported by the minidriver, the valid values for this member are:</p>
<table>
<tr>
<th>Value</th>
<th>Meaning</th>
</tr>
<tr>
<td>
<p>-1</p>
</td>
<td>
<p>Strength not Available.</p>
</td>
</tr>
<tr>
<td>
<p>0</p>
</td>
<td>
<p>Not on an acceptable frequency.</p>
</td>
</tr>
<tr>
<td>
<p>1</p>
</td>
<td>
<p>On an acceptable frequency.</p>
</td>
</tr>
</table>
<p> </p>
</dd>

### -field <b>Busy</b>

<dd>
<p>Indicates if the minidriver is presently busy with the process of tuning. This member must be set to <b>TRUE</b> if the minidriver is currently tuning to a channel. Otherwise, if the minidriver is not currently tuning to a new channel, this member must be set to <b>FALSE</b>.</p>
</dd>
</dl>

## -remarks
<p>For more information about the <b>PLLOffset</b> and <b>SignalStrength</b> members see <a href="https://msdn.microsoft.com/ae97d5f7-82de-4d6e-9835-ff4c7427f333">PCI based TV capture</a>. If your tuner device supports radio tuning, see <a href="NULL">Video Capture Devices with Radio Tuners</a>.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ksmedia.h (include Ksmedia.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564262">KSPROPERTY</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567800">PROPSETID_TUNER</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff565921">KSPROPERTY_TUNER_STATUS</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [stream\stream]:%20KSPROPERTY_TUNER_STATUS_S structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>