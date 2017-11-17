---
UID: NS.ksmedia.PKSDS3D_BUFFER_CONE_ANGLES
title: PKSDS3D_BUFFER_CONE_ANGLES
author: windows-driver-content
description: A KSDS3D_BUFFER_CONE_ANGLES structure specifies the inside and outside cone angles.
old-location: audio\ksds3d_buffer_cone_angles.htm
ms.assetid: 702d3698-396d-4609-a082-74290d2ccb41
ms.author: windowsdriverdev
ms.date: 10/30/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: audio
req.header: ksmedia.h
req.include-header: Ksmedia.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: KSDS3D_BUFFER_CONE_ANGLES
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
ms.keywords: PKSDS3D_BUFFER_CONE_ANGLES, KSDS3D_BUFFER_CONE_ANGLES, *PKSDS3D_BUFFER_CONE_ANGLES
req.iface: 
---

# PKSDS3D_BUFFER_CONE_ANGLES structure



## -description
<p>A KSDS3D_BUFFER_CONE_ANGLES structure specifies the inside and outside cone angles.</p>


## -syntax

````
typedef struct {
  ULONG InsideConeAngle;
  ULONG OutsideConeAngle;
} KSDS3D_BUFFER_CONE_ANGLES, *PKSDS3D_BUFFER_CONE_ANGLES;
````


## -struct-fields
<dl>

### -field <b>InsideConeAngle</b>

<dd>
<p>Specifies the angle in degrees of the inside sound projection cone.</p>
</dd>

### -field <b>OutsideConeAngle</b>

<dd>
<p>Specifies the angle in degrees of the outside sound projection cone.</p>
</dd>
</dl>

## -remarks
<p>This structure is used to set or get the data value for the <a href="https://msdn.microsoft.com/library/windows/hardware/ff537318">KSPROPERTY_DIRECTSOUND3DBUFFER_CONEANGLES</a> property. DirectSound uses this property to implement the <b>IDirectSound3DBuffer::GetConeAngles</b> and <b>IDirectSound3DBuffer::SetConeAngles</b> methods, which are described in the Microsoft Windows SDK documentation.</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff537318">KSPROPERTY_DIRECTSOUND3DBUFFER_CONEANGLES</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [audio\audio]:%20KSDS3D_BUFFER_CONE_ANGLES structure%20 RELEASE:%20(10/30/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>