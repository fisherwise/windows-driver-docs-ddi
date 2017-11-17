---
UID: NC.d3d10umddi.PFND3D11_1DDI_SETCONSTANTBUFFERS
title: PFND3D11_1DDI_SETCONSTANTBUFFERS
author: windows-driver-content
description: Sets constant buffers for a compute shader.
old-location: display\cssetconstantbuffers_d3d11_1_.htm
ms.assetid: 6A2B50BF-415D-47BB-9514-B15F717A76EA
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: display
req.header: d3d10umddi.h
req.include-header: D3d10umddi.h
req.target-type: Desktop
req.target-min-winverclnt: Windows 8
req.target-min-winversvr: Windows Server 2012
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: CsSetConstantBuffers(D3D11_1)
req.alt-loc: D3d10umddi.h
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
ms.keywords: SETRESULT_INFO, SETRESULT_INFO, *PSETRESULT_INFO
req.iface: 
---

# PFND3D11_1DDI_SETCONSTANTBUFFERS callback



## -description
<p>Sets constant buffers for a compute shader.</p>


## -prototype

````
PFND3D11_1DDI_SETCONSTANTBUFFERS CsSetConstantBuffers(D3D11_1);

VOID APIENTRY* CsSetConstantBuffers(D3D11_1)(
  _In_           D3D10DDI_HDEVICE   hDevice,
  _In_           UINT               StartBuffer,
  _In_           UINT               NumBuffers,
  _In_     const D3D10DDI_HRESOURCE *phBuffers,
  _In_opt_ const UINT               *pFirstConstant,
  _In_opt_ const UINT               *pNumConstants
)
{ ... }
````


## -parameters
<dl>

### -param <i>hDevice</i> [in]

<dd>
<p> A handle to the display device (graphics context).</p>
</dd>

### -param <i>StartBuffer</i> [in]

<dd>
<p> The starting constant buffer to set. </p>
</dd>

### -param <i>NumBuffers</i> [in]

<dd>
<p> The total number of buffers to set. </p>
</dd>

### -param <i>phBuffers</i> [in]

<dd>
<p> An array of handles to the constant buffers, beginning with the buffer that <i>StartBuffer</i> specifies.</p>
</dd>

### -param <i>pFirstConstant</i> [in, optional]

<dd>
<p>A pointer to the first constant in the buffer pointed to by <i>StartBuffer</i>.</p>
</dd>

### -param <i>pNumConstants</i> [in, optional]

<dd>
<p>The number of constants in the  buffer pointed to by  <i>StartBuffer</i>.</p>
</dd>
</dl>

## -returns
<p>None</p>

<p>The driver can use the <a href="https://msdn.microsoft.com/968b04a7-8869-410c-a6fc-83d57726858f">pfnSetErrorCb</a> callback function to set an error code. For more information about setting error codes, see the following Remarks section.</p>

## -remarks
<p>Buffers that this function specifies are created with the D3D10_BIND_CONSTANT_BUFFER flag. </p>

<p>The driver should not encounter any error, except for D3DDDIERR_DEVICEREMOVED. Therefore, if the driver passes any error, except for D3DDDIERR_DEVICEREMOVED, in a call to the <a href="https://msdn.microsoft.com/968b04a7-8869-410c-a6fc-83d57726858f">pfnSetErrorCb</a> function, the Direct3D runtime determines that the error is critical. Even if the device is removed, the driver is not required to return D3DDDIERR_DEVICEREMOVED; however, if device removal interferes with the operation of this function (which typically should not happen), the driver can return D3DDDIERR_DEVICEREMOVED.</p>

<p>Buffers that this function specifies are created with the D3D10_BIND_CONSTANT_BUFFER flag. </p>

<p>The driver should not encounter any error, except for D3DDDIERR_DEVICEREMOVED. Therefore, if the driver passes any error, except for D3DDDIERR_DEVICEREMOVED, in a call to the <a href="https://msdn.microsoft.com/968b04a7-8869-410c-a6fc-83d57726858f">pfnSetErrorCb</a> function, the Direct3D runtime determines that the error is critical. Even if the device is removed, the driver is not required to return D3DDDIERR_DEVICEREMOVED; however, if device removal interferes with the operation of this function (which typically should not happen), the driver can return D3DDDIERR_DEVICEREMOVED.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 8</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>Windows Server 2012</p>
</td>
</tr>
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
<dt>D3d10umddi.h (include D3d10umddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh406443">D3D11_1DDI_DEVICEFUNCS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/968b04a7-8869-410c-a6fc-83d57726858f">pfnSetErrorCb</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20PFND3D11_1DDI_SETCONSTANTBUFFERS callback function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>