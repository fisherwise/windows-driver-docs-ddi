---
UID: NI.ntddsysenv.IOCTL_SYSENV_QUERY_VARIABLE_INFO
title: IOCTL_SYSENV_QUERY_VARIABLE_INFO
author: windows-driver-content
description: Returns information about system environment variables using SysEnv device.
old-location: kernel\ioctl_ioctl_sysenv_query_variable_info.htm
ms.assetid: 4056202F-2292-40A5-BE1D-8C1A6FA79B50
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: ioctl
ms.prod: windows-hardware
ms.technology: kernel
req.header: ntddsysenv.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IOCTL_SYSENV_QUERY_VARIABLE_INFO
req.alt-loc: Ntddsysenv.h
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
ms.keywords: STORAGE_BREAK_RESERVATION_REQUEST, STORAGE_BREAK_RESERVATION_REQUEST, *PSTORAGE_BREAK_RESERVATION_REQUEST
req.iface: 
---

# IOCTL_SYSENV_QUERY_VARIABLE_INFO IOCTL



## -description
<p>
<p>Returns information about system environment variables using
    SysEnv device.
</p>
</p>
<p>Returns information about system environment variables using
    SysEnv device.
</p>


## -ioctlparameters

### -input-buffer
<p>A pointer to a ULONG variable that contains the attributes of the system environment variable.</p>

<p>A pointer to a ULONG variable that contains the attributes of the system environment variable.</p>

### -input-buffer-length
<p>Size of ULONG.</p>

<p>Size of ULONG.</p>

<p>Size of ULONG.</p>

### -output-buffer
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/mt791534">SYSENV_VARIABLE_INFO</a> structure that contains variable information.</p>

<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/mt791534">SYSENV_VARIABLE_INFO</a> structure that contains variable information.</p>

<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/mt791534">SYSENV_VARIABLE_INFO</a> structure that contains variable information.</p>

<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/mt791534">SYSENV_VARIABLE_INFO</a> structure that contains variable information.</p>

### -output-buffer-length
<p>The size of the <a href="https://msdn.microsoft.com/library/windows/hardware/mt791534">SYSENV_VARIABLE_INFO</a> structure.</p>

<p>The size of the <a href="https://msdn.microsoft.com/library/windows/hardware/mt791534">SYSENV_VARIABLE_INFO</a> structure.</p>

<p>The size of the <a href="https://msdn.microsoft.com/library/windows/hardware/mt791534">SYSENV_VARIABLE_INFO</a> structure.</p>

<p>The size of the <a href="https://msdn.microsoft.com/library/windows/hardware/mt791534">SYSENV_VARIABLE_INFO</a> structure.</p>

<p>The size of the <a href="https://msdn.microsoft.com/library/windows/hardware/mt791534">SYSENV_VARIABLE_INFO</a> structure.</p>

### -in-out-buffer

<text></text>

### -inout-buffer-length

<text></text>

### -status-block
I/O Status block
<p><b>Irp-&gt;IoStatus.Status</b> is set to STATUS_SUCCESS if the request is successful. Otherwise, <b>Status</b> to the appropriate error condition as a <a href="https://msdn.microsoft.com/7792201b-63bb-4db5-803d-2af02893d505">NTSTATUS</a> code. </p>

<p><b>Irp-&gt;IoStatus.Status</b> is set to STATUS_SUCCESS if the request is successful. Otherwise, <b>Status</b> to the appropriate error condition as a <a href="https://msdn.microsoft.com/7792201b-63bb-4db5-803d-2af02893d505">NTSTATUS</a> code. </p>

<p><b>Irp-&gt;IoStatus.Status</b> is set to STATUS_SUCCESS if the request is successful. Otherwise, <b>Status</b> to the appropriate error condition as a <a href="https://msdn.microsoft.com/7792201b-63bb-4db5-803d-2af02893d505">NTSTATUS</a> code. </p>

<p><b>Irp-&gt;IoStatus.Status</b> is set to STATUS_SUCCESS if the request is successful. Otherwise, <b>Status</b> to the appropriate error condition as a <a href="https://msdn.microsoft.com/7792201b-63bb-4db5-803d-2af02893d505">NTSTATUS</a> code. </p>

<p><b>Irp-&gt;IoStatus.Status</b> is set to STATUS_SUCCESS if the request is successful. Otherwise, <b>Status</b> to the appropriate error condition as a <a href="https://msdn.microsoft.com/7792201b-63bb-4db5-803d-2af02893d505">NTSTATUS</a> code. </p>

<p><b>Irp-&gt;IoStatus.Status</b> is set to STATUS_SUCCESS if the request is successful. Otherwise, <b>Status</b> to the appropriate error condition as a <a href="https://msdn.microsoft.com/7792201b-63bb-4db5-803d-2af02893d505">NTSTATUS</a> code. </p>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntddsysenv.h</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff542894">Creating IOCTL Requests in Drivers</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548651">WdfIoTargetSendInternalIoctlOthersSynchronously</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548656">WdfIoTargetSendInternalIoctlSynchronously</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548660">WdfIoTargetSendIoctlSynchronously</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20IOCTL_SYSENV_QUERY_VARIABLE_INFO control code%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>