---
UID: NS.d3d10umddi.D3D10DDI_DEVICEFUNCS~r1
title: D3D10DDI_DEVICEFUNCS
author: windows-driver-content
description: The D3D10DDI_DEVICEFUNCS structure contains functions that the user-mode display driver can implement to render graphics primitives and process state changes.
old-location: display\d3d10ddi_devicefuncs.htm
ms.assetid: 005f4fc0-2b22-47bf-a129-59b2dc4ff052
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3d10umddi.h
req.include-header: D3d10umddi.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3D10DDI_DEVICEFUNCS
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
ms.keywords: D3D10DDI_DEVICEFUNCS, D3D10DDI_DEVICEFUNCS
req.iface: 
---

# D3D10DDI_DEVICEFUNCS structure



## -description
<p>The D3D10DDI_DEVICEFUNCS structure contains functions that the user-mode display driver can implement to render graphics primitives and process state changes.</p>


## -syntax

````
typedef struct D3D10DDI_DEVICEFUNCS {
  PFND3D10DDI_RESOURCEUPDATESUBRESOURCEUP               pfnDefaultConstantBufferUpdateSubresourceUP;
  PFND3D10DDI_SETCONSTANTBUFFERS                        pfnVsSetConstantBuffers;
  PFND3D10DDI_SETSHADERRESOURCES                        pfnPsSetShaderResources;
  PFND3D10DDI_SETSHADER                                 pfnPsSetShader;
  PFND3D10DDI_SETSAMPLERS                               pfnPsSetSamplers;
  PFND3D10DDI_SETSHADER                                 pfnVsSetShader;
  PFND3D10DDI_DRAWINDEXED                               pfnDrawIndexed;
  PFND3D10DDI_DRAW                                      pfnDraw;
  PFND3D10DDI_RESOURCEMAP                               pfnDynamicIABufferMapNoOverwrite;
  PFND3D10DDI_RESOURCEUNMAP                             pfnDynamicIABufferUnmap;
  PFND3D10DDI_RESOURCEMAP                               pfnDynamicConstantBufferMapDiscard;
  PFND3D10DDI_RESOURCEMAP                               pfnDynamicIABufferMapDiscard;
  PFND3D10DDI_RESOURCEUNMAP                             pfnDynamicConstantBufferUnmap;
  PFND3D10DDI_SETCONSTANTBUFFERS                        pfnPsSetConstantBuffers;
  PFND3D10DDI_SETINPUTLAYOUT                            pfnIaSetInputLayout;
  PFND3D10DDI_IA_SETVERTEXBUFFERS                       pfnIaSetVertexBuffers;
  PFND3D10DDI_IA_SETINDEXBUFFER                         pfnIaSetIndexBuffer;
  PFND3D10DDI_DRAWINDEXEDINSTANCED                      pfnDrawIndexedInstanced;
  PFND3D10DDI_DRAWINSTANCED                             pfnDrawInstanced;
  PFND3D10DDI_RESOURCEMAP                               pfnDynamicResourceMapDiscard;
  PFND3D10DDI_RESOURCEUNMAP                             pfnDynamicResourceUnmap;
  PFND3D10DDI_SETCONSTANTBUFFERS                        pfnGsSetConstantBuffers;
  PFND3D10DDI_SETSHADER                                 pfnGsSetShader;
  PFND3D10DDI_IA_SETTOPOLOGY                            pfnIaSetTopology;
  PFND3D10DDI_RESOURCEMAP                               pfnStagingResourceMap;
  PFND3D10DDI_RESOURCEUNMAP                             pfnStagingResourceUnmap;
  PFND3D10DDI_SETSHADERRESOURCES                        pfnVsSetShaderResources;
  PFND3D10DDI_SETSAMPLERS                               pfnVsSetSamplers;
  PFND3D10DDI_SETSHADERRESOURCES                        pfnGsSetShaderResources;
  PFND3D10DDI_SETSAMPLERS                               pfnGsSetSamplers;
  PFND3D10DDI_SETRENDERTARGETS                          pfnSetRenderTargets;
  PFND3D10DDI_SHADERRESOURCEVIEWREADAFTERWRITEHAZARD    pfnShaderResourceViewReadAfterWriteHazard;
  PFND3D10DDI_RESOURCEREADAFTERWRITEHAZARD              pfnResourceReadAfterWriteHazard;
  PFND3D10DDI_SETBLENDSTATE                             pfnSetBlendState;
  PFND3D10DDI_SETDEPTHSTENCILSTATE                      pfnSetDepthStencilState;
  PFND3D10DDI_SETRASTERIZERSTATE                        pfnSetRasterizerState;
  PFND3D10DDI_QUERYEND                                  pfnQueryEnd;
  PFND3D10DDI_QUERYBEGIN                                pfnQueryBegin;
  PFND3D10DDI_RESOURCECOPYREGION                        pfnResourceCopyRegion;
  PFND3D10DDI_RESOURCEUPDATESUBRESOURCEUP               pfnResourceUpdateSubresourceUP;
  PFND3D10DDI_SO_SETTARGETS                             pfnSoSetTargets;
  PFND3D10DDI_DRAWAUTO                                  pfnDrawAuto;
  PFND3D10DDI_SETVIEWPORTS                              pfnSetViewports;
  PFND3D10DDI_SETSCISSORRECTS                           pfnSetScissorRects;
  PFND3D10DDI_CLEARRENDERTARGETVIEW                     pfnClearRenderTargetView;
  PFND3D10DDI_CLEARDEPTHSTENCILVIEW                     pfnClearDepthStencilView;
  PFND3D10DDI_SETPREDICATION                            pfnSetPredication;
  PFND3D10DDI_QUERYGETDATA                              pfnQueryGetData;
  PFND3D10DDI_FLUSH                                     pfnFlush;
  PFND3D10DDI_GENMIPS                                   pfnGenMips;
  PFND3D10DDI_RESOURCECOPY                              pfnResourceCopy;
  PFND3D10DDI_RESOURCERESOLVESUBRESOURCE                pfnResourceResolveSubresource;
  PFND3D10DDI_RESOURCEMAP                               pfnResourceMap;
  PFND3D10DDI_RESOURCEUNMAP                             pfnResourceUnmap;
  PFND3D10DDI_RESOURCEISSTAGINGBUSY                     pfnResourceIsStagingBusy;
  PFND3D10DDI_RELOCATEDEVICEFUNCS                       pfnRelocateDeviceFuncs;
  PFND3D10DDI_CALCPRIVATERESOURCESIZE                   pfnCalcPrivateResourceSize;
  PFND3D10DDI_CALCPRIVATEOPENEDRESOURCESIZE             pfnCalcPrivateOpenedResourceSize;
  PFND3D10DDI_CREATERESOURCE                            pfnCreateResource;
  PFND3D10DDI_OPENRESOURCE                              pfnOpenResource;
  PFND3D10DDI_DESTROYRESOURCE                           pfnDestroyResource;
  PFND3D10DDI_CALCPRIVATESHADERRESOURCEVIEWSIZE         pfnCalcPrivateShaderResourceViewSize;
  PFND3D10DDI_CREATESHADERRESOURCEVIEW                  pfnCreateShaderResourceView;
  PFND3D10DDI_DESTROYSHADERRESOURCEVIEW                 pfnDestroyShaderResourceView;
  PFND3D10DDI_CALCPRIVATERENDERTARGETVIEWSIZE           pfnCalcPrivateRenderTargetViewSize;
  PFND3D10DDI_CREATERENDERTARGETVIEW                    pfnCreateRenderTargetView;
  PFND3D10DDI_DESTROYRENDERTARGETVIEW                   pfnDestroyRenderTargetView;
  PFND3D10DDI_CALCPRIVATEDEPTHSTENCILVIEWSIZE           pfnCalcPrivateDepthStencilViewSize;
  PFND3D10DDI_CREATEDEPTHSTENCILVIEW                    pfnCreateDepthStencilView;
  PFND3D10DDI_DESTROYDEPTHSTENCILVIEW                   pfnDestroyDepthStencilView;
  PFND3D10DDI_CALCPRIVATEELEMENTLAYOUTSIZE              pfnCalcPrivateElementLayoutSize;
  PFND3D10DDI_CREATEELEMENTLAYOUT                       pfnCreateElementLayout;
  PFND3D10DDI_DESTROYELEMENTLAYOUT                      pfnDestroyElementLayout;
  PFND3D10DDI_CALCPRIVATEBLENDSTATESIZE                 pfnCalcPrivateBlendStateSize;
  PFND3D10DDI_CREATEBLENDSTATE                          pfnCreateBlendState;
  PFND3D10DDI_DESTROYBLENDSTATE                         pfnDestroyBlendState;
  PFND3D10DDI_CALCPRIVATEDEPTHSTENCILSTATESIZE          pfnCalcPrivateDepthStencilStateSize;
  PFND3D10DDI_CREATEDEPTHSTENCILSTATE                   pfnCreateDepthStencilState;
  PFND3D10DDI_DESTROYDEPTHSTENCILSTATE                  pfnDestroyDepthStencilState;
  PFND3D10DDI_CALCPRIVATERASTERIZERSTATESIZE            pfnCalcPrivateRasterizerStateSize;
  PFND3D10DDI_CREATERASTERIZERSTATE                     pfnCreateRasterizerState;
  PFND3D10DDI_DESTROYRASTERIZERSTATE                    pfnDestroyRasterizerState;
  PFND3D10DDI_CALCPRIVATESHADERSIZE                     pfnCalcPrivateShaderSize;
  PFND3D10DDI_CREATEVERTEXSHADER                        pfnCreateVertexShader;
  PFND3D10DDI_CREATEGEOMETRYSHADER                      pfnCreateGeometryShader;
  PFND3D10DDI_CREATEPIXELSHADER                         pfnCreatePixelShader;
  PFND3D10DDI_CALCPRIVATEGEOMETRYSHADERWITHSTREAMOUTPUT pfnCalcPrivateGeometryShaderWithStreamOutput;
  PFND3D10DDI_CREATEGEOMETRYSHADERWITHSTREAMOUTPUT      pfnCreateGeometryShaderWithStreamOutput;
  PFND3D10DDI_DESTROYSHADER                             pfnDestroyShader;
  PFND3D10DDI_CALCPRIVATESAMPLERSIZE                    pfnCalcPrivateSamplerSize;
  PFND3D10DDI_CREATESAMPLER                             pfnCreateSampler;
  PFND3D10DDI_DESTROYSAMPLER                            pfnDestroySampler;
  PFND3D10DDI_CALCPRIVATEQUERYSIZE                      pfnCalcPrivateQuerySize;
  PFND3D10DDI_CREATEQUERY                               pfnCreateQuery;
  PFND3D10DDI_DESTROYQUERY                              pfnDestroyQuery;
  PFND3D10DDI_CHECKFORMATSUPPORT                        pfnCheckFormatSupport;
  PFND3D10DDI_CHECKMULTISAMPLEQUALITYLEVELS             pfnCheckMultisampleQualityLevels;
  PFND3D10DDI_CHECKCOUNTERINFO                          pfnCheckCounterInfo;
  PFND3D10DDI_CHECKCOUNTER                              pfnCheckCounter;
  PFND3D10DDI_DESTROYDEVICE                             pfnDestroyDevice;
  PFND3D10DDI_SETTEXTFILTERSIZE                         pfnSetTextFilterSize;
} D3D10DDI_DEVICEFUNCS;
````


