---
UID: NS.d3d10umddi.D3DWDDM1_3DDI_DEVICEFUNCS~r1
title: D3DWDDM1_3DDI_DEVICEFUNCS
author: windows-driver-content
description: Contains functions that a user-mode display driver that is optimized for the Microsoft Direct3D version 11.2 runtime can implement to render graphics primitives and process state changes.
old-location: display\d3dwddm1_3ddi_devicefuncs.htm
ms.assetid: DE7A88BA-2E59-4E8C-B315-CA6260E3D68E
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3d10umddi.h
req.include-header: D3d10umddi.h
req.target-type: Windows
req.target-min-winverclnt: Windows 8.1,WDDM 1.3
req.target-min-winversvr: Windows Server 2012 R2
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3D11_1DDI_DEVICEFUNCS
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
ms.keywords: D3DWDDM1_3DDI_DEVICEFUNCS, D3DWDDM1_3DDI_DEVICEFUNCS
req.iface: 
---

# D3DWDDM1_3DDI_DEVICEFUNCS structure



## -description
<p>Contains functions that a user-mode display driver that is optimized for the Microsoft Direct3D version 11.2 runtime can implement to render graphics primitives and process state changes. Used by Windows Display Driver Model (WDDM) 1.3 and later user-mode display drivers.</p>


## -syntax

