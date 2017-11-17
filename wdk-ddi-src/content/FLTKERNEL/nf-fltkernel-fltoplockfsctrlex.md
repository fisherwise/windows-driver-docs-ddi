---
UID: NF.fltkernel.FltOplockFsctrlEx
title: FltOplockFsctrlEx
author: windows-driver-content
description: The FltOplockFsctrlEx routine performs various opportunistic lock (oplock) operations on behalf of a minifilter driver.
old-location: ifsk\fltoplockfsctrlex.htm
ms.assetid: 02adb7a7-0c1d-4dd4-bde2-f2e700a7ee76
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: ifsk
req.header: fltkernel.h
req.include-header: Fltkernel.h
req.target-type: Universal
req.target-min-winverclnt: This routine is available starting with Windows 8.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FltOplockFsctrlEx
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
ms.keywords: FltOplockFsctrlEx
req.iface: 
---

# FltOplockFsctrlEx function



## -description
<p>The <b>FltOplockFsctrlEx</b> routine performs various opportunistic lock (oplock) operations on behalf of a minifilter driver. </p>


## -syntax

````
FLT_PREOP_CALLBACK_STATUS FltOplockFsctrlEx(
  _In_ POPLOCK            Oplock,
  _In_ PFLT_CALLBACK_DATA CallbackData,
  _In_ ULONG              OpenCount,
  _In_ ULONG              Flags
);
````


## -parameters
<dl>

### -param <i>Oplock</i> [in]

<dd>
<p>An opaque oplock pointer for the file. This pointer must have been initialized by a previous call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff543289">FltInitializeOplock</a>. </p>
</dd>

### -param <i>CallbackData</i> [in]

<dd>
<p>A pointer to the callback data structure for the I/O operation (<a href="https://msdn.microsoft.com/library/windows/hardware/ff544620">FLT_CALLBACK_DATA</a>). This parameter is required and cannot be <b>NULL</b>. </p>
</dd>

### -param <i>OpenCount</i> [in]

<dd>
<p>The number of user handles for the file, if an exclusive oplock is being requested. Setting a nonzero value for a level 2, R, or RH oplock request indicates that there are byte-range locks on the file. For information about oplock types, see <a href="https://msdn.microsoft.com/e9a45ae0-0ec8-4d6c-8486-ae88bdaa1f8c">Oplock Semantics Overview</a>. </p>
</dd>

### -param <i>Flags</i> [in]

<dd>
<p>A bitmask for the associated oplock operations. A minifilter driver sets bits to specify the behavior of <b>FltOplockFsctrlEx</b>. The <i>Flags</i> parameter has the following options:</p>
<p></p>
<dl>

### -param <a id="OPLOCK_FSCTRL_FLAG_ALL_KEYS_MATCH__0x00000001_"></a><a id="oplock_fsctrl_flag_all_keys_match__0x00000001_"></a><a id="OPLOCK_FSCTRL_FLAG_ALL_KEYS_MATCH__0X00000001_"></a>OPLOCK_FSCTRL_FLAG_ALL_KEYS_MATCH (0x00000001)

<dd>
<p>Specifies that the file system verified that all oplock keys on any handles that are currently open match. By specifying this flag, you allow the oplock package to grant an oplock of level RW or RWH when more than one open handle to the file exists. For more information about oplock types, see the Oplock Semantics <a href="NULL">Overview</a> page. </p>
</dd>
</dl>
</dd>
</dl>

## -returns
<p><b>FltOplockFsctrlEx</b> returns FLT_PREOP_PENDING for some FSCTL operations. For more information, see the reference pages for the FSCTL codes listed in the following Remarks section. Otherwise, <b>FltOplockFsctrlEx</b> returns FLT_PREOP_COMPLETE. </p>

## -remarks
<p>A minifilter driver calls <b>FltOplockFsctrlEx</b> to perform various opportunistic lock operations for a create operation or file system control I/O operation. The FLT_CALLBACK_DATA structure pointed to by the <i>CallbackData</i> parameter must represent an IRP-based <a href="https://msdn.microsoft.com/library/windows/hardware/ff550751">IRP_MJ_FILE_SYSTEM_CONTROL</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff548630">IRP_MJ_CREATE</a> operation. </p>