## -struct-fields
<dl>

### -field <b>pfnDefaultConstantBufferUpdateSubresourceUP</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/80086f1a-75f8-464f-973e-9c1e67725933">DefaultConstantBufferUpdateSubresourceUP</a> function.</p>
</dd>

### -field <b>pfnVsSetConstantBuffers</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/38a27fa3-905a-4ab7-b018-53ea3c589661">VsSetConstantBuffers</a> function.</p>
</dd>

### -field <b>pfnPsSetShaderResources</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/e30aabdd-52b7-40c0-bb92-50cbabdc5e1f">PsSetShaderResources</a> function.</p>
</dd>

### -field <b>pfnPsSetShader</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/bc6213cd-8e0c-4f10-8942-c42818b512dc">PsSetShader</a> function. </p>
</dd>

### -field <b>pfnPsSetSamplers</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/3c4b36a9-842c-45dd-a261-74b5ceed5b12">PsSetSamplers</a> function.</p>
</dd>

### -field <b>pfnVsSetShader</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/6bcafd44-3503-44f7-8676-c27eda585f9d">VsSetShader</a> function.</p>
</dd>

### -field <b>pfnDrawIndexed</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/d1097bb6-35ac-4069-ae05-b74c75a98e21">DrawIndexed</a> function.</p>
</dd>

