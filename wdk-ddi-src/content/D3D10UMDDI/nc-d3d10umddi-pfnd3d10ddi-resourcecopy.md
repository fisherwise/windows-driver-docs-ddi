---
UID: NC.d3d10umddi.PFND3D10DDI_RESOURCECOPY
title: PFND3D10DDI_RESOURCECOPY
author: windows-driver-content
description: The ResourceCopy function copies an entire source resource to a destination resource.
old-location: display\resourcecopy.htm
ms.assetid: 9a837f42-0bea-4425-b693-dd7947ac24b1
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: display
req.header: d3d10umddi.h
req.include-header: D3d10umddi.h
req.target-type: Desktop
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: ResourceCopy
req.alt-loc: d3d10umddi.h
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

# PFND3D10DDI_RESOURCECOPY callback



## -description
<p>The <i>ResourceCopy</i> function copies an entire source resource to a destination resource.</p>


## -prototype

````
PFND3D10DDI_RESOURCECOPY ResourceCopy;

VOID APIENTRY ResourceCopy(
  _In_ D3D10DDI_HDEVICE   hDevice,
  _In_ D3D10DDI_HRESOURCE hDstResource,
  _In_ D3D10DDI_HRESOURCE hSrcResource
)
{ ... }
````


## -parameters
<dl>

### -param <i>hDevice</i> [in]

<dd>
<p> A handle to the display device (graphics context).</p>
</dd>

### -param <i>hDstResource</i> [in]

<dd>
<p> A handle to the destination resource to copy to.</p>
</dd>

### -param <i>hSrcResource</i> [in]

<dd>
<p> A handle to the source resource to copy from.</p>
</dd>
</dl>

## -returns
<p>None</p>

<p>The driver can use the <a href="https://msdn.microsoft.com/968b04a7-8869-410c-a6fc-83d57726858f">pfnSetErrorCb</a> callback function to set an error code. For more information about setting error codes, see the Remarks section.</p>

## -remarks
<p>The Microsoft Direct3D runtime calls the user-mode display driver's <i>ResourceCopy</i> function to inform the driver to copy from the specified source resource to the specified destination resource. The source and destination resources cannot be the same resource. Both source and destination resources must be the same type of resource and have the same dimensions. The format types (DXGI_FORMAT-typed values) of both resources must be castable to each other. The source and the destination resource must not be currently mapped. In addition, the resource creation flags restrict whether the resource can participate in the copy operation. </p>

<p>The driver should not encounter any error, except for D3DDDIERR_DEVICEREMOVED. Therefore, if the driver passes any error, except for D3DDDIERR_DEVICEREMOVED, in a call to the <a href="https://msdn.microsoft.com/968b04a7-8869-410c-a6fc-83d57726858f">pfnSetErrorCb</a> function, the Direct3D runtime will determine that the error is critical. Even if the device was removed, the driver is not required to return D3DDDIERR_DEVICEREMOVED; however, if device removal interfered with the operation of <i>ResourceCopy</i> (which typically should not happen), the driver can return D3DDDIERR_DEVICEREMOVED.</p>

<p>The driver can implement a <i>ResourceCopy</i> function that can contain a <b>switch</b> statement to process copying and conversion. That is, the driver can implement one <i>ResourceCopy</i> and can set the <b>pfnResourceConvert</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff541873">D3D10_1DDI_DEVICEFUNCS</a> structure to point to <i>ResourceCopy</i> along with the <b>pfnResourceCopy</b> member of D3D10_1DDI_DEVICEFUNCS. However, to improve performance, the driver can implement separate <i>ResourceCopy</i> and <i>ResourceConvert</i> functions.</p>

<p>The Direct3D 10.1 version  of <i>ResourceCopy</i> has a major functionality difference from the Direct3D 10.0 version in regard to the <b>ResourceDimension</b> member of <a href="https://msdn.microsoft.com/library/windows/hardware/ff541697">D3D10DDIARG_CREATERESOURCE</a> for the source and destination resources that were created in calls to the driver's <a href="https://msdn.microsoft.com/c21839f0-8302-49f9-a2b4-4009fbd2d88c">CreateResource(D3D10)</a> function. For the Direct3D 10.0 version  of <i>ResourceCopy</i>, the <b>ResourceDimension</b> member of D3D10DDIARG_CREATERESOURCE for the source and destination resources must match. The Direct3D 10.1 version of <i>ResourceCopy</i> allows a slight relaxation for the <b>ResourceDimension</b> member of D3D10DDIARG_CREATERESOURCE for the source and destination resources. The Direct3D 10.1 version of <i>ResourceCopy</i> allows for the copying of Tex2D source resources on TexCube destination resources or TexCube source resources on Tex2D destination resources. In addition, the distinction between TexCube at the resource level is gone in Direct3D version 10.1. The Direct3D 10.1 version of <i>ResourceCopy</i> only represents whether it can copy a TexCube. In Direct3D version 10.0, copying a resource, validation of a multiple render target, and so on (that is, various operations that required the resource type to be identical) all included the distinction of TexCube to factor into the resource type. In Direct3D version 10.1, the runtime can determine only Tex2D.</p>