````
typedef struct D3D11DDI_DEVICEFUNCS {
  PFND3D11_1DDI_RESOURCEUPDATESUBRESOURCEUP               pfnDefaultConstantBufferUpdateSubresourceUP;
  PFND3D11_1DDI_SETCONSTANTBUFFERS                        pfnVsSetConstantBuffers;
  PFND3D10DDI_SETSHADERRESOURCES                          pfnPsSetShaderResources;
  PFND3D10DDI_SETSHADER                                   pfnPsSetShader;
  PFND3D10DDI_SETSAMPLERS                                 pfnPsSetSamplers;
  PFND3D10DDI_SETSHADER                                   pfnVsSetShader;
  PFND3D10DDI_DRAWINDEXED                                 pfnDrawIndexed;
  PFND3D10DDI_DRAW                                        pfnDraw;
  PFND3D10DDI_RESOURCEMAP                                 pfnDynamicIABufferMapNoOverwrite;
  PFND3D10DDI_RESOURCEUNMAP                               pfnDynamicIABufferUnmap;
  PFND3D10DDI_RESOURCEMAP                                 pfnDynamicConstantBufferMapDiscard;
  PFND3D10DDI_RESOURCEMAP                                 pfnDynamicIABufferMapDiscard;
  PFND3D10DDI_RESOURCEUNMAP                               pfnDynamicConstantBufferUnmap;
  PFND3D11_1DDI_SETCONSTANTBUFFERS                        pfnPsSetConstantBuffers;
  PFND3D10DDI_SETINPUTLAYOUT                              pfnIaSetInputLayout;
  PFND3D10DDI_IA_SETVERTEXBUFFERS                         pfnIaSetVertexBuffers;
  PFND3D10DDI_IA_SETINDEXBUFFER                           pfnIaSetIndexBuffer;
  PFND3D10DDI_DRAWINDEXEDINSTANCED                        pfnDrawIndexedInstanced;
  PFND3D10DDI_DRAWINSTANCED                               pfnDrawInstanced;
  PFND3D10DDI_RESOURCEMAP                                 pfnDynamicResourceMapDiscard;
  PFND3D10DDI_RESOURCEUNMAP                               pfnDynamicResourceUnmap;
  PFND3D11_1DDI_SETCONSTANTBUFFERS                        pfnGsSetConstantBuffers;
  PFND3D10DDI_SETSHADER                                   pfnGsSetShader;
  PFND3D10DDI_IA_SETTOPOLOGY                              pfnIaSetTopology;
  PFND3D10DDI_RESOURCEMAP                                 pfnStagingResourceMap;
  PFND3D10DDI_RESOURCEUNMAP                               pfnStagingResourceUnmap;
  PFND3D10DDI_SETSHADERRESOURCES                          pfnVsSetShaderResources;
  PFND3D10DDI_SETSAMPLERS                                 pfnVsSetSamplers;
  PFND3D10DDI_SETSHADERRESOURCES                          pfnGsSetShaderResources;
  PFND3D10DDI_SETSAMPLERS                                 pfnGsSetSamplers;
  PFND3D11DDI_SETRENDERTARGETS                            pfnSetRenderTargets;
  PFND3D10DDI_SHADERRESOURCEVIEWREADAFTERWRITEHAZARD      pfnShaderResourceViewReadAfterWriteHazard;
  PFND3D10DDI_RESOURCEREADAFTERWRITEHAZARD                pfnResourceReadAfterWriteHazard;
  PFND3D10DDI_SETBLENDSTATE                               pfnSetBlendState;
  PFND3D10DDI_SETDEPTHSTENCILSTATE                        pfnSetDepthStencilState;
  PFND3D10DDI_SETRASTERIZERSTATE                          pfnSetRasterizerState;
  PFND3D10DDI_QUERYEND                                    pfnQueryEnd;
  PFND3D10DDI_QUERYBEGIN                                  pfnQueryBegin;
  PFND3D11_1DDI_RESOURCECOPYREGION                        pfnResourceCopyRegion;
  PFND3D11_1DDI_RESOURCEUPDATESUBRESOURCEUP               pfnResourceUpdateSubresourceUP;
  PFND3D10DDI_SO_SETTARGETS                               pfnSoSetTargets;
  PFND3D10DDI_DRAWAUTO                                    pfnDrawAuto;
  PFND3D10DDI_SETVIEWPORTS                                pfnSetViewports;
  PFND3D10DDI_SETSCISSORRECTS                             pfnSetScissorRects;
  PFND3D10DDI_CLEARRENDERTARGETVIEW                       pfnClearRenderTargetView;
  PFND3D10DDI_CLEARDEPTHSTENCILVIEW                       pfnClearDepthStencilView;
  PFND3D10DDI_SETPREDICATION                              pfnSetPredication;
  PFND3D10DDI_QUERYGETDATA                                pfnQueryGetData;
  PFND3D11_1DDI_FLUSH                                     pfnFlush;
  PFND3D10DDI_GENMIPS                                     pfnGenMips;
  PFND3D10DDI_RESOURCECOPY                                pfnResourceCopy;
  PFND3D10DDI_RESOURCERESOLVESUBRESOURCE                  pfnResourceResolveSubresource;
  PFND3D10DDI_RESOURCEMAP                                 pfnResourceMap;
  PFND3D10DDI_RESOURCEUNMAP                               pfnResourceUnmap;
  PFND3D10DDI_RESOURCEISSTAGINGBUSY                       pfnResourceIsStagingBusy;
  PFND3D11_1DDI_RELOCATEDEVICEFUNCS                       pfnRelocateDeviceFuncs;
  PFND3D11DDI_CALCPRIVATERESOURCESIZE                     pfnCalcPrivateResourceSize;
  PFND3D10DDI_CALCPRIVATEOPENEDRESOURCESIZE               pfnCalcPrivateOpenedResourceSize;
  PFND3D11DDI_CREATERESOURCE                              pfnCreateResource;
  PFND3D10DDI_OPENRESOURCE                                pfnOpenResource;
  PFND3D10DDI_DESTROYRESOURCE                             pfnDestroyResource;
  PFND3D11DDI_CALCPRIVATESHADERRESOURCEVIEWSIZE           pfnCalcPrivateShaderResourceViewSize;
  PFND3D11DDI_CREATESHADERRESOURCEVIEW                    pfnCreateShaderResourceView;
  PFND3D10DDI_DESTROYSHADERRESOURCEVIEW                   pfnDestroyShaderResourceView;
  PFND3D10DDI_CALCPRIVATERENDERTARGETVIEWSIZE             pfnCalcPrivateRenderTargetViewSize;
  PFND3D10DDI_CREATERENDERTARGETVIEW                      pfnCreateRenderTargetView;
  PFND3D10DDI_DESTROYRENDERTARGETVIEW                     pfnDestroyRenderTargetView;
  PFND3D11DDI_CALCPRIVATEDEPTHSTENCILVIEWSIZE             pfnCalcPrivateDepthStencilViewSize;
  PFND3D11DDI_CREATEDEPTHSTENCILVIEW                      pfnCreateDepthStencilView;
  PFND3D10DDI_DESTROYDEPTHSTENCILVIEW                     pfnDestroyDepthStencilView;
  PFND3D10DDI_CALCPRIVATEELEMENTLAYOUTSIZE                pfnCalcPrivateElementLayoutSize;
  PFND3D10DDI_CREATEELEMENTLAYOUT                         pfnCreateElementLayout;
  PFND3D10DDI_DESTROYELEMENTLAYOUT                        pfnDestroyElementLayout;
  PFND3D11_1DDI_CALCPRIVATEBLENDSTATESIZE                 pfnCalcPrivateBlendStateSize;
  PFND3D11_1DDI_CREATEBLENDSTATE                          pfnCreateBlendState;
  PFND3D10DDI_DESTROYBLENDSTATE                           pfnDestroyBlendState;
  PFND3D10DDI_CALCPRIVATEDEPTHSTENCILSTATESIZE            pfnCalcPrivateDepthStencilStateSize;
  PFND3D10DDI_CREATEDEPTHSTENCILSTATE                     pfnCreateDepthStencilState;
  PFND3D10DDI_DESTROYDEPTHSTENCILSTATE                    pfnDestroyDepthStencilState;
  PFND3D11_1DDI_CALCPRIVATERASTERIZERSTATESIZE            pfnCalcPrivateRasterizerStateSize;
  PFND3D11_1DDI_CREATERASTERIZERSTATE                     pfnCreateRasterizerState;
  PFND3D10DDI_DESTROYRASTERIZERSTATE                      pfnDestroyRasterizerState;
  PFND3D11_1DDI_CALCPRIVATESHADERSIZE                     pfnCalcPrivateShaderSize;
  PFND3D11_1DDI_CREATEVERTEXSHADER                        pfnCreateVertexShader;
  PFND3D11_1DDI_CREATEGEOMETRYSHADER                      pfnCreateGeometryShader;
  PFND3D11_1DDI_CREATEPIXELSHADER                         pfnCreatePixelShader;
  PFND3D11_1DDI_CALCPRIVATEGEOMETRYSHADERWITHSTREAMOUTPUT pfnCalcPrivateGeometryShaderWithStreamOutput;
  PFND3D11_1DDI_CREATEGEOMETRYSHADERWITHSTREAMOUTPUT      pfnCreateGeometryShaderWithStreamOutput;
  PFND3D10DDI_DESTROYSHADER                               pfnDestroyShader;
  PFND3D10DDI_CALCPRIVATESAMPLERSIZE                      pfnCalcPrivateSamplerSize;
  PFND3D10DDI_CREATESAMPLER                               pfnCreateSampler;
  PFND3D10DDI_DESTROYSAMPLER                              pfnDestroySampler;
  PFND3D10DDI_CALCPRIVATEQUERYSIZE                        pfnCalcPrivateQuerySize;
  PFND3D10DDI_CREATEQUERY                                 pfnCreateQuery;
  PFND3D10DDI_DESTROYQUERY                                pfnDestroyQuery;
  PFND3D10DDI_CHECKFORMATSUPPORT                          pfnCheckFormatSupport;
  PFND3D10DDI_CHECKMULTISAMPLEQUALITYLEVELS               pfnCheckMultisampleQualityLevels;
  PFND3D10DDI_CHECKCOUNTERINFO                            pfnCheckCounterInfo;
  PFND3D10DDI_CHECKCOUNTER                                pfnCheckCounter;
  PFND3D10DDI_DESTROYDEVICE                               pfnDestroyDevice;
  PFND3D10DDI_SETTEXTFILTERSIZE                           pfnSetTextFilterSize;
  PFND3D10DDI_RESOURCECOPY                                pfnResourceConvert;
  PFND3D11_1DDI_RESOURCECOPYREGION                        pfnResourceConvertRegion;
  PFND3D11DDI_DRAWINDEXEDINSTANCEDINDIRECT                pfnDrawIndexedInstancedIndirect;
  PFND3D11DDI_DRAWINSTANCEDINDIRECT                       pfnDrawInstancedIndirect;
  PFND3D11DDI_COMMANDLISTEXECUTE                          pfnCommandListExecute;
  PFND3D10DDI_SETSHADERRESOURCES                          pfnHsSetShaderResources;
  PFND3D10DDI_SETSHADER                                   pfnHsSetShader;
  PFND3D10DDI_SETSAMPLERS                                 pfnHsSetSamplers;
  PFND3D11_1DDI_SETCONSTANTBUFFERS                        pfnHsSetConstantBuffers;
  PFND3D10DDI_SETSHADERRESOURCES                          pfnDsSetShaderResources;
  PFND3D10DDI_SETSHADER                                   pfnDsSetShader;
  PFND3D10DDI_SETSAMPLERS                                 pfnDsSetSamplers;
  PFND3D11_1DDI_SETCONSTANTBUFFERS                        pfnDsSetConstantBuffers;
  PFND3D11_1DDI_CREATEHULLSHADER                          pfnCreateHullShader;
  PFND3D11_1DDI_CREATEDOMAINSHADER                        pfnCreateDomainShader;
  PFND3D11DDI_CHECKDEFERREDCONTEXTHANDLESIZES             pfnCheckDeferredContextHandleSizes;
  PFND3D11DDI_CALCDEFERREDCONTEXTHANDLESIZE               pfnCalcDeferredContextHandleSize;
  PFND3D11DDI_CALCPRIVATEDEFERREDCONTEXTSIZE              pfnCalcPrivateDeferredContextSize;
  PFND3D11DDI_CREATEDEFERREDCONTEXT                       pfnCreateDeferredContext;
  PFND3D11DDI_ABANDONCOMMANDLIST                          pfnAbandonCommandList;
  PFND3D11DDI_CALCPRIVATECOMMANDLISTSIZE                  pfnCalcPrivateCommandListSize;
  PFND3D11DDI_CREATECOMMANDLIST                           pfnCreateCommandList;
  PFND3D11DDI_DESTROYCOMMANDLIST                          pfnDestroyCommandList;
  PFND3D11_1DDI_CALCPRIVATETESSELLATIONSHADERSIZE         pfnCalcPrivateTessellationShaderSize;
  PFND3D11DDI_SETSHADER_WITH_IFACES                       pfnPsSetShaderWithIfaces;
  PFND3D11DDI_SETSHADER_WITH_IFACES                       pfnVsSetShaderWithIfaces;
  PFND3D11DDI_SETSHADER_WITH_IFACES                       pfnGsSetShaderWithIfaces;
  PFND3D11DDI_SETSHADER_WITH_IFACES                       pfnHsSetShaderWithIfaces;
  PFND3D11DDI_SETSHADER_WITH_IFACES                       pfnDsSetShaderWithIfaces;
  PFND3D11DDI_SETSHADER_WITH_IFACES                       pfnCsSetShaderWithIfaces;
  PFND3D11DDI_CREATECOMPUTESHADER                         pfnCreateComputeShader;
  PFND3D10DDI_SETSHADER                                   pfnCsSetShader;
  PFND3D10DDI_SETSHADERRESOURCES                          pfnCsSetShaderResources;
  PFND3D10DDI_SETSAMPLERS                                 pfnCsSetSamplers;
  PFND3D11_1DDI_SETCONSTANTBUFFERS                        pfnCsSetConstantBuffers;
  PFND3D11DDI_CALCPRIVATEUNORDEREDACCESSVIEWSIZE          pfnCalcPrivateUnorderedAccessViewSize;
  PFND3D11DDI_CREATEUNORDEREDACCESSVIEW                   pfnCreateUnorderedAccessView;
  PFND3D11DDI_DESTROYUNORDEREDACCESSVIEW                  pfnDestroyUnorderedAccessView;
  PFND3D11DDI_CLEARUNORDEREDACCESSVIEWUINT                pfnClearUnorderedAccessViewUint;
  PFND3D11DDI_CLEARUNORDEREDACCESSVIEWFLOAT               pfnClearUnorderedAccessViewFloat;
  PFND3D11DDI_SETUNORDEREDACCESSVIEWS                     pfnCsSetUnorderedAccessViews;
  PFND3D11DDI_DISPATCH                                    pfnDispatch;
  PFND3D11DDI_DISPATCHINDIRECT                            pfnDispatchIndirect;
  PFND3D11DDI_SETRESOURCEMINLOD                           pfnSetResourceMinLOD;
  PFND3D11DDI_COPYSTRUCTURECOUNT                          pfnCopyStructureCount;
  PFND3D11DDI_RECYCLECOMMANDLIST                          pfnRecycleCommandList;
  PFND3D11DDI_RECYCLECREATECOMMANDLIST                    pfnRecycleCreateCommandList;
  PFND3D11DDI_RECYCLECREATEDEFERREDCONTEXT                pfnRecycleCreateDeferredContext;
  PFND3D11DDI_DESTROYCOMMANDLIST                          pfnRecycleDestroyCommandList;
  PFND3D11_1DDI_DISCARD                                   pfnDiscard;
  PFND3D11_1DDI_ASSIGNDEBUGBINARY                         pfnAssignDebugBinary;
  PFND3D10DDI_RESOURCEMAP                                 pfnDynamicConstantBufferMapNoOverwrite;
  PFND3D11_1DDI_CHECKDIRECTFLIPSUPPORT                    pfnCheckDirectFlipSupport;
  PFND3D11_1DDI_CLEARVIEW                                 pfnClearView;
  PFND3DWDDM1_3DDI_UPDATETILEMAPPINGS                     pfnUpdateTileMappings;
  PFND3DWDDM1_3DDI_COPYTILEMAPPINGS                       pfnCopyTileMappings;
  PFND3DWDDM1_3DDI_COPYTILES                              pfnCopyTiles;
  PFND3DWDDM1_3DDI_UPDATETILES                            pfnUpdateTiles;
  PFND3DWDDM1_3DDI_TILEDRESOURCEBARRIER                   pfnTiledResourceBarrier;
  PFND3DWDDM1_3DDI_GETMIPPACKING                          pfnGetMipPacking;
  PFND3DWDDM1_3DDI_RESIZETILEPOOL                         pfnResizeTilePool;
  PFND3DWDDM1_3DDI_SETMARKER                              pfnSetMarker;
  PFND3DWDDM1_3DDI_SETMARKERMODE                          pfnSetMarkerMode;
} D3D11_1DDI_DEVICEFUNCS;
````