### -field <b>pfnDraw</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/7a6f1d56-12be-4185-97bf-06f265ee6fe3">Draw</a> function.</p>
</dd>

### -field <b>pfnDynamicIABufferMapNoOverwrite</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/1310a3f8-02dd-4d35-98ad-4016e57d1eb2">ResourceMap</a> function. For more information about whether to implement a separate <b>DynamicIABufferMapNoOverwrite</b> function or to point to the multipurpose <b>ResourceMap</b>, see the Remarks section of <b>ResourceMap</b>. </p>
</dd>

### -field <b>pfnDynamicIABufferUnmap</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/fb2b714e-232d-40b2-88ad-ee8dcd70a057">ResourceUnmap</a> function. For more information about whether to implement a separate <b>DynamicIABufferUnmap</b> function or to point to the multipurpose <b>ResourceUnmap</b>, see the Remarks section of <a href="https://msdn.microsoft.com/1310a3f8-02dd-4d35-98ad-4016e57d1eb2">ResourceMap</a>. </p>
</dd>

### -field <b>pfnDynamicConstantBufferMapDiscard</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/1310a3f8-02dd-4d35-98ad-4016e57d1eb2">ResourceMap</a> function. For more information about whether to implement a separate <b>DynamicConstantBufferMapDiscard</b> function or to point to the multipurpose <b>ResourceMap</b>, see the Remarks section of <b>ResourceMap</b>. </p>
</dd>

