---
UID: NF.storport.StorPortFreeDeviceBase
title: StorPortFreeDeviceBase
author: windows-driver-content
description: StorPortFreeDeviceBase frees a range of device I/O memory that was mapped by StorPortGetDeviceBase.
old-location: storage\storportfreedevicebase.htm
ms.assetid: 4feb3bde-c243-493c-a6f9-4accd545955c
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
req.alt-api: StorPortFreeDeviceBase
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
req.irql: 
ms.keywords: StorPortFreeDeviceBase
req.iface: 
req.product: Windows 10 or later.
---

# StorPortFreeDeviceBase function



## -description
<p><b>StorPortFreeDeviceBase</b> frees a range of device I/O memory that was mapped by <a href="https://msdn.microsoft.com/library/windows/hardware/ff567080">StorPortGetDeviceBase</a>.</p>


## -syntax

````
STORPORT_API VOID StorPortFreeDeviceBase(
  _In_ PVOID HwDeviceExtension,
  _In_ PVOID MappedAddress
);
````


## -parameters
<dl>

### -param <i>HwDeviceExtension</i> [in]

<dd>
<p>A pointer to the hardware device extension. This is a per HBA storage area that the port driver allocates and initializes on behalf of the miniport driver. Miniport drivers usually store HBA-specific information in this extension, such as the state of the HBA and the mapped access ranges for the HBA. This area is available to the miniport driver immediately after the miniport driver calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff567108">StorPortInitialize</a>. The port driver frees this memory when it removes the device. </p>
</dd>

### -param <i>MappedAddress</i> [in]

<dd>
<p>Pointer to region of memory to be freed.</p>
</dd>
</dl>

## -returns
<p>None </p>

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
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567080">StorPortGetDeviceBase</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff564623">ScsiPortFreeDeviceBase</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20StorPortFreeDeviceBase function%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>