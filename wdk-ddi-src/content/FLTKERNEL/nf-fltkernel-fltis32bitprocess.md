---
UID: NF.fltkernel.FltIs32bitProcess
title: FltIs32bitProcess
author: windows-driver-content
description: The FltIs32bitProcess routine checks whether the originator of the current I/O operation is a 32-bit user-mode application.
old-location: ifsk\fltis32bitprocess.htm
ms.assetid: 0ba4d101-5eba-4258-9526-9e9dc3fd142a
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: ifsk
req.header: fltkernel.h
req.include-header: Fltkernel.h
req.target-type: Universal
req.target-min-winverclnt: The FltIs32bitProcess routine is available on Microsoft Windows XP SP2, Microsoft Windows Server 2003 SP1, and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FltIs32bitProcess
req.alt-loc: fltmgr.sys
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: FltMgr.lib
req.dll: Fltmgr.sys
req.irql: <= APC_LEVEL
ms.keywords: FltIs32bitProcess
req.iface: 
---

# FltIs32bitProcess function



## -description
<p>The <b>FltIs32bitProcess</b> routine checks whether the originator of the current I/O operation is a 32-bit user-mode application.</p>


## -syntax

````
BOOLEAN FltIs32bitProcess(
  _In_opt_ PFLT_CALLBACK_DATA CallbackData
);
````


## -parameters
<dl>

### -param <i>CallbackData</i> [in, optional]

<dd>
<p>Pointer to the callback data structure for the current I/O operation (<a href="https://msdn.microsoft.com/library/windows/hardware/ff544620">FLT_CALLBACK_DATA</a>). This parameter is optional and can be <b>NULL</b>. </p>
</dd>
</dl>

## -returns
<p><b>FltIs32bitProcess</b> returns <b>TRUE</b> if the originator of the current I/O operation is a 32-bit user-mode process, <b>FALSE</b> otherwise.</p>

## -remarks
<p>Minifilter drivers call <b>FltIs32bitProcess</b> to determine whether an I/O request is likely to contain data elements that need to be converted, or "thunked," before they can be used in a 64-bit driver. For more information about thunking and other 64-bit driver issues, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff559923">Programming Issues for 64-Bit Drivers</a>. </p>

<p>On a 32-bit system, <b>FltIs32bitProcess</b> always returns <b>TRUE</b>. </p>

<p>On a 64-bit system, <b>FltIs32bitProcess</b> returns <b>TRUE</b> or <b>FALSE</b>, according to the following conditions: </p>

<p>If the <i>CallbackData</i> parameter is <b>NULL</b>, and the caller is running in the context of a 32-bit user-mode process, <b>FltIs32bitProcess</b> returns <b>TRUE</b>. </p>

<p>If the <i>CallbackData</i> parameter is not <b>NULL</b>, and the callback data structure represents an IRP-based I/O operation where IRP was issued by the I/O manager on behalf of a user-mode process, <b>FltIs32bitProcess</b> returns <b>TRUE</b>. </p>

<p>If the <i>CallbackData</i> parameter is not <b>NULL</b>, the callback data structure represents a fast I/O operation or a file system filter (FSFilter) callback operation, and the caller is running in the context of a 32-bit user-mode process, <b>FltIs32bitProcess</b> returns <b>TRUE</b>. </p>

<p>If none of the above conditions is <b>true</b>, <b>FltIs32bitProcess</b> returns <b>FALSE</b>. </p>

<p>To determine whether a callback data structure represents an IRP-based I/O operation, use the <a href="https://msdn.microsoft.com/library/windows/hardware/ff544654">FLT_IS_IRP_OPERATION</a> macro. </p>

<p>To determine whether a callback data structure represents a fast I/O operation, use the <a href="https://msdn.microsoft.com/library/windows/hardware/ff544645">FLT_IS_FASTIO_OPERATION</a> macro. </p>

<p>To determine whether a callback data structure represents a file system filter (FSFilter) callback operation, use the <a href="https://msdn.microsoft.com/library/windows/hardware/ff544648">FLT_IS_FS_FILTER_OPERATION</a> macro.</p>

<p>Minifilter drivers call <b>FltIs32bitProcess</b> to determine whether an I/O request is likely to contain data elements that need to be converted, or "thunked," before they can be used in a 64-bit driver. For more information about thunking and other 64-bit driver issues, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff559923">Programming Issues for 64-Bit Drivers</a>. </p>

<p>On a 32-bit system, <b>FltIs32bitProcess</b> always returns <b>TRUE</b>. </p>

<p>On a 64-bit system, <b>FltIs32bitProcess</b> returns <b>TRUE</b> or <b>FALSE</b>, according to the following conditions: </p>

<p>If the <i>CallbackData</i> parameter is <b>NULL</b>, and the caller is running in the context of a 32-bit user-mode process, <b>FltIs32bitProcess</b> returns <b>TRUE</b>. </p>

<p>If the <i>CallbackData</i> parameter is not <b>NULL</b>, and the callback data structure represents an IRP-based I/O operation where IRP was issued by the I/O manager on behalf of a user-mode process, <b>FltIs32bitProcess</b> returns <b>TRUE</b>. </p>

<p>If the <i>CallbackData</i> parameter is not <b>NULL</b>, the callback data structure represents a fast I/O operation or a file system filter (FSFilter) callback operation, and the caller is running in the context of a 32-bit user-mode process, <b>FltIs32bitProcess</b> returns <b>TRUE</b>. </p>

<p>If none of the above conditions is <b>true</b>, <b>FltIs32bitProcess</b> returns <b>FALSE</b>. </p>

<p>To determine whether a callback data structure represents an IRP-based I/O operation, use the <a href="https://msdn.microsoft.com/library/windows/hardware/ff544654">FLT_IS_IRP_OPERATION</a> macro. </p>

<p>To determine whether a callback data structure represents a fast I/O operation, use the <a href="https://msdn.microsoft.com/library/windows/hardware/ff544645">FLT_IS_FASTIO_OPERATION</a> macro. </p>

<p>To determine whether a callback data structure represents a file system filter (FSFilter) callback operation, use the <a href="https://msdn.microsoft.com/library/windows/hardware/ff544648">FLT_IS_FS_FILTER_OPERATION</a> macro.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt><a href="http://go.microsoft.com/fwlink/p/?linkid=531356" target="_blank">Universal</a></dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>The FltIs32bitProcess routine is available on Microsoft Windows XP SP2, Microsoft Windows Server 2003 SP1, and later. </p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Fltkernel.h (include Fltkernel.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>FltMgr.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>Fltmgr.sys</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&lt;= APC_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544645">FLT_IS_FASTIO_OPERATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544648">FLT_IS_FS_FILTER_OPERATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544654">FLT_IS_IRP_OPERATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549372">IoIs32bitProcess</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20FltIs32bitProcess routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>