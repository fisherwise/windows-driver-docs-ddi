---
UID: NS.ksmedia.PKSPROPERTY_TUNER_CAPS_S
title: PKSPROPERTY_TUNER_CAPS_S
author: windows-driver-content
description: The KSPROPERTY_TUNER_CAPS_S structure describes the hardware capabilities of TV and radio tuning devices.
old-location: stream\ksproperty_tuner_caps_s.htm
ms.assetid: 9d58acda-07b6-4dc2-8f6a-83c6e8bd8e44
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
req.alt-api: KSPROPERTY_TUNER_CAPS_S
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
ms.keywords: PKSPROPERTY_TUNER_CAPS_S, KSPROPERTY_TUNER_CAPS_S, *PKSPROPERTY_TUNER_CAPS_S
req.iface: 
---

# PKSPROPERTY_TUNER_CAPS_S structure



## -description
<p>The KSPROPERTY_TUNER_CAPS_S structure describes the hardware capabilities of TV and radio tuning devices.</p>


## -syntax

````
typedef struct {
  KSPROPERTY   Property;
  ULONG        ModesSupported;
  KSPIN_MEDIUM VideoMedium;
  KSPIN_MEDIUM TVAudioMedium;
  KSPIN_MEDIUM RadioAudioMedium;
} KSPROPERTY_TUNER_CAPS_S, *PKSPROPERTY_TUNER_CAPS_S;
````


## -struct-fields
<dl>

### -field <b>Property</b>

<dd>
<p>Specifies an initialized <a href="https://msdn.microsoft.com/library/windows/hardware/ff564262">KSPROPERTY</a> structure that describes the property set, property ID, and request type.</p>
</dd>

### -field <b>ModesSupported</b>

<dd>
<p>Specifies a bitwise OR of the supported tuner modes. This member may be set to one or more of the following values from the KSPROPERTY_TUNER_MODES enumeration that is defined in <i>ksmedia.h</i>:</p>
<table>
<tr>
<th>Flag</th>
<th>Meaning</th>
</tr>
<tr>
<td>
<p>KSPROPERTY_TUNER_MODE_TV</p>
</td>
<td>
<p>Indicates that the tuner is capable of tuning analog broadcast or cable television channels.</p>
</td>
</tr>
<tr>
<td>
<p>KSPROPERTY_TUNER_MODE_FM_RADIO</p>
</td>
<td>
<p>Indicates that the tuner is capable of tuning FM radio channels.</p>
</td>
</tr>
<tr>
<td>
<p>KSPROPERTY_TUNER_MODE_AM_RADIO</p>
</td>
<td>
<p>Indicates that the tuner is capable of tuning AM radio channels.</p>
</td>
</tr>
<tr>
<td>
<p>KSPROPERTY_TUNER_MODE_DSS</p>
</td>
<td>
<p>Indicates that the tuner is capable of tuning DSS channels.</p>
</td>
</tr>
<tr>
<td>
<p>KSPROPERTY_TUNER_MODE_ATSC</p>
</td>
<td>
<p>Indicates that the tuner is capable of tuning digital television channels. This setting can be used for ATSC, DVB-C, or DVB-T television reception.</p>
</td>
</tr>
</table>
<p> </p>
</dd>

### -field <b>VideoMedium</b>

<dd>
<p>Specifies a unique GUID representing the hardware connection of the analog video signal. This value enforces connections between filters. Possible values are <b>NULL</b>, indicating that no pin is created; GUID_NULL, indicating that Medium is not used to enforce connections; or a GUID. If a GUID value is used, only crossbar pins with a matching Medium GUID are allowed to connect. </p>
</dd>

### -field <b>TVAudioMedium</b>

<dd>
<p>Specifies a unique GUID representing the hardware connection of the TV audio signal. This value enforces connections between filters. Possible values are <b>NULL</b>, indicating that no pin is created; GUID_NULL, indicating that Medium is not used to enforce connections; or a GUID. If a GUID value is used, only crossbar pins with a matching Medium GUID are allowed to connect. </p>
</dd>

### -field <b>RadioAudioMedium</b>

<dd>
<p>Specifies a unique GUID representing the hardware connection of the analog radio audio signal. This value enforces connections between filters. Possible values are <b>NULL</b>, indicating that no pin is created; GUID_NULL, indicating that Medium is not used to enforce connections; or a GUID. If a GUID value is used, only crossbar pins with a matching Medium GUID are allowed to connect. </p>
</dd>
</dl>

## -remarks


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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff565825">KSPROPERTY_TUNER_CAPS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff565842">KSPROPERTY_TUNER_IF_MEDIUM</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [stream\stream]:%20KSPROPERTY_TUNER_CAPS_S structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>