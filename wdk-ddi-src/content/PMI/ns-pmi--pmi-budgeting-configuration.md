---
UID: NS.pmi._PMI_BUDGETING_CONFIGURATION
title: PMI_BUDGETING_CONFIGURATION
author: windows-driver-content
description: The PMI_BUDGETING_CONFIGURATION structure contains information about the current power budget of a power meter. A power budget defines how much power that the system can consume from the set of power supplies monitored by the power meter.
old-location: powermeter\pmi_budgeting_configuration.htm
ms.assetid: f9c3c289-30b8-4cec-8c38-198d1ba3d8ae
ms.author: windowsdriverdev
ms.date: 10/23/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: powermeter
req.header: pmi.h
req.include-header: Pmi.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows 7, Windows Server 2008 R2, and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: PMI_BUDGETING_CONFIGURATION
req.alt-loc: pmi.h
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
ms.keywords: PMI_BUDGETING_CONFIGURATION, PMI_BUDGETING_CONFIGURATION, *PPMI_BUDGETING_CONFIGURATION
req.iface: 
---

# PMI_BUDGETING_CONFIGURATION structure



## -description
<p>The PMI_BUDGETING_CONFIGURATION structure contains information about the current power budget of a power meter. A power budget defines how much power that the system can consume from the set of power supplies monitored by the power meter.</p>


## -syntax

````
typedef struct _PMI_BUDGETING_CONFIGURATION {
  ULONG ConfiguredBudget;
} PMI_BUDGETING_CONFIGURATION, *PPMI_BUDGETING_CONFIGURATION;
````


## -struct-fields
<dl>

### -field <b>ConfiguredBudget</b>

<dd>
<p>A value, in units of milliwatts (mW), that specifies the current power budget. A value of zero indicates that the power budget is not enabled on the power meter. </p>
</dd>
</dl>

## -remarks
<p>The PMI_BUDGETING_CONFIGURATION structure is returned through an <a href="https://msdn.microsoft.com/library/windows/hardware/ff543842">IOCTL_PMI_GET_CONFIGURATION</a> I/O control (IOCTL) query request. This query request has its input data set to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff543869">PMI_CONFIGURATION_TYPE</a> enumerator value of <b>PmiBudgetingConfiguration</b>. </p>

<p>If the IOCTL query request completes successfully, the request returns a <a href="https://msdn.microsoft.com/library/windows/hardware/ff543865">PMI_CONFIGURATION</a> structure with its <b>Capabilities</b> member formatted as a PM_BUDGETING_CONFIGURATION structure.</p>

<p>Unlike other PMI capability or configuration data, the power meter's current budgeting configuration can be changed. This is only possible if an IOCTL query request of <a href="https://msdn.microsoft.com/library/windows/hardware/ff543837">IOCTL_PMI_GET_CAPABILITIES</a> returns a <a href="https://msdn.microsoft.com/library/windows/hardware/ff543902">PMI_REPORTED_CAPABILITIES</a> structure with the <b>Writeable</b> member set to <b>TRUE</b>. In this case, the budgeting configuration for the power meter can be changed through a set request of <a href="https://msdn.microsoft.com/library/windows/hardware/ff543849">IOCTL_PMI_SET_CONFIGURATION</a>. </p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Available in Windows 7, Windows Server 2008 R2, and later versions of the Windows operating systems.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Pmi.h (include Pmi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543837">IOCTL_PMI_GET_CAPABILITIES</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543842">IOCTL_PMI_GET_CONFIGURATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543849">IOCTL_PMI_SET_CONFIGURATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543865">PMI_CONFIGURATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543869">PMI_CONFIGURATION_TYPE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543902">PMI_REPORTED_CAPABILITIES</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [powermeter\powermeter]:%20PMI_BUDGETING_CONFIGURATION structure%20 RELEASE:%20(10/23/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>