## -struct-fields
<dl>

### -field <b>pfnDefaultConstantBufferUpdateSubresourceUP</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/67FCC9A4-B3C5-46FC-83ED-CFFB8186328F">DefaultConstantBufferUpdateSubresourceUP(D3D11_1)</a> function.</p>
</dd>

### -field <b>pfnVsSetConstantBuffers</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/82C277EF-7FC9-43AF-B84A-CB464AB7D73C">VsSetConstantBuffers(D3D11_1)</a> function.</p>
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
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/1310a3f8-02dd-4d35-98ad-4016e57d1eb2">ResourceMap</a> function. For more information about whether to implement a separate <i>DynamicIABufferMapNoOverwrite</i> function or to point to the multipurpose <i>ResourceMap</i>, see the Remarks section of <i>ResourceMap</i>. </p>
</dd>

### -field <b>pfnDynamicIABufferUnmap</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/fb2b714e-232d-40b2-88ad-ee8dcd70a057">ResourceUnmap</a> function. For more information about whether to implement a separate <i>DynamicIABufferUnmap</i> function or to point to the multipurpose <i>ResourceUnmap</i>, see the Remarks section of <a href="https://msdn.microsoft.com/1310a3f8-02dd-4d35-98ad-4016e57d1eb2">ResourceMap</a>. </p>
</dd>