### -field <b>pfnDynamicIABufferMapDiscard</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/1310a3f8-02dd-4d35-98ad-4016e57d1eb2">ResourceMap</a> function. For more information about whether to implement a separate <b>DynamicIABufferMapDiscard</b> function or to point to the multipurpose <b>ResourceMap</b>, see the Remarks section of <b>ResourceMap</b>. </p>
</dd>

### -field <b>pfnDynamicConstantBufferUnmap</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/fb2b714e-232d-40b2-88ad-ee8dcd70a057">ResourceUnmap</a> function. For more information about whether to implement a separate <b>DynamicConstantBufferUnmap</b> function or to point to the multipurpose <b>ResourceUnmap</b>, see the Remarks section of <a href="https://msdn.microsoft.com/1310a3f8-02dd-4d35-98ad-4016e57d1eb2">ResourceMap</a>. </p>
</dd>

### -field <b>pfnPsSetConstantBuffers</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/d77070d8-daf8-44d3-9032-a7a7d3c2c242">PsSetConstantBuffers</a> function.</p>
</dd>

### -field <b>pfnIaSetInputLayout</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/905e4e7f-5bc5-487f-8d82-4ebc2db66135">IaSetInputLayout</a> function.</p>
</dd>

### -field <b>pfnIaSetVertexBuffers</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/3d5a7ea1-08c2-4594-93bc-97b985cd16dc">IaSetVertexBuffers</a> function.</p>
</dd>

### -field <b>pfnIaSetIndexBuffer</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/042ebb72-b794-4cb8-9d81-bd52a785f1e0">IaSetIndexBuffer</a> function.</p>
</dd>

### -field <b>pfnDrawIndexedInstanced</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/3dc64562-9dc0-4d43-835d-6fdd509435f8">DrawIndexedInstanced</a> function.</p>
</dd>

### -field <b>pfnDrawInstanced</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/c539cf8b-e056-476a-9b23-7e360917a7d9">DrawInstanced</a> function.</p>
</dd>

### -field <b>pfnDynamicResourceMapDiscard</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/1310a3f8-02dd-4d35-98ad-4016e57d1eb2">ResourceMap</a> function. For more information about whether to implement a separate <b>DynamicResourceMapDiscard</b> function or to point to the multipurpose <b>ResourceMap</b>, see the Remarks section of <b>ResourceMap</b>. </p>
</dd>

