---
UID: NS.gnssdriver.PGNSS_DEVICE_CAPABILITY
title: PGNSS_DEVICE_CAPABILITY
author: windows-driver-content
description: This structure is used to determine the device capabilities of the underlying GNSS engine.
old-location: sensors\gnss_device_capability.htm
ms.assetid: F8FA91AC-9085-4C25-8798-CEB9ADB34320
ms.author: windowsdriverdev
ms.date: 10/23/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: sensors
req.header: gnssdriver.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: GNSS_DEVICE_CAPABILITY
req.alt-loc: gnssdriver.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: <= DISPATCH_LEVEL
ms.keywords: PGNSS_DEVICE_CAPABILITY, GNSS_DEVICE_CAPABILITY, *PGNSS_DEVICE_CAPABILITY
req.iface: 
---

# PGNSS_DEVICE_CAPABILITY structure



## -description
<p>This structure is used to determine the device capabilities of the underlying GNSS engine.</p>


## -syntax

````
typedef struct {
  ULONG             Size;
  ULONG             Version;
  BOOL              SupportMultipleFixSessions;
  BOOL              SupportMultipleAppSessions;
  BOOL              RequireAgnssInjection;
  ULONG             AgnssFormatSupported;
  ULONG             AgnssFormatPreferred;
  BOOL              SupportDistanceTracking;
  BOOL              SupportContinuousTracking;
  ULONG             Reserved1;
  BOOL              Reserved2;
  BOOL              Reserved3;
  BOOL              Reserved4;
  BOOL              Reserved5;
  ULONG             GeofencingSupport;
  BOOL              Reserved6;
  BOOL              Reserved7;
  BOOL              SupportCpLocation;
  BOOL              SupportUplV2;
  BOOL              SupportSuplV1;
  BOOL              SupportSuplV2;
  GNSS_SUPL_VERSION SupportedSuplVersion;
  ULONG             MaxGeofencesSupported;
  BOOL              SupportMultipleSuplRootCert;
  ULONG             GnssBreadCrumbPayloadVersion;
  ULONG             MaxGnssBreadCrumbFixes;
  BYTE              Unused[496];
} GNSS_DEVICE_CAPABILITY, *PGNSS_DEVICE_CAPABILITY;
````


## -struct-fields
<dl>

### -field <b>Size</b>

<dd>
<p>Structure size.</p>
</dd>

### -field <b>Version</b>

<dd>
<p>Version number.</p>
</dd>

### -field <b>SupportMultipleFixSessions</b>

<dd>
<p>Indicates whether the GNSS driver natively supports multiple sessions for the same type (For example, multiple simultaneous distance tracking sessions initiated by the HLOS). If FALSE, the GNSS adapter will multiplex  the fix session requests from multiple LBS apps to combine into one fix session request that satisfies all the client requests.</p>
<p>If this capability is not present, the driver must support at least one active sessions of each supported fix session type. For example, if the driver supports distance-based tracking and single-shot functionality, it must support one distance-based fix session and one single-shot fix session active at the same time.</p>
<p>The driver must always support modification of session parameter for an active fix session type so that the GNSS adapter does not need to stop/start an ongoing fix session when a new fix request needs to be multiplexed. In Windows 10, the GNSS adapter does not support initiating in the GNSS driver multiple sessions of the same type.</p>
</dd>

### -field <b>SupportMultipleAppSessions</b>

<dd>
<p>Indicates whether the GNSS driver natively supports and tracks requests coming from multiple HLOS applications. The GNSS driver must not restrict being called from more than one application at the same time.</p>
<p>A value of TRUE indicates that the driver keeps track of the different HLOS application sessions, logically partitions the requests, ensures that request from one application session does not influence another application session, and so on. For example, it will be able to handle separately the GNSS adapter and a test application, and respond to commands from each separately.</p>
<p>A value of FALSE indicates that the driver does not differentiate different HLOS application sessions and logically treats everything in a global manner as if they all are coming from a single HLOS application-session.</p>
</dd>

### -field <b>RequireAgnssInjection</b>

<dd>
<p>Indicates whether the GNSS driver requires assistance data to be injected for faster TTFF.</p>
</dd>

### -field <b>AgnssFormatSupported</b>

<dd>
<p>Specifies a bitmask containing the different AGNSS formats (GNSS_AGNSSFORMAT_*) that the driver can handle.</p>
<pre class="syntax" xml:space="preserve"><code>#define GNSS_AGNSSFORMAT_XTRA1      0x01
#define GNSS_AGNSSFORMAT_XTRA2      0x02
#define GNSS_AGNSSFORMAT_LTO        0x04
#define GNSS_AGNSSFORMAT_XTRA3      0x08
#define GNSS_AGNSSFORMAT_XTRA3_1    0x16
</code></pre>
<p>The values 0x0020-0xFFFF are  reserved for extensibility.</p>
<p>This list currently includes a few IHV proprietary formats. The list can be updated when IHVs or OEMs decide to obtain the GNSS assistance information, specifically extended ephemeris, via the location platform.</p>
</dd>