### -field <b>pfnDynamicConstantBufferMapDiscard</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/1310a3f8-02dd-4d35-98ad-4016e57d1eb2">ResourceMap</a> function. For more information about whether to implement a separate <i>DynamicConstantBufferMapDiscard</i> function or to point to the multipurpose <i>ResourceMap</i>, see the Remarks section of <i>ResourceMap</i>. </p>
</dd>

### -field <b>pfnDynamicIABufferMapDiscard</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/1310a3f8-02dd-4d35-98ad-4016e57d1eb2">ResourceMap</a> function. For more information about whether to implement a separate <i>DynamicIABufferMapDiscard</i> function or to point to the multipurpose <i>ResourceMap</i>, see the Remarks section of <i>ResourceMap</i>. </p>
</dd>

### -field <b>pfnDynamicConstantBufferUnmap</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/fb2b714e-232d-40b2-88ad-ee8dcd70a057">ResourceUnmap</a> function. For more information about whether to implement a separate <i>DynamicConstantBufferUnmap</i> function or to point to the multipurpose <i>ResourceUnmap</i>, see the Remarks section of <a href="https://msdn.microsoft.com/1310a3f8-02dd-4d35-98ad-4016e57d1eb2">ResourceMap</a>. </p>
</dd>

### -field <b>pfnPsSetConstantBuffers</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/052CACD8-7812-42B8-A5DD-E6DCD7BFA3D7">PsSetConstantBuffers(D3D11_1)</a> function.</p>
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
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/1310a3f8-02dd-4d35-98ad-4016e57d1eb2">ResourceMap</a> function. For more information about whether to implement a separate <i>DynamicResourceMapDiscard</i> function or to point to the multipurpose <i>ResourceMap</i>, see the Remarks section of <i>ResourceMap</i>. </p>
</dd>

