---
UID: NS.ntddtape._TAPE_WMI_OPERATIONS
title: TAPE_WMI_OPERATIONS
author: windows-driver-content
description: The tape miniclass driver passes this structure to its TapeMiniWMIControl routine to indicate which WMI operation must be performed by the device.
old-location: storage\tape_wmi_operations.htm
ms.assetid: 430d982e-4740-46ad-8391-aba5813a833a
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: Storage
req.header: ntddtape.h
req.include-header: Ntddchgr.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: TAPE_WMI_OPERATIONS
req.alt-loc: ntddtape.h
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
ms.keywords: TAPE_WMI_OPERATIONS, TAPE_WMI_OPERATIONS, *PTAPE_WMI_OPERATIONS
req.iface: 
---

# TAPE_WMI_OPERATIONS structure



## -description
<p>The tape miniclass driver passes this structure to its <a href="https://msdn.microsoft.com/library/windows/hardware/ff567957">TapeMiniWMIControl</a> routine to indicate which WMI operation must be performed by the device. </p>


## -syntax

````
typedef struct _TAPE_WMI_OPERATIONS {
  ULONG Method;
  ULONG DataBufferSize;
  PVOID DataBuffer;
} TAPE_WMI_OPERATIONS, *PTAPE_WMI_OPERATIONS;
````


## -struct-fields
<dl>

### -field <b>Method</b>

<dd>
<p>Indicates the operation to be performed by the tape device. The operations allowed are as follows:</p>
<p></p>
<dl>

### -field <a id="TAPE_CHECK_FOR_DRIVE_PROBLEM"></a><a id="tape_check_for_drive_problem"></a>TAPE_CHECK_FOR_DRIVE_PROBLEM

<dd>
<p>If the tape drive supports commands to return specific device errors, such as tape alerts, the minidriver's <a href="https://msdn.microsoft.com/library/windows/hardware/ff567957">TapeMiniWMIControl</a> routine should execute the TAPE_QUERY_DEVICE_ERROR_DATA method Otherwise, it should execute the TAPE_QUERY_IO_ERROR_DATA method.</p>
</dd>
</dl>
<p></p>
<dl>

### -field <a id="TAPE_QUERY_DEVICE_ERROR_DATA"></a><a id="tape_query_device_error_data"></a>TAPE_QUERY_DEVICE_ERROR_DATA

<dd>
<p>Returns specific device errors, such as tape alerts. Not all tape drives support this method.</p>
</dd>
</dl>
<p></p>
<dl>

### -field <a id="TAPE_QUERY_IO_ERROR_DATA__"></a><a id="tape_query_io_error_data__"></a>TAPE_QUERY_IO_ERROR_DATA  

<dd>
<p>Returns general I/O error data, such as read/write errors, based on the I/O error count. All tape drives support this method.</p>
</dd>
</dl>
</dd>

### -field <b>DataBufferSize</b>

<dd>
<p>Indicates the size in bytes of the buffer in which the tape minidriver returns the results of the operation. </p>
</dd>

### -field <b>DataBuffer</b>

<dd>
<p>Pointer to a buffer in which the tape minidriver returns the results of the operation. The first <b>sizeof</b>(ULONG) bytes of <b>DataBuffer</b> contain a value of type <a href="https://msdn.microsoft.com/library/windows/hardware/ff567962">TAPE_DRIVE_PROBLEM_TYPE</a>, followed by <b>DataBufferSize</b> - <b>sizeof</b>(ULONG) bytes of tape data. </p>
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
<dt>Ntddtape.h (include Ntddchgr.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567957">TapeMiniWMIControl</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567962">TAPE_DRIVE_PROBLEM_TYPE</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20TAPE_WMI_OPERATIONS structure%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>