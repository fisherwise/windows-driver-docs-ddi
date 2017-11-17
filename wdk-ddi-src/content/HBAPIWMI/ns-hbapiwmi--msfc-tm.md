---
UID: NS.hbapiwmi._MSFC_TM
title: MSFC_TM
author: windows-driver-content
description: The MSFC_TM structure is used by WMI providers to timestamp events.
old-location: storage\msfc_tm.htm
ms.assetid: 7e27f53f-350e-4315-9de6-60835bddcbfb
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: Storage
req.header: hbapiwmi.h
req.include-header: Hbapiwmi.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: MSFC_TM
req.alt-loc: hbapiwmi.h
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
ms.keywords: MSFC_TM, MSFC_TM, *PMSFC_TM
req.iface: 
---

# MSFC_TM structure



## -description
<p>The MSFC_TM structure is used by WMI providers to timestamp events. </p>


## -syntax

````
typedef struct _MSFC_TM {
  ULONG tm_sec;
  ULONG tm_min;
  ULONG tm_hour;
  ULONG tm_mday;
  ULONG tm_mon;
  ULONG tm_year;
  ULONG tm_wday;
  ULONG tm_yday;
  ULONG tm_isdst;
} MSFC_TM, *PMSFC_TM;
````


## -struct-fields
<dl>

### -field <b>tm_sec</b>

<dd>
<p>Indicates the number of seconds past the minute. This member must have a value between 0 and 59. </p>
</dd>

### -field <b>tm_min</b>

<dd>
<p>Indicates the number of minutes after the hour. This member must have a value between 0 and 59.</p>
</dd>

### -field <b>tm_hour</b>

<dd>
<p>Indicates the number of hours since midnight. This member must have a value between 0 and 23.</p>
</dd>

### -field <b>tm_mday</b>

<dd>
<p>Indicates the day of the month. This member must have a value between 1 and 31.</p>
</dd>

### -field <b>tm_mon</b>

<dd>
<p>Indicates the number of months since January. This member must have a value between 0 and 11.</p>
</dd>

### -field <b>tm_year</b>

<dd>
<p>Indicates the number of years since 1900. </p>
</dd>

### -field <b>tm_wday</b>

<dd>
<p>Indicates the number of days since Sunday. This member must have a value between 0 and 6.</p>
</dd>

### -field <b>tm_yday</b>

<dd>
<p>Indicates the number of days since January 1. This member must have a value between 0 and 365.</p>
</dd>

### -field <b>tm_isdst</b>

<dd>
<p>Indicates when <b>TRUE</b> that the time stamp complies with daylight savings time. When <b>FALSE</b>, indicates that the timestamp does not comply with daylight savings time. </p>
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
<dt>Hbapiwmi.h (include Hbapiwmi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff562965">MSFC_TM WMI Class</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20MSFC_TM structure%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>