### -field <b>pfnDynamicResourceUnmap</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/fb2b714e-232d-40b2-88ad-ee8dcd70a057">ResourceUnmap</a> function. For more information about whether to implement a separate <i>DynamicResourceUnmap</i> function or to point to the multipurpose <i>ResourceUnmap</i>, see the Remarks section of <a href="https://msdn.microsoft.com/1310a3f8-02dd-4d35-98ad-4016e57d1eb2">ResourceMap</a>. </p>
</dd>

### -field <b>pfnGsSetConstantBuffers</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/9C7655F9-049E-47B7-90F4-D337D88C864E">GsSetConstantBuffers(D3D11_1)</a> function.</p>
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
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/1310a3f8-02dd-4d35-98ad-4016e57d1eb2">ResourceMap</a> function. For more information about whether to implement a separate <i>StagingResourceMap</i> function or to point to the multipurpose <i>ResourceMap</i>, see the Remarks section of <i>ResourceMap</i>. </p>
</dd>

### -field <b>pfnStagingResourceUnmap</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/fb2b714e-232d-40b2-88ad-ee8dcd70a057">ResourceUnmap</a> function. For more information about whether to implement a separate <i>StagingResourceUnmap</i> function or to point to the multipurpose <i>ResourceUnmap</i>, see the Remarks section of <a href="https://msdn.microsoft.com/1310a3f8-02dd-4d35-98ad-4016e57d1eb2">ResourceMap</a>. </p>
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
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/cfe5f570-4e53-43ee-942d-56da8dfcfe80">SetRenderTargets(D3D11)</a> function.</p>
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
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/CA26FB37-1A4C-4057-90A5-64FFBE289E39">ResourceCopyRegion(D3D11_1)</a> function.</p>
</dd>

### -field <b>pfnResourceUpdateSubresourceUP</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/7c2363ea-2191-4b99-94a2-d98a11ee8cce">ResourceUpdateSubresourceUP(D3D11_1)</a> function.</p>
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
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/6f4bda19-2d51-4058-ba68-cbb5deb44a54">Flush(D3D11_1)</a> function.</p>
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
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/5d9f964e-5d7a-4b6c-977e-c718e3424f84">RelocateDeviceFuncs(D3D11_1)</a> function.</p>
</dd>

### -field <b>pfnCalcPrivateResourceSize</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/3b3a2571-012e-4acd-b836-f52e7b88a2fb">CalcPrivateResourceSize(D3D11)</a> function.</p>
</dd>

### -field <b>pfnCalcPrivateOpenedResourceSize</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/000688fb-6475-4dab-bb65-91c899a592a7">CalcPrivateOpenedResourceSize</a> function.</p>
</dd>

### -field <b>pfnCreateResource</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/2dff9d2e-c497-422f-824b-a7101904fd67">CreateResource(D3D11)</a> function.</p>
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
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/894f6ef1-a5a4-40aa-9a07-f66da4ce7d81">CalcPrivateShaderResourceViewSize(D3D11)</a> function.</p>
</dd>

### -field <b>pfnCreateShaderResourceView</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/7ca462c7-ec43-4af7-92c8-ed69e5d324e2">CreateShaderResourceView(D3D11)</a> function.</p>
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
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/d92e3bde-9527-401e-aafd-4ba39603d4a7">CalcPrivateDepthStencilViewSize(D3D11)</a> function.</p>
</dd>

### -field <b>pfnCreateDepthStencilView</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/cf4c34da-71df-4b49-b1c8-73d1a2dbc3cb">CreateDepthStencilView(D3D11)</a> function.</p>
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
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/e53bb658-ef6c-4f44-aa5a-8c641046f90d">CalcPrivateBlendStateSize(D3D11_1)</a> function.</p>
</dd>

### -field <b>pfnCreateBlendState</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/5956412e-ae35-4960-afc0-a82c6a2aa9f1">CreateBlendState(D3D11_1)</a> function.</p>
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
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/76d0228e-a6e5-425e-a2b6-7d719dbfa43d">CalcPrivateRasterizerStateSize(D3D11_1)</a> function.</p>
</dd>

### -field <b>pfnCreateRasterizerState</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/5640e1c9-6a38-4eca-9048-0bc9ff66c43c">CreateRasterizerState(D3D11_1)</a> function.</p>
</dd>

### -field <b>pfnDestroyRasterizerState</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/7d730528-dc97-4490-a9fa-3d7916eef2e6">DestroyRasterizerState</a> function.</p>
</dd>

### -field <b>pfnCalcPrivateShaderSize</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/e23c267f-41df-47a6-ae43-3bbcb48fd300">CalcPrivateShaderSize(D3D11_1)</a> function.</p>
</dd>

### -field <b>pfnCreateVertexShader</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/8da896d3-b80c-409a-a838-99eb71668a93">CreateVertexShader(D3D11_1)</a> function.</p>
</dd>