<p>If the operation is an IRP_MJ_FILE_SYSTEM_CONTROL operation, you can use <b>FltOplockFsctrlEx</b> with the following FSCTL codes: </p><dl>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545462">FSCTL_OPBATCH_ACK_CLOSE_PENDING</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545476">FSCTL_OPLOCK_BREAK_ACK_NO_2</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545468">FSCTL_OPLOCK_BREAK_ACKNOWLEDGE</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545485">FSCTL_OPLOCK_BREAK_NOTIFY</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545510">FSCTL_REQUEST_BATCH_OPLOCK</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545518">FSCTL_REQUEST_FILTER_OPLOCK</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545538">FSCTL_REQUEST_OPLOCK_LEVEL_1</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545546">FSCTL_REQUEST_OPLOCK_LEVEL_2</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545530">FSCTL_REQUEST_OPLOCK</a>
</p>
</dd>
</dl><p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545462">FSCTL_OPBATCH_ACK_CLOSE_PENDING</a>
</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545476">FSCTL_OPLOCK_BREAK_ACK_NO_2</a>
</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545468">FSCTL_OPLOCK_BREAK_ACKNOWLEDGE</a>
</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545485">FSCTL_OPLOCK_BREAK_NOTIFY</a>
</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545510">FSCTL_REQUEST_BATCH_OPLOCK</a>
</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545518">FSCTL_REQUEST_FILTER_OPLOCK</a>
</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545538">FSCTL_REQUEST_OPLOCK_LEVEL_1</a>
</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545546">FSCTL_REQUEST_OPLOCK_LEVEL_2</a>
</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545530">FSCTL_REQUEST_OPLOCK</a>
</p>

<p>The FSCTL code is set in the <b>FsControlCode</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff544673">FLT_PARAMETERS</a> structure for the operation. For more information about <b>FsControlCode</b> and other IRP_MJ_FILE_SYSTEM_CONTROL parameters, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff544705">FLT_PARAMETERS for IRP_MJ_FILE_SYSTEM_CONTROL</a>. </p>

<p>For more information about opportunistic locks, see the Microsoft Windows SDK documentation. </p>

<p>If the operation is an <a href="https://msdn.microsoft.com/library/windows/hardware/ff548630">IRP_MJ_CREATE</a> request, you can use <b>FltOplockFsctrlEx</b>  to request a pending filter opportunistic lock if all of the following conditions are true: </p>

<p>The value of the <i>OpenCount</i> parameter is 1. </p>

<p>The value of the <i>DesiredAccess</i> parameter for the IRP_MJ_CREATE request is FILE_READ_ATTRIBUTES. This parameter is set in the <b>SecurityContext</b> member of the FLT_PARAMETERS structure for the operation. For more information, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff544687">FLT_PARAMETERS for IRP_MJ_CREATE</a>. </p>

<p>The value of the <i>ShareAccess</i> parameter for the IRP_MJ_CREATE operation is FILE_SHARE_READ, FILE_SHARE_WRITE, or FILE_SHARE_DELETE. This parameter is set in the <b>ShareAccess</b> member of the FLT_PARAMETERS structure for the operation. For more information, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff544687">FLT_PARAMETERS for IRP_MJ_CREATE</a>. </p>

<p>A minifilter driver calls <b>FltOplockFsctrlEx</b> to perform various opportunistic lock operations for a create operation or file system control I/O operation. The FLT_CALLBACK_DATA structure pointed to by the <i>CallbackData</i> parameter must represent an IRP-based <a href="https://msdn.microsoft.com/library/windows/hardware/ff550751">IRP_MJ_FILE_SYSTEM_CONTROL</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff548630">IRP_MJ_CREATE</a> operation. </p>