### -field <b>AgnssFormatPreferred</b>

<dd>
<p>Specifies the preferred AGNSS format using the same bitmask as AgnssFormatSupported. For example, if both XTRA1 and XTRA2 are supported but XTRA2 is the preferred format, the GNSS driver sets AgnssFormatSupported to 0x000C and AgnssFormatPreferred to 0x0004.</p>
</dd>

### -field <b>SupportDistanceTracking</b>

<dd>
<p>Indicates whether the GNSS driver/engine natively supports low-power tracking of the device based on a session-specific threshold. A TRUE value implies that the driver can support this natively in a low-power mode, for example, by offloading the tracking to a low-power processor and not requiring the app processor to be up and poll for movement.</p>
<p>If the GNSS driver supports distance tracking, it implicitly supports other types of parallel fix sessions at the same time. For example, if a distance tracking session is active, a parallel single-shot must also be allowed and both types of fix sessions must be honored.</p>
</dd>

### -field <b>SupportContinuousTracking</b>

<dd>
<p>Indicates whether the GNSS Driver/Engine natively supports continuous low-power tracking of the device. A TRUE value implies that the driver can support this natively in a low-power mode, for example, by offloading the tracking to a low-power processor and not requiring the app processor to be up and poll continuously.</p>
<p>If the GNSS Driver supports continuous tracking, it implicitly supports other types of parallel fix sessions at the same time. For example, single-shot and continuous tracking can happen in parallel.</p>
</dd>

### -field <b>Reserved1</b>

<dd>
<p>Reserved for future use.</p>
</dd>

### -field <b>Reserved2</b>

<dd>
<p>Reserved for future use.</p>
</dd>

### -field <b>Reserved3</b>

<dd>
<p>Reserved for future use.</p>
</dd>

### -field <b>Reserved4</b>

<dd>
<p>Reserved for future use.</p>
</dd>

### -field <b>Reserved5</b>

<dd>
<p>Reserved for future use.</p>
</dd>

### -field <b>GeofencingSupport</b>

<dd>
<p>Version 1 GNSS drivers must indicate that this capability is not supported.</p>
<p>Version 2 GNSS drivers and later can indicate geofence support by setting the following bitmasks:</p>
<pre class="syntax" xml:space="preserve"><code>#define GNSS_GEOFENCESUPPORT_SUPPORTED     0x01
#define GNSS_GEOFENCESUPPORT_CIRCLE        0x02</code></pre>
<p>GNSS_GEOFENCESUPPORT_SUPPORTED indicates that the GNSS engine supports geofence tracking. Supporting geofence tracking functionality implies that it is done natively, in a power-optimized way, and uses the appropriate hybrid positioning technologies available in the GNSS engine, as applicable.</p>
<p>GNSS_GEOFENCESUPPORT_CIRCLE indicates that the GNSS engine supports circular geofences.</p>
</dd>

### -field <b>Reserved6</b>

<dd>
<p>Reserved for future use.</p>
</dd>

### -field <b>Reserved7</b>

<dd>
<p>Reserved for future use.</p>
</dd>

### -field <b>SupportCpLocation</b>

<dd>
<p>Specifies whether CP location is supported.</p>
</dd>

### -field <b>SupportUplV2</b>

<dd>
<p>Specifies whether V2 user plane location for CDMA is supported.</p>
</dd>

### -field <b>SupportSuplV1</b>

<dd>
<p>Specifies whether SUPL V1 is supported.</p>
</dd>

### -field <b>SupportSuplV2</b>

<dd>
<p>Specifies whether SUPL V2 is supported.</p>
</dd>

### -field <b>SupportedSuplVersion</b>

<dd>
<p>Specifies the latest SUPL version that is supported by the SUPL client. This version information is currently not used by the HLOS at for any validation purposes.</p>
</dd>

### -field <b>MaxGeofencesSupported</b>

<dd>
<p>Specifies the number of geofences the GNSS engine can track based on constraints set by the platform. This value will only be valid when the GeofencingSupport field is set.</p>
</dd>

### -field <b>SupportMultipleSuplRootCert</b>

<dd>
<p>Specifies the SUPL parameter.</p>
</dd>

### -field <b>GnssBreadCrumbPayloadVersion</b>

<dd>
<p>Must be BREADCRUMBING_UNSUPPORTED or BREADCRUMBING_VERSION_<i>x</i>.</p>
</dd>

### -field <b>MaxGnssBreadCrumbFixes</b>

<dd>
<p>Must greater than or equal to MIN_BREADCRUMBS_SUPPORTED.</p>
</dd>

### -field <b>Unused[496]</b>

<dd>
<p>Padding buffer.</p>
</dd>
</dl>

## -remarks
<p>This is a list of individual capability support. The capability is represented either by a Boolean or by a well-defined enumeration of the specific attribute.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Gnssdriver.h</dt>
</dl>
</td>
</tr>
</table>