### -field <b>pfnCreateGeometryShader</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/A0C3826D-E4F3-4169-A899-41C11006DE69">CreateGeometryShader(D3D11_1)</a> function.</p>
</dd>

### -field <b>pfnCreatePixelShader</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/8b5d6d2e-6a08-4841-8df5-ca88368a4e26">CreatePixelShader(D3D11_1)</a> function.</p>
</dd>

### -field <b>pfnCalcPrivateGeometryShaderWithStreamOutput</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/316e30b9-eb06-483c-a124-476b4308cf5f">CalcPrivateGeometryShaderWithStreamOutput(D3D11_1)</a> function.</p>
</dd>

### -field <b>pfnCreateGeometryShaderWithStreamOutput</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/1d06ef38-4eb9-4129-b409-74bbd1951f92">CreateGeometryShaderWithStreamOutput(D3D11_1)</a> function.</p>
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

### -field <b>pfnResourceConvert</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/9a837f42-0bea-4425-b693-dd7947ac24b1">ResourceCopy</a> function. For more information about whether to implement a separate <i>ResourceConvert</i> function or to point to the multipurpose <i>ResourceCopy</i>, see the Remarks section of <i>ResourceCopy</i>.</p>
</dd>

### -field <b>pfnResourceConvertRegion</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/CA26FB37-1A4C-4057-90A5-64FFBE289E39">ResourceCopyRegion(D3D11_1)</a> function. For more information about whether to implement a separate <i>ResourceConvertRegion(D3D11_1)</i> function or to point to the multipurpose <i>ResourceCopyRegion(D3D11_1)</i>, see the Remarks section of <i>ResourceCopyRegion(D3D11_1)</i>.</p>
</dd>

### -field <b>pfnDrawIndexedInstancedIndirect</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/3debfb11-4de9-456b-a094-feb2f68e96a5">DrawIndexedInstancedIndirect</a> function.</p>
</dd>

### -field <b>pfnDrawInstancedIndirect</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/99520dae-3934-496f-80bf-e5b306554415">DrawInstancedIndirect</a> function.</p>
</dd>

### -field <b>pfnCommandListExecute</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/49f44f29-52f6-40d9-8617-a24aa3d30736">CommandListExecute</a> function. The driver is only required to implement <i>CommandListExecute</i> if the driver supports the D3D11DDICAPS_COMMANDLISTS_BUILD_2 capability. </p>
</dd>

### -field <b>pfnHsSetShaderResources</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/54449d80-4943-4178-99cb-0ceed498600c">HsSetShaderResources</a> function.</p>
</dd>

### -field <b>pfnHsSetShader</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/ee70f44c-f160-4fd1-971d-9a4f8b9bd906">HsSetShader</a> function.</p>
</dd>

### -field <b>pfnHsSetSamplers</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/7aeb4bbc-7405-4795-afdd-d20def3c2c9c">HsSetSamplers</a> function.</p>
</dd>

### -field <b>pfnHsSetConstantBuffers</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/35A2EE73-940B-4CC8-B49D-8FCA48F23369">HsSetConstantBuffers(D3D11_1)</a> function.</p>
</dd>

### -field <b>pfnDsSetShaderResources</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/4e108415-4259-4382-8971-63c879f079e7">DsSetShaderResources</a> function.</p>
</dd>

### -field <b>pfnDsSetShader</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/3824f8b1-d3ee-45be-991f-196ef6eec9c3">DsSetShader</a> function.</p>
</dd>

### -field <b>pfnDsSetSamplers</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/1d398a7f-9f1b-42bc-862f-457ebbd41761">DsSetSamplers</a> function.</p>
</dd>

### -field <b>pfnDsSetConstantBuffers</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/9D82F689-E68B-4A15-8532-7BF696E84753">DsSetConstantBuffers(D3D11_1)</a> function.</p>
</dd>

### -field <b>pfnCreateHullShader</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/5461f9d4-5eff-4ff7-9eeb-cf94bc243dba">CreateHullShader(D3D11_1)</a> function.</p>
</dd>

### -field <b>pfnCreateDomainShader</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/74e6457f-4a99-4b19-9a7e-3ebac5aef48e">CreateDomainShader(D3D11_1)</a> function.</p>
</dd>

### -field <b>pfnCheckDeferredContextHandleSizes</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/0ddaec86-79e6-4d09-8403-6588b35f8b0f">CheckDeferredContextHandleSizes</a> function. The driver is only required to implement <i>CheckDeferredContextHandleSizes</i> if the driver supports the D3D11DDICAPS_COMMANDLISTS_BUILD_2 capability. </p>
</dd>

### -field <b>pfnCalcDeferredContextHandleSize</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/d26c26ef-be8e-434a-b3d3-623ed539c541">CalcDeferredContextHandleSize</a> function. The driver is only required to implement <i>CalcDeferredContextHandleSize</i> if the driver supports the D3D11DDICAPS_COMMANDLISTS_BUILD_2 capability. </p>
</dd>

### -field <b>pfnCalcPrivateDeferredContextSize</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/282898b1-45e1-4d85-9ab7-fd400623bdc5">CalcPrivateDeferredContextSize</a> function. The driver is only required to implement <i>CalcPrivateDeferredContextSize</i> if the driver supports the D3D11DDICAPS_COMMANDLISTS_BUILD_2 capability. </p>
</dd>