<p>If the operation is an IRP_MJ_FILE_SYSTEM_CONTROL operation, you can use <b>FltOplockFsctrlEx</b> with the following FSCTL codes: </p><dl>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545462">FSCTL_OPBATCH_ACK_CLOSE_PENDING</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545476">FSCTL_OPLOCK_BREAK_ACK_NO_2</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545468">FSCTL_OPLOCK_BREAK_ACKNOWLEDGE</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545485">FSCTL_OPLOCK_BREAK_NOTIFY</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545510">FSCTL_REQUEST_BATCH_OPLOCK</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545518">FSCTL_REQUEST_FILTER_OPLOCK</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545538">FSCTL_REQUEST_OPLOCK_LEVEL_1</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545546">FSCTL_REQUEST_OPLOCK_LEVEL_2</a>
</p>
</dd>
<dd>
<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545530">FSCTL_REQUEST_OPLOCK</a>
</p>
</dd>
</dl><p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545462">FSCTL_OPBATCH_ACK_CLOSE_PENDING</a>
</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545476">FSCTL_OPLOCK_BREAK_ACK_NO_2</a>
</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545468">FSCTL_OPLOCK_BREAK_ACKNOWLEDGE</a>
</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545485">FSCTL_OPLOCK_BREAK_NOTIFY</a>
</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545510">FSCTL_REQUEST_BATCH_OPLOCK</a>
</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545518">FSCTL_REQUEST_FILTER_OPLOCK</a>
</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545538">FSCTL_REQUEST_OPLOCK_LEVEL_1</a>
</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545546">FSCTL_REQUEST_OPLOCK_LEVEL_2</a>
</p>

<p>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545530">FSCTL_REQUEST_OPLOCK</a>
</p>

<p>The FSCTL code is set in the <b>FsControlCode</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff544673">FLT_PARAMETERS</a> structure for the operation. For more information about <b>FsControlCode</b> and other IRP_MJ_FILE_SYSTEM_CONTROL parameters, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff544705">FLT_PARAMETERS for IRP_MJ_FILE_SYSTEM_CONTROL</a>. </p>

<p>For more information about opportunistic locks, see the Microsoft Windows SDK documentation. </p>

<p>If the operation is an <a href="https://msdn.microsoft.com/library/windows/hardware/ff548630">IRP_MJ_CREATE</a> request, you can use <b>FltOplockFsctrlEx</b>  to request a pending filter opportunistic lock if all of the following conditions are true: </p>

<p>The value of the <i>OpenCount</i> parameter is 1. </p>

<p>The value of the <i>DesiredAccess</i> parameter for the IRP_MJ_CREATE request is FILE_READ_ATTRIBUTES. This parameter is set in the <b>SecurityContext</b> member of the FLT_PARAMETERS structure for the operation. For more information, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff544687">FLT_PARAMETERS for IRP_MJ_CREATE</a>. </p>

<p>The value of the <i>ShareAccess</i> parameter for the IRP_MJ_CREATE operation is FILE_SHARE_READ, FILE_SHARE_WRITE, or FILE_SHARE_DELETE. This parameter is set in the <b>ShareAccess</b> member of the FLT_PARAMETERS structure for the operation. For more information, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff544687">FLT_PARAMETERS for IRP_MJ_CREATE</a>. </p>

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
<p>This routine is available starting with Windows 8. </p>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544620">FLT_CALLBACK_DATA</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544687">FLT_PARAMETERS for IRP_MJ_CREATE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544705">FLT_PARAMETERS for IRP_MJ_FILE_SYSTEM_CONTROL</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff543289">FltInitializeOplock</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545462">FSCTL_OPBATCH_ACK_CLOSE_PENDING</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545476">FSCTL_OPLOCK_BREAK_ACK_NO_2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545468">FSCTL_OPLOCK_BREAK_ACKNOWLEDGE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545485">FSCTL_OPLOCK_BREAK_NOTIFY</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545510">FSCTL_REQUEST_BATCH_OPLOCK</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545518">FSCTL_REQUEST_FILTER_OPLOCK</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545530">FSCTL_REQUEST_OPLOCK</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545538">FSCTL_REQUEST_OPLOCK_LEVEL_1</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545546">FSCTL_REQUEST_OPLOCK_LEVEL_2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547113">FsRtlOplockFsctrlEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff548630">IRP_MJ_CREATE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550751">IRP_MJ_FILE_SYSTEM_CONTROL</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20FltOplockFsctrlEx routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>