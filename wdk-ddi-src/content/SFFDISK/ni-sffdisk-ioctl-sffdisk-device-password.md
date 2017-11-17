---
UID: NI.sffdisk.IOCTL_SFFDISK_DEVICE_PASSWORD
title: IOCTL_SFFDISK_DEVICE_PASSWORD
author: windows-driver-content
description: User-mode applications use this IOCTL to perform basic operations on a Secure Digital (SD) card, such as setting the password on the card, resetting the card, or locking and unlocking the card.
old-location: sd\ioctl_sffdisk_device_password.htm
ms.assetid: 76b65ada-06b8-411e-83e9-62088f697f02
ms.author: windowsdriverdev
ms.date: 10/23/2017
ms.topic: ioctl
ms.prod: windows-hardware
ms.technology: SD
req.header: sffdisk.h
req.include-header: Sffdisk.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IOCTL_SFFDISK_DEVICE_PASSWORD
req.alt-loc: sffdisk.h
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
ms.keywords: SERCX2_SYSTEM_DMA_TRANSMIT_CONFIG_INIT
req.iface: 
req.product: Windows 10 or later.
---

# IOCTL_SFFDISK_DEVICE_PASSWORD IOCTL



## -description
<p>User-mode applications use this IOCTL to perform basic operations on a Secure Digital (SD) card, such as setting the password on the card, resetting the card, or locking and unlocking the card. For a description of this command, see the <i>Secure Digital I/O (SDIO)</i> specification.</p>
<p>To perform this operation, call the <a href="base.deviceiocontrol">DeviceIoControl</a> function (described in the Microsoft Windows SDK documentation) using the following parameters.</p>


## -syntax

````
bRet = DeviceIoControl (
    (HANDLE)  hDevice, 
    (DWORD)  dwIoControlCode, 
    (PUCHAR)  lpInBuffer,
    (DWORD)  nInBufferSize, 
    (PUCHAR)  lpOutBuffer,
    (DWORD)  nOutBufferSize, 
    (LPDWORD)  lpBytesReturned,
    (LPOVERLAPPED)  lpOverlapped 
  );
````


## -ioctlparameters

### -input-buffer

<text></text>

### -input-buffer-length

<text></text>

### -output-buffer

<text></text>

### -output-buffer-length

<text></text>

### -in-out-buffer

<text></text>

### -inout-buffer-length

<text></text>

### -status-block
I/O Status block
<p>If the operation succeeds, <a href="base.deviceiocontrol">DeviceIoControl</a> returns a nonzero value.</p>

<p>If the operation fails, <a href="base.deviceiocontrol">DeviceIoControl</a> returns zero. To get extended error information, call <b>GetLastError</b>.</p>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Sffdisk.h (include Sffdisk.h)</dt>
</dl>
</td>
</tr>
</table>