### -field <b>pfnCreateDeferredContext</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/464a2291-55c8-4e51-ba08-219ce426d038">CreateDeferredContext</a> function. The driver is only required to implement <i>CreateDeferredContext</i> if the driver supports the D3D11DDICAPS_COMMANDLISTS_BUILD_2 capability. </p>
</dd>

### -field <b>pfnAbandonCommandList</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/fc8347da-25ac-47ea-b482-61b7873ca5bc">AbandonCommandList</a> function. The driver is only required to implement <i>AbandonCommandList</i> if the driver supports the D3D11DDICAPS_COMMANDLISTS_BUILD_2 capability. </p>
</dd>

### -field <b>pfnCalcPrivateCommandListSize</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/04725df2-6373-4e04-862e-d533363af00b">CalcPrivateCommandListSize</a> function. The driver is only required to implement <i>CalcPrivateCommandListSize</i> if the driver supports the D3D11DDICAPS_COMMANDLISTS_BUILD_2 capability. </p>
</dd>

### -field <b>pfnCreateCommandList</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/583bde52-ba21-44ce-9f48-8ace6f7a70cc">CreateCommandList</a> function. The driver is only required to implement <i>CreateCommandList</i> if the driver supports the D3D11DDICAPS_COMMANDLISTS_BUILD_2 capability. </p>
</dd>

### -field <b>pfnDestroyCommandList</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/9f03c193-f017-4189-a082-908e28a2e9f7">DestroyCommandList</a> function. The driver is only required to implement <i>DestroyCommandList</i> if the driver supports the D3D11DDICAPS_COMMANDLISTS_BUILD_2 capability. </p>
</dd>

### -field <b>pfnCalcPrivateTessellationShaderSize</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/606b50c0-4070-4694-9299-f20e28743958">CalcPrivateTessellationShaderSize(D3D11_1)</a> function. </p>
</dd>

### -field <b>pfnPsSetShaderWithIfaces</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/8d8d4449-1770-4a57-b8b9-e1cfc64b96cb">PsSetShaderWithIfaces</a> function. </p>
</dd>

### -field <b>pfnVsSetShaderWithIfaces</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/cc360e57-8c0a-441a-a072-7dc792ce201c">VsSetShaderWithIfaces</a> function. </p>
</dd>

### -field <b>pfnGsSetShaderWithIfaces</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/f1db3ed8-7621-4d3a-820d-f50298967404">GsSetShaderWithIfaces</a> function. </p>
</dd>

### -field <b>pfnHsSetShaderWithIfaces</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/c0dd4504-33d3-4a49-ac4e-169375f81430">HsSetShaderWithIfaces</a> function. </p>
</dd>

### -field <b>pfnDsSetShaderWithIfaces</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/fce9447a-459d-4446-9764-5b7daedce041">DsSetShaderWithIfaces</a> function. </p>
</dd>

### -field <b>pfnCsSetShaderWithIfaces</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/2e7170e8-2b77-45a7-9ff5-834452c13ddf">CsSetShaderWithIfaces</a> function. </p>
</dd>

### -field <b>pfnCreateComputeShader</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/e62ad086-f652-4e2c-bc2d-f1ccb197f01e">CreateComputeShader</a> function. </p>
</dd>

### -field <b>pfnCsSetShader</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/ab689c60-3099-4d69-a7e2-5edfb623cbc3">CsSetShader</a> function. </p>
</dd>

### -field <b>pfnCsSetShaderResources</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/29570c3b-eb3b-4d8f-b471-8f3ea6226e23">CsSetShaderResources</a> function. </p>
</dd>

### -field <b>pfnCsSetSamplers</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/7bf05fb6-e959-464a-9e6b-74c568d1d88c">CsSetSamplers</a> function. </p>
</dd>

### -field <b>pfnCsSetConstantBuffers</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/6A2B50BF-415D-47BB-9514-B15F717A76EA">CsSetConstantBuffers(D3D11_1)</a> function. </p>
</dd>

### -field <b>pfnCalcPrivateUnorderedAccessViewSize</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/6aca5d33-c8c6-4c6b-a66a-e28a958cbc2e">CalcPrivateUnorderedAccessViewSize</a> function. </p>
</dd>

### -field <b>pfnCreateUnorderedAccessView</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/c5a258e7-6645-46bb-ab2c-a1c8f5e593b7">CreateUnorderedAccessView</a> function. </p>
</dd>

### -field <b>pfnDestroyUnorderedAccessView</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/1bce3519-f333-4b47-b29b-bde1b5c3005c">DestroyUnorderedAccessView</a> function. </p>
</dd>

### -field <b>pfnClearUnorderedAccessViewUint</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/7cdc81a9-e468-4da8-bc32-9e9cea1fd60d">ClearUnorderedAccessViewUINT</a> function. </p>
</dd>

### -field <b>pfnClearUnorderedAccessViewFloat</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/31734efd-0c17-4476-918d-942c015072bd">ClearUnorderedAccessViewFLOAT</a> function. </p>
</dd>

### -field <b>pfnCsSetUnorderedAccessViews</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/ab8c529b-19e2-4a2a-af68-0e3998829788">CsSetUnorderedAccessViews</a> function. </p>
</dd>

### -field <b>pfnDispatch</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/6fbbf05a-efb0-4f24-8811-b87141cf2daa">Dispatch</a> function. </p>
</dd>

### -field <b>pfnDispatchIndirect</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/0c818515-163f-48ba-ad57-f4405672c98f">DispatchIndirect</a> function. </p>
</dd>

