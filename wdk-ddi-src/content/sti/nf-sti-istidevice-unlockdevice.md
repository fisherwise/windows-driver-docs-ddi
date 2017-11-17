---
UID: NF.sti.IStiDevice.UnLockDevice
title: IStiDevice::UnLockDevice
author: windows-driver-content
description: The IStiDevice::UnLockDevice method unlocks a device that was locked by a previous call to IStiDevice::LockDevice.
old-location: image\istidevice_unlockdevice.htm
ms.assetid: 0bcd48c6-be8a-47af-9e34-a06ce572925c
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: image
req.header: sti.h
req.include-header: Sti.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IStiDevice.UnLockDevice
req.alt-loc: Sti.h
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
ms.keywords: IStiDevice, UnLockDevice, IStiDevice::UnLockDevice
req.iface: IStiDevice
req.product: Windows 10 or later.
---

# IStiDevice::UnLockDevice method



## -description
<p>The <b>IStiDevice::UnLockDevice</b> method unlocks a device that was locked by a previous call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff543756">IStiDevice::LockDevice</a>.</p>


## -syntax

````
HRESULT UnLockDevice();
````


## -parameters


## -returns
<p>If the operation succeeds, the method returns S_OK. Otherwise, it returns one of the STIERR-prefixed error codes defined in <i>stierr.h</i>.</p>

<p>If the operation succeeds, the method returns S_OK. Otherwise, it returns one of the STIERR-prefixed error codes defined in <i>stierr.h</i>.</p>

<p>If the operation succeeds, the method returns S_OK. Otherwise, it returns one of the STIERR-prefixed error codes defined in <i>stierr.h</i>.</p>

## -remarks
<p>Before the <b>IStiDevice::UnLockDevice</b> method releases the <b>IStiDevice</b>-level lock on the device, it calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff543843">IStiUSD::UnLockDevice</a> in the appropriate vendor-supplied minidriver.</p>

<p>Before calling <b>IStiDevice::UnLockDevice</b>, clients of the <b>IStiDevice</b> COM interface must call <a href="https://msdn.microsoft.com/library/windows/hardware/ff543778">IStillImage::CreateDevice</a> to obtain an <b>IStiDevice</b> interface pointer, which provides access to a specified device.</p>

<p>Before the <b>IStiDevice::UnLockDevice</b> method releases the <b>IStiDevice</b>-level lock on the device, it calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff543843">IStiUSD::UnLockDevice</a> in the appropriate vendor-supplied minidriver.</p>

<p>Before calling <b>IStiDevice::UnLockDevice</b>, clients of the <b>IStiDevice</b> COM interface must call <a href="https://msdn.microsoft.com/library/windows/hardware/ff543778">IStillImage::CreateDevice</a> to obtain an <b>IStiDevice</b> interface pointer, which provides access to a specified device.</p>

<p>Before the <b>IStiDevice::UnLockDevice</b> method releases the <b>IStiDevice</b>-level lock on the device, it calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff543843">IStiUSD::UnLockDevice</a> in the appropriate vendor-supplied minidriver.</p>

<p>Before calling <b>IStiDevice::UnLockDevice</b>, clients of the <b>IStiDevice</b> COM interface must call <a href="https://msdn.microsoft.com/library/windows/hardware/ff543778">IStillImage::CreateDevice</a> to obtain an <b>IStiDevice</b> interface pointer, which provides access to a specified device.</p>

<p>Before the <b>IStiDevice::UnLockDevice</b> method releases the <b>IStiDevice</b>-level lock on the device, it calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff543843">IStiUSD::UnLockDevice</a> in the appropriate vendor-supplied minidriver.</p>

<p>Before calling <b>IStiDevice::UnLockDevice</b>, clients of the <b>IStiDevice</b> COM interface must call <a href="https://msdn.microsoft.com/library/windows/hardware/ff543778">IStillImage::CreateDevice</a> to obtain an <b>IStiDevice</b> interface pointer, which provides access to a specified device.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt>Desktop</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Sti.h (include Sti.h)</dt>
</dl>
</td>
</tr>
</table>