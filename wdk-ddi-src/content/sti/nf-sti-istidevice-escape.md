---
UID: NF.sti.IStiDevice.Escape
title: IStiDevice::Escape
author: windows-driver-content
description: The IStiDevice::Escape method sends a request for a vendor-specific I/O operation to a still image device.
old-location: image\istidevice_escape.htm
ms.assetid: ca2aae12-b4b8-4bae-bc3b-812a1ae539c0
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
req.alt-api: IStiDevice.Escape
req.alt-loc: sti.h
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
ms.keywords: IStiDevice, Escape, IStiDevice::Escape
req.iface: IStiDevice
req.product: Windows 10 or later.
---

# IStiDevice::Escape method



## -description
<p>The <b>IStiDevice::Escape</b> method sends a request for a vendor-specific I/O operation to a still image device.</p>


## -syntax

````
HRESULT Escape(
  [in]      STI_RAW_CONTROL_CODE EscapeFunction,
  [in]      LPVOID               lpInData,
            DWORD                cbInDataSize,
  [in, out] LPVOID               pOutData,
            DWORD                dwOutDataSize,
  [out]     LPDWORD              pdwActualData
);
````


## -parameters
<dl>

### -param <i>EscapeFunction</i> [in]

<dd>
<p>Caller-supplied, vendor-defined, DWORD-sized value representing an I/O operation. The device's minidriver must recognize this value and must export an <b>IStiUSD</b> interface. Vendor-defined values must be greater than STI_RAW_RESERVED, which is defined in <i>Sti.h</i>.</p>
</dd>

### -param <i>lpInData</i> [in]

<dd>
<p>Caller-supplied pointer to a buffer containing data to be sent to the device.</p>
</dd>

### -param <i>cbInDataSize</i> 

<dd>
<p>Caller-supplied length, in bytes, of the data contained in the buffer pointed to by <i>lpInData</i>.</p>
</dd>

### -param <i>pOutData</i> [in, out]

<dd>
<p>Caller-supplied pointer to a memory buffer to receive data from the device.</p>
</dd>

### -param <i>dwOutDataSize</i> 

<dd>
<p>Caller-supplied length, in bytes, of the buffer pointed to by <i>lpOutData</i>.</p>
</dd>

### -param <i>pdwActualData</i> [out]

<dd>
<p>Receives the number of bytes actually written to <i>pOutData</i>.</p>
</dd>
</dl>

## -returns
<p>If the operation succeeds, the method returns S_OK. Otherwise, it returns one of the STIERR-prefixed error codes defined in <i>stierr.h</i>.</p>

## -remarks
<p>The <b>IStiDevice::Escape</b> method calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff543815">IStiUSD::Escape</a>, which is exported by vendor-supplied minidrivers. The device's minidriver defines the Method parameter usage.</p>

<p>Before calling <b>IStiDevice::Escape</b>, clients of the <b>IStiDevice</b> COM interface must call <a href="https://msdn.microsoft.com/library/windows/hardware/ff543778">IStillImage::CreateDevice</a> to obtain an <b>IStiDevice</b> interface pointer, which provides access to a specified device.</p>

<p>A call to <b>IStiDevice::Escape</b> must be preceded by a call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff543756">IStiDevice::LockDevice</a> and followed by a call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff543770">IStiDevice::UnLockDevice</a>.</p>

<p>The <b>IStiDevice::Escape</b> method calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff543815">IStiUSD::Escape</a>, which is exported by vendor-supplied minidrivers. The device's minidriver defines the Method parameter usage.</p>

<p>Before calling <b>IStiDevice::Escape</b>, clients of the <b>IStiDevice</b> COM interface must call <a href="https://msdn.microsoft.com/library/windows/hardware/ff543778">IStillImage::CreateDevice</a> to obtain an <b>IStiDevice</b> interface pointer, which provides access to a specified device.</p>

<p>A call to <b>IStiDevice::Escape</b> must be preceded by a call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff543756">IStiDevice::LockDevice</a> and followed by a call to <a href="https://msdn.microsoft.com/library/windows/hardware/ff543770">IStiDevice::UnLockDevice</a>.</p>

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