### -field <b>pfnDynamicResourceUnmap</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/fb2b714e-232d-40b2-88ad-ee8dcd70a057">ResourceUnmap</a> function. For more information about whether to implement a separate <b>DynamicResourceUnmap</b> function or to point to the multipurpose <b>ResourceUnmap</b>, see the Remarks section of <b>ResourceUnmap</b>. </p>
</dd>

### -field <b>pfnGsSetConstantBuffers</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/1d13fe21-55bc-46c0-b07e-3c96f671496c">GsSetConstantBuffers</a> function.</p>
</dd>

### -field <b>pfnGsSetShader</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/9f40371d-4a74-4020-af8a-e3781d1bc632">GsSetShader</a> function.</p>
</dd>

### -field <b>pfnIaSetTopology</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/c2ee9c8b-7e33-4fc9-9bd3-2b2984e94390">IaSetTopology</a> function.</p>
</dd>

### -field <b>pfnStagingResourceMap</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/1310a3f8-02dd-4d35-98ad-4016e57d1eb2">ResourceMap</a> function. For more information about whether to implement a separate <b>StagingResourceMap</b> function or to point to the multipurpose <b>ResourceMap</b>, see the Remarks section of <b>ResourceMap</b>. </p>
</dd>

### -field <b>pfnStagingResourceUnmap</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/fb2b714e-232d-40b2-88ad-ee8dcd70a057">ResourceUnmap</a> function. For more information about whether to implement a separate <b>StagingResourceUnmap</b> function or to point to the multipurpose <b>ResourceUnmap</b>, see the Remarks section of <a href="https://msdn.microsoft.com/1310a3f8-02dd-4d35-98ad-4016e57d1eb2">ResourceMap</a>. </p>
</dd>

### -field <b>pfnVsSetShaderResources</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/4d432517-97f0-441f-ac49-0416ac19b319">VsSetShaderResources</a> function.</p>
</dd>

### -field <b>pfnVsSetSamplers</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/3f2c08e2-8372-45a7-9d65-936889f21e27">VsSetSamplers</a> function.</p>
</dd>

### -field <b>pfnGsSetShaderResources</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/b5cd87bb-7a08-444c-9120-d7ab79e512c5">GsSetShaderResources</a> function.</p>
</dd>

### -field <b>pfnGsSetSamplers</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/a70b7b29-99d2-4e7e-aeb3-bf324d71ebaf">GsSetSamplers</a> function.</p>
</dd>

### -field <b>pfnSetRenderTargets</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/852893e6-1f1c-470a-ab72-f52c1e06e0c0">SetRenderTargets</a> function.</p>
</dd>

### -field <b>pfnShaderResourceViewReadAfterWriteHazard</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/bb391154-a9ff-4032-b86e-81fa4ea2e37c">ShaderResourceViewReadAfterWriteHazard</a> function.</p>
</dd>

### -field <b>pfnResourceReadAfterWriteHazard</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/4d7dd4f5-9792-48cb-bf69-3903ac9dda75">ResourceReadAfterWriteHazard</a> function.</p>
</dd>

### -field <b>pfnSetBlendState</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/8794413f-f4d5-4382-8886-2f0659d8a781">SetBlendState</a> function.</p>
</dd>

### -field <b>pfnSetDepthStencilState</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/379f8113-b07c-4984-ba37-a06d6c21b9e9">SetDepthStencilState</a> function.</p>
</dd>

### -field <b>pfnSetRasterizerState</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/8162c9c9-4ebd-45a9-adaf-576f25c3907e">SetRasterizerState</a> function.</p>
</dd>

### -field <b>pfnQueryEnd</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/5a231d7e-7e47-40ad-99d1-82661dec41d0">QueryEnd</a> function.</p>
</dd>

### -field <b>pfnQueryBegin</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/2f0a7462-83a6-47df-b5f6-b3706b875349">QueryBegin</a> function.</p>
</dd>

### -field <b>pfnResourceCopyRegion</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/e782dc8c-e34e-4f96-b6d9-c34d7843ed05">ResourceCopyRegion</a> function.</p>
</dd>

