---
UID: NC.d3d10umddi.PFND3D11_1DDI_CREATEVIDEOPROCESSOROUTPUTVIEW
title: PFND3D11_1DDI_CREATEVIDEOPROCESSOROUTPUTVIEW
author: windows-driver-content
description: Creates a resource view for a video processor. This view defines the output sample for the video processing operation.
old-location: display\createvideoprocessoroutputview.htm
ms.assetid: 619695dc-8525-4200-a0c2-8ce0fb1010ed
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
req.alt-api: CreateVideoProcessorOutputView
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

# PFND3D11_1DDI_CREATEVIDEOPROCESSOROUTPUTVIEW callback



## -description
<p>Creates a resource view for a video processor. This view defines the output sample for the video processing operation.</p>


## -prototype

````
PFND3D11_1DDI_CREATEVIDEOPROCESSOROUTPUTVIEW CreateVideoProcessorOutputView;

HRESULT APIENTRY* CreateVideoProcessorOutputView(
  _In_       D3D10DDI_HDEVICE                             hDevice,
  _In_ const D3D11_1DDIARG_CREATEVIDEOPROCESSOROUTPUTVIEW *pCreateData,
  _In_       D3D11_1DDI_HVIDEOPROCESSOROUTPUTVIEW         hView,
  _In_       D3D11_1DDI_HRTVIDEOPROCESSOROUTPUTVIEW       hRTView
)
{ ... }
````


## -parameters
<dl>

### -param <i>hDevice</i> [in]

<dd>
<p>A handle to the display device (graphics context).

</p>
</dd>

### -param <i>pCreateData</i> [in]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/hh406320">D3D11_1DDIARG_CREATEVIDEOPROCESSOROUTPUTVIEW</a> structure. This structure specifies the attributes of the video processor output view to be created.</p>
</dd>

### -param <i>hView</i> [in]

<dd>
<p>A handle to the driver's private data for the video processor output view. For more information, see the Remarks section.</p>
</dd>

### -param <i>hRTView</i> [in]

<dd>
<p>A handle to the video processor output view that the driver should use when it calls back into the Direct3D runtime.</p>
</dd>
</dl>

## -returns
<p><i>CreateVideoProcessorOutputView</i> returns one of the following values:</p><dl>
<dt><b>S_OK</b></dt>
</dl><p>The video processor output view was created successfully.</p><dl>
<dt><b>D3DDDIERR_DEVICEREMOVED</b></dt>
</dl><p>The graphics adapter was removed.</p><dl>
<dt><b>E_OUTOFMEMORY</b></dt>
</dl><p>
        Memory was not available to complete the operation.</p>

<p> </p>

## -remarks
<p>The Direct3D runtime calls <i>CreateVideoProcessorOutputView</i> after it has called the driver's <a href="https://msdn.microsoft.com/2cf09e91-e83b-47ae-bf34-037dc01d7e80">CalcPrivateVideoProcessorOutputViewSize</a>   to determine the size in bytes for the private data that the driver requires for the video processor output view. The runtime allocates the memory for this private data for the driver. The driver uses this memory to store private data that is related to the video processor output view.</p>

<p>When the runtime  calls <i>CreateVideoProcessorOutputView</i>, it passes the handle to the private data memory in the <i>hView</i> parameter. This handle is actually a pointer to the memory. </p>

<p>The Direct3D runtime calls <i>CreateVideoProcessorOutputView</i> after it has called the driver's <a href="https://msdn.microsoft.com/2cf09e91-e83b-47ae-bf34-037dc01d7e80">CalcPrivateVideoProcessorOutputViewSize</a>   to determine the size in bytes for the private data that the driver requires for the video processor output view. The runtime allocates the memory for this private data for the driver. The driver uses this memory to store private data that is related to the video processor output view.</p>

<p>When the runtime  calls <i>CreateVideoProcessorOutputView</i>, it passes the handle to the private data memory in the <i>hView</i> parameter. This handle is actually a pointer to the memory. </p>

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
<a href="https://msdn.microsoft.com/2cf09e91-e83b-47ae-bf34-037dc01d7e80">CalcPrivateVideoProcessorOutputViewSize</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh406312">D3D11_1DDIARG_CREATEVIDEODECODEROUTPUTVIEW</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20PFND3D11_1DDI_CREATEVIDEOPROCESSOROUTPUTVIEW callback function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>