### -field <b>pfnSetResourceMinLOD</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/a54b2fa7-c0c2-42b7-ae89-7984282d4af4">SetResourceMinLOD</a> function. </p>
</dd>

### -field <b>pfnCopyStructureCount</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/39f20ff3-859f-4933-8be0-e2bb7c05e7e1">CopyStructureCount</a> function. </p>
</dd>

### -field <b>pfnRecycleCommandList</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/4cff7f3d-ba13-4389-bafc-edffc0697ce9">RecycleCommandList</a> function. </p>
</dd>

### -field <b>pfnRecycleCreateCommandList</b>

<dd>
<p>A pointer to the driver's   <a href="https://msdn.microsoft.com/c387545e-2891-401d-b7ca-ee7549a52603">RecycleCreateCommandList</a> function. </p>
</dd>

### -field <b>pfnRecycleCreateDeferredContext</b>

<dd>
<p>A pointer to the driver's  <a href="https://msdn.microsoft.com/c9e08048-683a-4f43-b3b8-1914c2933a5c">RecycleCreateDeferredContext</a> function. </p>
</dd>

### -field <b>pfnRecycleDestroyCommandList</b>

<dd>
<p>A pointer to the driver's  <a href="https://msdn.microsoft.com/9f03c193-f017-4189-a082-908e28a2e9f7">RecycleDestroyCommandList</a> function.</p>
</dd>

### -field <b>pfnDiscard</b>

<dd>
<p>A pointer to the driver's  <a href="https://msdn.microsoft.com/d94234ab-712b-4449-96de-16b9e310d250">Discard(D3D11_1)</a> function. </p>
</dd>

### -field <b>pfnAssignDebugBinary</b>

<dd>
<p>A pointer to the driver's  <a href="https://msdn.microsoft.com/eb1e3c27-71c1-4920-9aa4-3253306fa3f4">AssignDebugBinary</a> function.</p>
</dd>

### -field <b>pfnDynamicConstantBufferMapNoOverwrite</b>

<dd>
<p>A pointer to the driver's  <a href="https://msdn.microsoft.com/1310a3f8-02dd-4d35-98ad-4016e57d1eb2">ResourceMap</a> function. </p>
</dd>

### -field <b>pfnCheckDirectFlipSupport</b>

<dd>
<p>A pointer to the driver's  <a href="https://msdn.microsoft.com/2acf84cb-5e51-4aa8-96ce-96abc6ceec8c">CheckDirectFlipSupport(D3D11_1)</a> function. </p>
</dd>

### -field <b>pfnClearView</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/c3cc08ea-22db-4fae-a180-76f3babd1c5c">ClearView</a>  function. </p>
</dd>

### -field <b>pfnUpdateTileMappings</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/1C8FC920-145F-4AE9-B049-F6BDAE29D1F1">UpdateTileMappings</a>  function. </p>
</dd>

### -field <b>pfnCopyTileMappings</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/CB2CE5E7-DDD4-4782-BB91-67A2C562A975">CopyTileMappings</a>  function. </p>
</dd>

### -field <b>pfnCopyTiles</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/8DA0FF6C-CA2C-4943-93C3-BFC3773617CC">CopyTiles</a>  function. </p>
</dd>

### -field <b>pfnUpdateTiles</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/4891AB01-DE51-4B32-AA52-5619E86CC474">UpdateTiles</a>  function. </p>
</dd>

### -field <b>pfnTiledResourceBarrier</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/9A2E9B3F-13E4-48D7-A3F3-E7CDCDD1E0CC">TiledResourceBarrier</a>  function. </p>
</dd>

### -field <b>pfnGetMipPacking</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/8AF361B5-279D-4525-AD98-843A4A746201">GetMipPacking</a>  function. </p>
</dd>

### -field <b>pfnResizeTilePool</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/184EF418-1B1E-4A10-8F10-1331DF99DCBD">ResizeTilePool</a>  function. </p>
</dd>

### -field <b>pfnSetMarker</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/BE618B0C-18E7-4B2B-87EB-172DAD9BCE15">SetMarker</a>  function. </p>
</dd>

### -field <b>pfnSetMarkerMode</b>

<dd>
<p>A pointer to the driver's <a href="https://msdn.microsoft.com/18B13509-7692-4336-937C-264B31A6FB78">SetMarkerMode</a>  function. </p>
</dd>
</dl>

## -remarks
<p>The order of user-mode display driver functions (that is, the order of the members of the <b>D3DWDDM1_3DDI_DEVICEFUNCS</b> structure) is in decreasing order of priority (in regard to performance).</p>

<p>The user-mode display driver can use different names for these functions because the address of the function table (this structure) is shared between the Direct3D 11.2 runtime and the driver through the call to the driver's <a href="https://msdn.microsoft.com/c69eedb1-c975-412c-aa9f-cf64a702f937">CreateDevice(D3D10)</a> function.</p>

<p>The <b>pfnResetPrimitiveID</b> and  <b>pfnSetVertexPipelineOutput</b> members (not shown here) and their data types are reserved for system use and should not be used in your driver.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 8.1</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>Windows Server 2012 R2</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>WDDM 1.3</p>
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
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh406443">D3D11_1DDI_DEVICEFUNCS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/BA2A1F90-6E30-4055-9374-943540AE2446">RelocateDeviceFuncs(D3D11_2)</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3DWDDM1_3DDI_DEVICEFUNCS structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>