### -field <b>pfnResourceUpdateSubresourceUP</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/3b6177f4-43a1-4461-abfc-5c463b0ba612">ResourceUpdateSubresourceUP</a> function.</p>
</dd>

### -field <b>pfnSoSetTargets</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/96f1c439-7323-456e-8c9c-793d8e0973d9">SoSetTargets</a> function.</p>
</dd>

### -field <b>pfnDrawAuto</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/83d96dc0-dfd4-449e-9e14-18f354d44534">DrawAuto</a> function.</p>
</dd>

### -field <b>pfnSetViewports</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/f5a55dd3-a8c4-4741-b99e-105021d79603">SetViewports</a> function.</p>
</dd>

### -field <b>pfnSetScissorRects</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/ef61f50b-a82b-43df-865f-2f9d9ca906d4">SetScissorRects</a> function.</p>
</dd>

### -field <b>pfnClearRenderTargetView</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/9dc95dd2-01ad-45d7-9e75-049026b25968">ClearRenderTargetView</a> function.</p>
</dd>

### -field <b>pfnClearDepthStencilView</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/0474c154-1bec-4602-880c-ffdc48c738f0">ClearDepthStencilView</a> function.</p>
</dd>

### -field <b>pfnSetPredication</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/df671478-859f-4ccd-9ab4-1986f9af10cf">SetPredication</a> function.</p>
</dd>

### -field <b>pfnQueryGetData</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/78ee9813-e23e-4d46-acc4-f2fa88559b03">QueryGetData</a> function.</p>
</dd>

### -field <b>pfnFlush</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/846f8539-4cb3-41d5-836d-563b7eb0d70b">Flush(D3D10)</a> function.</p>
</dd>

### -field <b>pfnGenMips</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/abd045f2-9c05-4579-8d80-aba31523157d">GenMips</a> function.</p>
</dd>

### -field <b>pfnResourceCopy</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/9a837f42-0bea-4425-b693-dd7947ac24b1">ResourceCopy</a> function.</p>
</dd>

### -field <b>pfnResourceResolveSubresource</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/f9f4a6e2-bc01-477f-a919-ec71871f665b">ResourceResolveSubresource</a> function.</p>
</dd>

### -field <b>pfnResourceMap</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/1310a3f8-02dd-4d35-98ad-4016e57d1eb2">ResourceMap</a> function.</p>
</dd>

### -field <b>pfnResourceUnmap</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/fb2b714e-232d-40b2-88ad-ee8dcd70a057">ResourceUnmap</a> function.</p>
</dd>

### -field <b>pfnResourceIsStagingBusy</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/df8498e2-a3b5-4bc8-b6d2-0d444f1d1485">ResourceIsStagingBusy</a> function.</p>
</dd>

### -field <b>pfnRelocateDeviceFuncs</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/3932a2a1-7b1d-4921-bd4a-905b44166091">RelocateDeviceFuncs</a> function.</p>
</dd>

### -field <b>pfnCalcPrivateResourceSize</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/2c4eb002-4788-46ab-92b9-3bb2dcb44ee3">CalcPrivateResourceSize</a> function.</p>
</dd>

### -field <b>pfnCalcPrivateOpenedResourceSize</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/000688fb-6475-4dab-bb65-91c899a592a7">CalcPrivateOpenedResourceSize</a> function.</p>
</dd>

### -field <b>pfnCreateResource</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/c21839f0-8302-49f9-a2b4-4009fbd2d88c">CreateResource(D3D10)</a> function.</p>
</dd>

### -field <b>pfnOpenResource</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/95f6d1e5-0c85-41ce-ad6d-f10d5103e2eb">OpenResource(D3D10)</a> function.</p>
</dd>

### -field <b>pfnDestroyResource</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/3ff77844-eeee-4fda-8798-2e240bc51379">DestroyResource(D3D10)</a> function.</p>
</dd>

### -field <b>pfnCalcPrivateShaderResourceViewSize</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/2abf5ca9-974b-40d7-b71c-43c4fb33dd7c">CalcPrivateShaderResourceViewSize</a> function.</p>
</dd>

