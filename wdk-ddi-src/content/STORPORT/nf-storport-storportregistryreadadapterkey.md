---
UID: NF.storport.StorPortRegistryReadAdapterKey
title: StorPortRegistryReadAdapterKey
author: windows-driver-content
description: The StorPortRegistryReadAdapterKey routine is called by the miniport driver to read the hardware or device registry adapter keys located in registry at HKLM/CurrentControlSet/Enum/&lt;Instance path&gt;/DeviceParameters/...
old-location: storage\storportregistryreadadapterkey.htm
ms.assetid: 85D43276-53A1-4CEE-99FE-23ED8BECB316
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: Storage
req.header: storport.h
req.include-header: Storport.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: StorPortRegistryWriteAdapterKey
req.alt-loc: Storport.lib,Storport.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Storport.lib
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: StorPortRegistryReadAdapterKey
req.iface: 
req.product: Windows 10 or later.
---

# StorPortRegistryReadAdapterKey function



## -description
<p>The <b>StorPortRegistryReadAdapterKey</b> routine is called by the miniport driver to read the hardware or device registry adapter keys located in registry at HKLM/CurrentControlSet/Enum/&lt;Instance path&gt;/DeviceParameters/... these keys are read from in the <a href="NULL">INF DDInstall.HW Section</a>.</p>


## -syntax

````
STORPORT_STATUS StorPortRegistryWriteAdapterKey(
  _In_     PVOID  HwDeviceExtension,
  _In_opt_ PCWSTR SubKeyName,
  _In_     PCWSTR ValueName,
  _In_     ULONG  ValueType,
  _Inout_  PVOID  ValueData,
  _Inout_  ULONG  ValueDataLength
);
````


## -parameters
<dl>

### -param <i>HwDeviceExtension</i> [in]

<dd>
<p>A pointer to the hardware device extension. This is a per HBA storage area that the port driver allocates and initializes on behalf of the miniport driver. Miniport drivers usually store HBA-specific information in this extension, such as the state of the HBA and the mapped access ranges for the HBA. This area is available to the miniport driver immediately after the miniport driver calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff567108">StorPortInitialize</a>. The port driver frees this memory when it removes the device. The miniport driver must be running at IRQL PASSIVE_LEVEL when it calls this routine.</p>
</dd>

### -param <i>SubKeyName</i> [in, optional]

<dd>
<p>The miniport subkey.</p>
</dd>

### -param <i>ValueName</i> [in]

<dd>
<p>The name of the Value under the key.</p>
</dd>

### -param <i>ValueType</i> [in]

<dd>
<p>One of the following registry data types.</p>
<table>
<tr>
<th>Type</th>
<th>Meaning</th>
</tr>
<tr>
<td>
<p>REG_SZ</p>
</td>
<td>
<p>Unicode null-terminated string.</p>
</td>
</tr>
<tr>
<td>
<p>REG_EXPAND_SZ</p>
</td>
<td>
<p>Unicode null-terminated string with environment variable references.</p>
</td>
</tr>
<tr>
<td>
<p>REG_BINARY</p>
</td>
<td>
<p>Binary data.</p>
</td>
</tr>
<tr>
<td>
<p>REG_DWORD</p>
</td>
<td>
<p>32-bit double word.</p>
</td>
</tr>
<tr>
<td>
<p>REG_DWORD_LITTLE_ENDIAN</p>
</td>
<td>
<p>32-bit double word with a little-endian format.</p>
</td>
</tr>
<tr>
<td>
<p>REG_DWORD_BIG_ENDIAN</p>
</td>
<td>
<p>32-bit double word with a big-endian format.</p>
</td>
</tr>
<tr>
<td>
<p>REG_LINK</p>
</td>
<td>
<p>Unicode string that specifies a symbolic link.</p>
</td>
</tr>
<tr>
<td>
<p>REG_MULTI_SZ</p>
</td>
<td>
<p>Multiple Unicode strings.</p>
</td>
</tr>
<tr>
<td>
<p>REG_RESOURCE_LIST</p>
</td>
<td>
<p>Resource list in the resource map.</p>
</td>
</tr>
<tr>
<td>
<p>REG_FULL_RESOURCE_DESCRIPTOR</p>
</td>
<td>
<p>Resource list in the hardware description.</p>
</td>
</tr>
<tr>
<td>
<p>REG_RESOURCE_REQUIREMENTS_LIST</p>
</td>
<td>
<p>Resource requirement list.</p>
</td>
</tr>
<tr>
<td>
<p>REG_QWORD</p>
</td>
<td>
<p>64-bit quadlet number.</p>
</td>
</tr>
<tr>
<td>
<p>REG_QWORD_LITTLE_ENDIAN</p>
</td>
<td>
<p>64-bit quadlet number with a little-endian format.</p>
</td>
</tr>
</table>
<p> </p>
</dd>

### -param <i>ValueData</i> [in, out]

<dd>
<p>Pointer to a the data that contains the registry data to be read. The data is converted from UNICODE to a NULL-terminated ASCII string.</p>
</dd>

### -param <i>ValueDataLength</i> [in, out]

<dd>
<p>Specifies the size of the data pointed to by <i>ValueData</i>.</p>
</dd>
</dl>

## -returns
<p>
            Returns STOR_STATUS_SUCCESS when the operation is successful, otherwise the appropriate error code.</p>

## -remarks


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
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Storport.h (include Storport.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Storport.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>PASSIVE_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567108">StorPortInitialize</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20StorPortRegistryReadAdapterKey routine%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>