<p>The following sections list conditions for copying and converting:</p>

<p><b>Copying</b></p>

<p>For copying, <i>ResourceCopy</i> ensures that the source and destination resources were created through the driver's <a href="https://msdn.microsoft.com/c21839f0-8302-49f9-a2b4-4009fbd2d88c">CreateResource(D3D10)</a> function with the following conditions: </p>

<p>The destination resource was not created with the D3D10_DDI_USAGE_IMMUTABLE value set in the <b>Usage</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff541697">D3D10DDIARG_CREATERESOURCE</a> structure. </p>

<p>The source and destination resources were created with the same resource type and dimensionality (buffer, one-dimensional (1-D) texture, and so on) by setting the same value in the <b>ResourceDimension</b> member of D3D10DDIARG_CREATERESOURCE.</p>

<p>The source and destination resources are not part of the exact same resource. </p>

<p>Each source and destination resource format that is specified in the <b>Format</b> member of D3D10DDIARG_CREATERESOURCE is in the same typeless group. </p>

<p>The source and destination resources must have the same number of samples and quality levels; except for single-sampled resources, which must only have the same number of samples. </p>

<p><i>ResourceCopy</i> does not ensure that no subresources are currently mapped. </p>

<p><b>Converting</b></p>

<p>For conversion, <i>ResourceCopy</i> ensures that the source and destination resources were created through the driver's <a href="https://msdn.microsoft.com/c21839f0-8302-49f9-a2b4-4009fbd2d88c">CreateResource(D3D10)</a> function with the following conditions:</p>

<p>The destination resource was not created with the D3D10_DDI_USAGE_IMMUTABLE value set in the <b>Usage</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff541697">D3D10DDIARG_CREATERESOURCE</a> structure. </p>

<p>The source and destination resources were created with the same resource type (buffer, one-dimensional (1-D) texture, and so on) by setting the same value in the <b>ResourceDimension</b> member of D3D10DDIARG_CREATERESOURCE.</p>

<p>The dimensions of the source and destination resources match up for conversion. </p>

<p>The source and destination resources are not part of the exact same resource. </p>

<p>Each source and destination resource format that is specified in the <b>Format</b> member of D3D10DDIARG_CREATERESOURCE supports the appropriate conversion operation. For mipped-block compressed resources, the dimensions are all validated to be a power of two. </p>

<p>The source and destination resources must have the same number of samples and quality levels; except for single-sampled resources, which must only have the same number of samples. </p>

<p><i>ResourceCopy</i> does not ensure that no subresources are currently mapped. </p>

<p>The Microsoft Direct3D runtime calls the user-mode display driver's <i>ResourceCopy</i> function to inform the driver to copy from the specified source resource to the specified destination resource. The source and destination resources cannot be the same resource. Both source and destination resources must be the same type of resource and have the same dimensions. The format types (DXGI_FORMAT-typed values) of both resources must be castable to each other. The source and the destination resource must not be currently mapped. In addition, the resource creation flags restrict whether the resource can participate in the copy operation. </p>

<p>The driver should not encounter any error, except for D3DDDIERR_DEVICEREMOVED. Therefore, if the driver passes any error, except for D3DDDIERR_DEVICEREMOVED, in a call to the <a href="https://msdn.microsoft.com/968b04a7-8869-410c-a6fc-83d57726858f">pfnSetErrorCb</a> function, the Direct3D runtime will determine that the error is critical. Even if the device was removed, the driver is not required to return D3DDDIERR_DEVICEREMOVED; however, if device removal interfered with the operation of <i>ResourceCopy</i> (which typically should not happen), the driver can return D3DDDIERR_DEVICEREMOVED.</p>

<p>The driver can implement a <i>ResourceCopy</i> function that can contain a <b>switch</b> statement to process copying and conversion. That is, the driver can implement one <i>ResourceCopy</i> and can set the <b>pfnResourceConvert</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff541873">D3D10_1DDI_DEVICEFUNCS</a> structure to point to <i>ResourceCopy</i> along with the <b>pfnResourceCopy</b> member of D3D10_1DDI_DEVICEFUNCS. However, to improve performance, the driver can implement separate <i>ResourceCopy</i> and <i>ResourceConvert</i> functions.</p>