### -field <b>pfnCreateShaderResourceView</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/3b1c998d-3fde-4712-ba74-7c8033033182">CreateShaderResourceView</a> function.</p>
</dd>

### -field <b>pfnDestroyShaderResourceView</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/dcdfe76e-a392-4a76-91fe-03648fec1278">DestroyShaderResourceView</a> function.</p>
</dd>

### -field <b>pfnCalcPrivateRenderTargetViewSize</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/14d85e4a-960c-4438-9360-a4f2677603b8">CalcPrivateRenderTargetViewSize</a> function.</p>
</dd>

### -field <b>pfnCreateRenderTargetView</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/bf9fc732-5f9a-4fee-8ea0-19b140789463">CreateRenderTargetView</a> function.</p>
</dd>

### -field <b>pfnDestroyRenderTargetView</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/ec04fed3-8e43-4f76-af82-b36c7029f0cc">DestroyRenderTargetView</a> function.</p>
</dd>

### -field <b>pfnCalcPrivateDepthStencilViewSize</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/e5dfa018-f9a5-467f-8e84-9697d5f94689">CalcPrivateDepthStencilViewSize</a> function.</p>
</dd>

### -field <b>pfnCreateDepthStencilView</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/1a1c28f0-8343-4255-8055-d31eb643b7d5">CreateDepthStencilView</a> function.</p>
</dd>

### -field <b>pfnDestroyDepthStencilView</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/5cd2b7bd-0231-4f00-a54e-960b9bffa98e">DestroyDepthStencilView</a> function.</p>
</dd>

### -field <b>pfnCalcPrivateElementLayoutSize</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/9fc80cea-8e4a-467a-b232-74333d2ceb5f">CalcPrivateElementLayoutSize</a> function.</p>
</dd>

### -field <b>pfnCreateElementLayout</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/5af2189a-a064-4c62-be09-733c1d632983">CreateElementLayout</a> function.</p>
</dd>

### -field <b>pfnDestroyElementLayout</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/8b6a07b5-5358-45d3-af42-84f8a6327535">DestroyElementLayout</a> function.</p>
</dd>

### -field <b>pfnCalcPrivateBlendStateSize</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/c13862b0-3136-4a95-bb00-6057f2934068">CalcPrivateBlendStateSize</a> function.</p>
</dd>

### -field <b>pfnCreateBlendState</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/f203a83c-0108-4e20-9972-06857099378c">CreateBlendState</a> function.</p>
</dd>

### -field <b>pfnDestroyBlendState</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/56fc1ecf-fd4c-4d36-941b-8fa6cca3b6b4">DestroyBlendState</a> function.</p>
</dd>

### -field <b>pfnCalcPrivateDepthStencilStateSize</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/dcc02e1e-97e0-4ccd-8329-8219cad5d09a">CalcPrivateDepthStencilStateSize</a> function.</p>
</dd>

### -field <b>pfnCreateDepthStencilState</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/ed2da104-c4e8-43eb-80e0-10273b575020">CreateDepthStencilState</a> function.</p>
</dd>

### -field <b>pfnDestroyDepthStencilState</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/5fc537f6-2507-4edd-bfa0-c011dd834a22">DestroyDepthStencilState</a> function.</p>
</dd>

### -field <b>pfnCalcPrivateRasterizerStateSize</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/8b10b2b8-21b0-451c-9a85-353222d9c288">CalcPrivateRasterizerStateSize</a> function.</p>
</dd>

### -field <b>pfnCreateRasterizerState</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/4507b92e-2437-4f90-b527-e06773ca1e08">CreateRasterizerState</a> function.</p>
</dd>

### -field <b>pfnDestroyRasterizerState</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/7d730528-dc97-4490-a9fa-3d7916eef2e6">DestroyRasterizerState</a> function.</p>
</dd>

### -field <b>pfnCalcPrivateShaderSize</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/76cdddb0-b927-4547-ae1d-f5105905633b">CalcPrivateShaderSize</a> function.</p>
</dd>

### -field <b>pfnCreateVertexShader</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/d6e4c3f9-1ee6-4484-913d-9a3dca64e627">CreateVertexShader(D3D10)</a> function.</p>
</dd>

