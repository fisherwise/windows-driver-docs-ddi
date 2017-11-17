---
UID: NS.ksmedia._KSCAMERA_PROFILE_PININFO
title: KSCAMERA_PROFILE_PININFO
author: windows-driver-content
description: This structure specifies the available list of media types for each of the camera driver pins.
old-location: stream\kscamera_profile_pininfo.htm
ms.assetid: 09B7D454-D28C-4E3F-9FF3-0DD595CDB90A
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: stream
req.header: ksmedia.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: KSCAMERA_PROFILE_PININFO
req.alt-loc: Ksmedia.h
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
ms.keywords: KSCAMERA_PROFILE_PININFO, KSCAMERA_PROFILE_PININFO, *PKSCAMERA_PROFILE_PININFO
req.iface: 
---

# KSCAMERA_PROFILE_PININFO structure



## -description
<p>This structure specifies the available list of media types for each of the camera driver pins.</p>


## -syntax

````
typedef struct _KSCAMERA_PROFILE_PININFO {
  GUID                        PinCategory;
  UINT32                      Reserved;
  UINT32                      MediaInfoCount;
  PKSCAMERA_PROFILE_MEDIAINFO MediaInfos;
} KSCAMERA_PROFILE_PININFO, *PKSCAMERA_PROFILE_PININFO;
````


## -struct-fields
<dl>

### -field <b>PinCategory</b>

<dd>
<p>This is the PINNAME category corresponding to Capture, Preview or Still image pin.  For Windows 10, the only supported pin categories are:  PINNAME_VIDEO_CAPTURE, PINNAME_VIDEO_PREVIEW, PINNAME_VIDEO_STILL.  All other categories will result in an STATUS_INVALID_PARAMETER error.</p>
</dd>

### -field <b>Reserved</b>

<dd>
<p>Unused. Must be 0.</p>
</dd>

### -field <b>MediaInfoCount</b>

<dd>
<p>Array size of KSCAMERA_PROFILE_MEDIAINFO structures specified in the MediaInfos field.</p>
</dd>

### -field <b>MediaInfos</b>

<dd>
<p>Array of KSCAMERA_PROFILE_MEDIAINFO structures.</p>
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
<dt>Ksmedia.h</dt>
</dl>
</td>
</tr>
</table>