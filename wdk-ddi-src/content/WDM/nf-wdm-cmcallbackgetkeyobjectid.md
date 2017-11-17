---
UID: NF.wdm.CmCallbackGetKeyObjectID
title: CmCallbackGetKeyObjectID
author: windows-driver-content
description: The CmCallbackGetKeyObjectID routine retrieves the unique identifier and object name that are associated with a specified registry key object.
old-location: kernel\cmcallbackgetkeyobjectid.htm
ms.assetid: e8db3009-7941-4fcc-a888-22c887bf59d5
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: Available starting with Windows Vista.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: CmCallbackGetKeyObjectID
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: <= APC_LEVEL
ms.keywords: CmCallbackGetKeyObjectID
req.iface: 
req.product: Windows 10 or later.
---

# CmCallbackGetKeyObjectID function



## -description
<p>The <b>CmCallbackGetKeyObjectID</b> routine retrieves the unique identifier and object name that are associated with a specified registry key object.</p>


## -syntax

````
NTSTATUS CmCallbackGetKeyObjectID(
  _In_      PLARGE_INTEGER   Cookie,
  _In_      PVOID            Object,
  _Out_opt_ PULONG_PTR       ObjectID,
  _Out_opt_ PCUNICODE_STRING *ObjectName
);
````


## -parameters
<dl>

### -param <i>Cookie</i> [in]

<dd>
<p>The cookie value that the driver previously obtained by calling the <a href="https://msdn.microsoft.com/library/windows/hardware/ff541918">CmRegisterCallback</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff541921">CmRegisterCallbackEx</a> routine.</p>
</dd>

### -param <i>Object</i> [in]

<dd>
<p>The pointer value that the driver's <a href="https://msdn.microsoft.com/library/windows/hardware/ff560903">RegistryCallback</a> callback routine received in the <b>Object</b> member of one of the <b>REG_<i>XXX</i>_KEY_INFORMATION</b> structures. </p>
<div class="alert"><b>Warning</b>  In certain circumstances registry callback notification structures may contain invalid non-NULL object pointers. Registry filtering drivers must not pass such pointers to this routine. For more information, see <a href="http://go.microsoft.com/fwlink/p/?linkid=613134">Invalid Key Object Pointers in Registry Notifications</a>.</div>
<div> </div>
</dd>

### -param <i>ObjectID</i> [out, optional]

<dd>
<p>A pointer to a location that receives a pointer to the unique identifier that represents the registry key that <i>Object</i> specifies. This parameter is optional and can be <b>NULL</b>.</p>
</dd>

### -param <i>ObjectName</i> [out, optional]

<dd>
<p>A pointer to a location that receives a pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff564879">UNICODE_STRING</a> structure. This structure contains the object name of the registry key object that <i>Object</i> specifies. The object name is actually the full path name of the registry key that the object represents. The caller must not write to this <b>UNICODE_STRING</b> structure or free it. This parameter is optional and can be <b>NULL</b>.</p>
</dd>
</dl>

## -returns
<p><b>CmCallbackGetKeyObjectID</b> returns STATUS_SUCCESS if the operation succeeds. Possible error return values include the following status code.</p><dl>
<dt><b>STATUS_INVALID_PARAMETER</b></dt>
</dl><p>The <i>Cookie</i> or <i>Object</i> parameter is invalid.</p>

<p> </p>

## -remarks
<p>The <b>CmCallbackGetKeyObjectID</b> routine is available starting with Windows Vista. An improved version of this routine, <a href="https://msdn.microsoft.com/library/windows/hardware/jj215789">CmCallbackGetKeyObjectIDEx</a>, is available starting with Windows 8. Drivers that run only in Windows 8 and later versions of Windows should call <b>CmCallbackGetKeyObjectIDEx</b> instead of <b>CmCallbackGetKeyObjectID</b>.</p>

<p>Drivers can use <b>CmCallbackGetKeyObjectID</b> to obtain the registry key identifier, the object name, or both, by supplying non-<b>NULL</b> values for the <i>ObjectID</i> or <i>ObjectName</i> parameters.</p>

<p>After the driver has obtained the identifier or name, the identifier or name is valid until the driver's <i>RegistryCallback</i> routine receives pre-notification of handle closure.</p>

<p>The driver must not modify the object name.</p>

<p>If two registry key objects represent the same registry key, the key identifiers for both objects are identical.</p>

<p>For more information about <b>CmCallbackGetKeyObjectID</b> and registry filtering operations, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff545879">Filtering Registry Calls</a>.</p>

<p>The <b>CmCallbackGetKeyObjectID</b> routine is available starting with Windows Vista. An improved version of this routine, <a href="https://msdn.microsoft.com/library/windows/hardware/jj215789">CmCallbackGetKeyObjectIDEx</a>, is available starting with Windows 8. Drivers that run only in Windows 8 and later versions of Windows should call <b>CmCallbackGetKeyObjectIDEx</b> instead of <b>CmCallbackGetKeyObjectID</b>.</p>

<p>Drivers can use <b>CmCallbackGetKeyObjectID</b> to obtain the registry key identifier, the object name, or both, by supplying non-<b>NULL</b> values for the <i>ObjectID</i> or <i>ObjectName</i> parameters.</p>

<p>After the driver has obtained the identifier or name, the identifier or name is valid until the driver's <i>RegistryCallback</i> routine receives pre-notification of handle closure.</p>

<p>The driver must not modify the object name.</p>

<p>If two registry key objects represent the same registry key, the key identifiers for both objects are identical.</p>

<p>For more information about <b>CmCallbackGetKeyObjectID</b> and registry filtering operations, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff545879">Filtering Registry Calls</a>.</p>

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
<p>Available starting with Windows Vista.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdm.h (include Wdm.h, Ntddk.h, or Ntifs.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>NtosKrnl.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>NtosKrnl.exe</dt>
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
<a href="https://msdn.microsoft.com/library/windows/hardware/jj215789">CmCallbackGetKeyObjectIDEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541918">CmRegisterCallback</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541921">CmRegisterCallbackEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff560903">RegistryCallback</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564879">UNICODE_STRING</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20CmCallbackGetKeyObjectID routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>