### -field <b>pfnCreateGeometryShader</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/b3b422e3-f8da-4aad-a230-7c7e26dd72ec">CreateGeometryShader</a> function.</p>
</dd>

### -field <b>pfnCreatePixelShader</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/67b7cc14-89f5-45f2-b1cf-53316f495c66">CreatePixelShader(D3D10)</a> function.</p>
</dd>

### -field <b>pfnCalcPrivateGeometryShaderWithStreamOutput</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/3e760b93-e859-4175-a24a-6bf3648db6db">CalcPrivateGeometryShaderWithStreamOutput</a> function.</p>
</dd>

### -field <b>pfnCreateGeometryShaderWithStreamOutput</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/6ad1573d-4377-4795-8511-5d6cae96ee4f">CreateGeometryShaderWithStreamOutput</a> function.</p>
</dd>

### -field <b>pfnDestroyShader</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/51a3e5aa-0f17-49a6-824d-7cfe8e0a1ded">DestroyShader</a> function.</p>
</dd>

### -field <b>pfnCalcPrivateSamplerSize</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/7231ba65-f6ed-4b00-a61f-21d8fe26398f">CalcPrivateSamplerSize</a> function.</p>
</dd>

### -field <b>pfnCreateSampler</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/603bb033-390b-4965-b6ea-6acc2c7a8fcf">CreateSampler</a> function.</p>
</dd>

### -field <b>pfnDestroySampler</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/8e66de90-c336-43b4-b0ad-cb24cea3638c">DestroySampler</a> function.</p>
</dd>

### -field <b>pfnCalcPrivateQuerySize</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/59a59aa8-085e-4bf8-8a6f-e08f2aecd894">CalcPrivateQuerySize</a> function.</p>
</dd>

### -field <b>pfnCreateQuery</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/abe6a82f-1613-4c74-9e81-01939db74bfd">CreateQuery(D3D10)</a> function.</p>
</dd>

### -field <b>pfnDestroyQuery</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/74bb85df-6d64-49e8-b431-2f4a9954eff2">DestroyQuery(D3D10)</a> function.</p>
</dd>

### -field <b>pfnCheckFormatSupport</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/463ab1e5-08b1-45a1-b7d8-bdfacb3d4bdb">CheckFormatSupport</a> function.</p>
</dd>

### -field <b>pfnCheckMultisampleQualityLevels</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/2b6a0ab8-f197-48c3-baf2-305b77b7e8b5">CheckMultisampleQualityLevels</a> function.</p>
</dd>

### -field <b>pfnCheckCounterInfo</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/5dcea47c-aac7-46e5-afd5-c3390c3c5286">CheckCounterInfo</a> function.</p>
</dd>

### -field <b>pfnCheckCounter</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/592a5146-a2fe-41d1-854b-df27a97bd513">CheckCounter</a> function.</p>
</dd>

### -field <b>pfnDestroyDevice</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/90ada8c8-8ad8-4992-aac1-6eb7fdf3f249">DestroyDevice(D3D10)</a> function.</p>
</dd>

### -field <b>pfnSetTextFilterSize</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/663fd3c3-7a8f-446d-b45a-392716116407">SetTextFilterSize</a> function.</p>
</dd>
</dl>

## -remarks
<p>The order of user-mode display driver functions (that is, the order of the members of the D3D10DDI_DEVICEFUNCS structure) is in decreasing order of priority (in regard to performance).</p>

<p>The user-mode display driver can use different names for these functions because the address of the function table (this structure) is shared between the Direct3D 10 runtime and the driver through the call to the driver's <a href="https://msdn.microsoft.com/c69eedb1-c975-412c-aa9f-cf64a702f937">CreateDevice(D3D10)</a> function.</p>

<p>The <b>pfnResetPrimitiveID</b> and  <b>pfnSetVertexPipelineOutput</b> members (not shown here) and their data types are reserved for system use and should not be used in your driver.</p>

## -requirements
<table>
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
<a href="https://msdn.microsoft.com/c69eedb1-c975-412c-aa9f-cf64a702f937">CreateDevice(D3D10)</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541664">D3D10DDIARG_CREATEDEVICE</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3D10DDI_DEVICEFUNCS structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>