<p>The Direct3D 10.1 version  of <i>ResourceCopy</i> has a major functionality difference from the Direct3D 10.0 version in regard to the <b>ResourceDimension</b> member of <a href="https://msdn.microsoft.com/library/windows/hardware/ff541697">D3D10DDIARG_CREATERESOURCE</a> for the source and destination resources that were created in calls to the driver's <a href="https://msdn.microsoft.com/c21839f0-8302-49f9-a2b4-4009fbd2d88c">CreateResource(D3D10)</a> function. For the Direct3D 10.0 version  of <i>ResourceCopy</i>, the <b>ResourceDimension</b> member of D3D10DDIARG_CREATERESOURCE for the source and destination resources must match. The Direct3D 10.1 version of <i>ResourceCopy</i> allows a slight relaxation for the <b>ResourceDimension</b> member of D3D10DDIARG_CREATERESOURCE for the source and destination resources. The Direct3D 10.1 version of <i>ResourceCopy</i> allows for the copying of Tex2D source resources on TexCube destination resources or TexCube source resources on Tex2D destination resources. In addition, the distinction between TexCube at the resource level is gone in Direct3D version 10.1. The Direct3D 10.1 version of <i>ResourceCopy</i> only represents whether it can copy a TexCube. In Direct3D version 10.0, copying a resource, validation of a multiple render target, and so on (that is, various operations that required the resource type to be identical) all included the distinction of TexCube to factor into the resource type. In Direct3D version 10.1, the runtime can determine only Tex2D.</p>

<p>The following sections list conditions for copying and converting:</p>

<p><b>Copying</b></p>

<p>For copying, <i>ResourceCopy</i> ensures that the source and destination resources were created through the driver's <a href="https://msdn.microsoft.com/c21839f0-8302-49f9-a2b4-4009fbd2d88c">CreateResource(D3D10)</a> function with the following conditions: </p>

<p>The destination resource was not created with the D3D10_DDI_USAGE_IMMUTABLE value set in the <b>Usage</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff541697">D3D10DDIARG_CREATERESOURCE</a> structure. </p>

<p>The source and destination resources were created with the same resource type and dimensionality (buffer, one-dimensional (1-D) texture, and so on) by setting the same value in the <b>ResourceDimension</b> member of D3D10DDIARG_CREATERESOURCE.</p>

<p>The source and destination resources are not part of the exact same resource. </p>

<p>Each source and destination resource format that is specified in the <b>Format</b> member of D3D10DDIARG_CREATERESOURCE is in the same typeless group. </p>

<p>The source and destination resources must have the same number of samples and quality levels; except for single-sampled resources, which must only have the same number of samples. </p>

<p><i>ResourceCopy</i> does not ensure that no subresources are currently mapped. </p>

<p><b>Converting</b></p>

<p>For conversion, <i>ResourceCopy</i> ensures that the source and destination resources were created through the driver's <a href="https://msdn.microsoft.com/c21839f0-8302-49f9-a2b4-4009fbd2d88c">CreateResource(D3D10)</a> function with the following conditions:</p>

<p>The destination resource was not created with the D3D10_DDI_USAGE_IMMUTABLE value set in the <b>Usage</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff541697">D3D10DDIARG_CREATERESOURCE</a> structure. </p>

<p>The source and destination resources were created with the same resource type (buffer, one-dimensional (1-D) texture, and so on) by setting the same value in the <b>ResourceDimension</b> member of D3D10DDIARG_CREATERESOURCE.</p>

<p>The dimensions of the source and destination resources match up for conversion. </p>

<p>The source and destination resources are not part of the exact same resource. </p>

<p>Each source and destination resource format that is specified in the <b>Format</b> member of D3D10DDIARG_CREATERESOURCE supports the appropriate conversion operation. For mipped-block compressed resources, the dimensions are all validated to be a power of two. </p>

<p>The source and destination resources must have the same number of samples and quality levels; except for single-sampled resources, which must only have the same number of samples. </p>

<p><i>ResourceCopy</i> does not ensure that no subresources are currently mapped. </p>

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
<p>Version</p>
</th>
<td width="70%">
<p>Available in Windows Vista and later versions of the Windows operating systems.</p>
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
<a href="https://msdn.microsoft.com/c21839f0-8302-49f9-a2b4-4009fbd2d88c">CreateResource(D3D10)</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541697">D3D10DDIARG_CREATERESOURCE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541833">D3D10DDI_DEVICEFUNCS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541873">D3D10_1DDI_DEVICEFUNCS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/968b04a7-8869-410c-a6fc-83d57726858f">pfnSetErrorCb</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20PFND3D10DDI_RESOURCECOPY callback function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>