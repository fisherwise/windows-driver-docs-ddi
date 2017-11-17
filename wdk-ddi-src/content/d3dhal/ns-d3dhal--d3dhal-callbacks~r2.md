---
UID: NS.d3dhal._D3DHAL_CALLBACKS~r2
title: D3DHAL_CALLBACKS
author: windows-driver-content
description: D3DHAL_CALLBACKS is one of several callback structures that describe the Direct3D support provided by the driver.
old-location: display\d3dhal_callbacks.htm
ms.assetid: 3b045732-a41f-47e7-9835-41e3ef54f14c
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3dhal.h
req.include-header: D3dhal.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3DHAL_CALLBACKS
req.alt-loc: d3dhal.h
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
ms.keywords: D3DHAL_CALLBACKS, D3DHAL_CALLBACKS
req.iface: 
---

# D3DHAL_CALLBACKS structure



## -description
<p>D3DHAL_CALLBACKS is one of several callback structures that describe the Direct3D support provided by the driver.</p>


## -syntax

````
typedef struct _D3DHAL_CALLBACKS {
  DWORD                        dwSize;
  LPD3DHAL_CONTEXTCREATECB     ContextCreate;
  LPD3DHAL_CONTEXTDESTROYCB    ContextDestroy;
  LPD3DHAL_CONTEXTDESTROYALLCB ContextDestroyAll;
  LPD3DHAL_SCENECAPTURECB      SceneCapture;
  LPVOID                       lpReserved10;
  LPVOID                       lpReserved11;
  LPD3DHAL_RENDERSTATECB       RenderState;
  LPD3DHAL_RENDERPRIMITIVECB   RenderPrimitive;
  DWORD                        dwReserved;
  LPD3DHAL_TEXTURECREATECB     TextureCreate;
  LPD3DHAL_TEXTUREDESTROYCB    TextureDestroy;
  LPD3DHAL_TEXTURESWAPCB       TextureSwap;
  LPD3DHAL_TEXTUREGETSURFCB    TextureGetSurf;
  LPVOID                       lpReserved12;
  LPVOID                       lpReserved13;
  LPVOID                       lpReserved14;
  LPVOID                       lpReserved15;
  LPVOID                       lpReserved16;
  LPVOID                       lpReserved17;
  LPVOID                       lpReserved18;
  LPVOID                       lpReserved19;
  LPVOID                       lpReserved20;
  LPVOID                       lpReserved21;
  LPD3DHAL_GETSTATECB          GetState;
  DWORD                        dwReserved0;
  DWORD                        dwReserved1;
  DWORD                        dwReserved2;
  DWORD                        dwReserved3;
  DWORD                        dwReserved4;
  DWORD                        dwReserved5;
  DWORD                        dwReserved6;
  DWORD                        dwReserved7;
  DWORD                        dwReserved8;
  DWORD                        dwReserved9;
} D3DHAL_CALLBACKS, *LPD3DHAL_CALLBACKS;
````


## -struct-fields
<dl>

### -field <b>dwSize</b>

<dd>
<p>Specifies the size in bytes of this D3DHAL_CALLBACKS structure.</p>
</dd>

### -field <b>ContextCreate</b>

<dd>
<p>Points to the driver-supplied <a href="https://msdn.microsoft.com/c960c3f4-7565-4163-b8c2-a13643110c8c">D3dContextCreate</a> callback. A driver must implement the callback that this member points to.</p>
</dd>

### -field <b>ContextDestroy</b>

<dd>
<p>Points to the driver-supplied <a href="https://msdn.microsoft.com/caed780c-06a1-4697-b102-bffb134ecf84">D3dContextDestroy</a> callback. A driver must implement the callback that this member points to.</p>
</dd>

### -field <b>ContextDestroyAll</b>

<dd>
<p>Must be set to <b>NULL</b> in a Windows 2000 and later driver.</p>
</dd>

### -field <b>SceneCapture</b>

<dd>
<p>Must be set to <b>NULL</b> in a Windows 2000 and later driver. For DirectX 6.0, this was a pointer to the driver-supplied <b>D3dSceneCapture</b> callback. For DirectX 7.0 and later, this callback was replaced by the handling of the D3DRENDERSTATE_SCENECAPTURE render state in the <a href="https://msdn.microsoft.com/6128ff7a-0d2c-48df-8b5e-cab33c5a74f5">D3dDrawPrimitives2</a> function.</p>
</dd>

### -field <b>lpReserved10</b>

<dd>
<p>Must be zero.</p>
</dd>

### -field <b>lpReserved11</b>

<dd>
<p>Must be zero.</p>
</dd>

### -field <b>RenderState</b>

<dd>
<p>Points to the driver-supplied D3DHAL_RENDERSTATEDATA callback. A driver must implement the callback that this member points to.</p>
</dd>

### -field <b>RenderPrimitive</b>

<dd>
<p>Points to the driver-supplied D3DHAL_RENDERPRIMITIVEDATA callback. A driver must implement the callback that this member points to.</p>
</dd>

### -field <b>dwReserved</b>

<dd>
<p>Specifies reserved fields and must be set to zero.</p>
</dd>

### -field <b>TextureCreate</b>

<dd>
<p>Must be set to <b>NULL</b> in a Windows 2000 and later driver. For DirectX 6.0, this was a pointer to the driver-supplied <b>D3dTextureCreate</b> callback, or <b>NULL</b>. </p>
</dd>

### -field <b>TextureDestroy</b>

<dd>
<p>Must be set to <b>NULL</b> in a Windows 2000 and later driver. For DirectX 6.0, this was a pointer to the driver-supplied <b>D3dTextureDestroy</b> callback, or <b>NULL</b>.</p>
</dd>

### -field <b>TextureSwap</b>

<dd>
<p>Must be set to <b>NULL</b> in a Windows 2000 and later driver. For DirectX 6.0, this was a pointer to the driver-supplied <b>D3dTextureSwap</b> callback, or <b>NULL</b>.</p>
</dd>

### -field <b>TextureGetSurf</b>

<dd>
<p>Must be set to <b>NULL</b> in a Windows 2000 and later driver. For DirectX 6.0, this was a pointer to the driver-supplied <b>D3dTextureGetSurf</b> callback, or <b>NULL</b>.</p>
</dd>

### -field <b>lpReserved12</b>

<dd>
<p>Must be zero.</p>
</dd>

### -field <b>lpReserved13</b>

<dd>
<p>Must be zero.</p>
</dd>

### -field <b>lpReserved14</b>

<dd>
<p>Must be zero.</p>
</dd>

### -field <b>lpReserved15</b>

<dd>
<p>Must be zero.</p>
</dd>

### -field <b>lpReserved16</b>

<dd>
<p>Must be zero.</p>
</dd>

### -field <b>lpReserved17</b>

<dd>
<p>Must be zero.</p>
</dd>

### -field <b>lpReserved18</b>

<dd>
<p>Must be zero.</p>
</dd>

### -field <b>lpReserved19</b>

<dd>
<p>Must be zero.</p>
</dd>

### -field <b>lpReserved20</b>

<dd>
<p>Must be zero.</p>
</dd>

### -field <b>lpReserved21</b>

<dd>
<p>Must be zero.</p>
</dd>

### -field <b>GetState</b>

<dd>
<p>Points to the driver-supplied D3DHAL_GETSTATEDATA callback. A driver must implement the callback that this member points to.</p>
</dd>

### -field <b>dwReserved0</b>

<dd>
<p>Must be zero.</p>
</dd>

### -field <b>dwReserved1</b>

<dd>
<p>Must be zero.</p>
</dd>

### -field <b>dwReserved2</b>

<dd>
<p>Must be zero.</p>
</dd>

### -field <b>dwReserved3</b>

<dd>
<p>Must be zero.</p>
</dd>

### -field <b>dwReserved4</b>

<dd>
<p>Must be zero.</p>
</dd>

### -field <b>dwReserved5</b>

<dd>
<p>Must be zero.</p>
</dd>

### -field <b>dwReserved6</b>

<dd>
<p>Must be zero.</p>
</dd>

### -field <b>dwReserved7</b>

<dd>
<p>Must be zero.</p>
</dd>

### -field <b>dwReserved8</b>

<dd>
<p>Must be zero</p>
</dd>

### -field <b>dwReserved9</b>

<dd>
<p>Must be zero.</p>
</dd>
</dl>

## -remarks
<p>The driver allocates this structure and sets appropriate values in all members. The driver's <a href="https://msdn.microsoft.com/library/windows/hardware/ff556229">DrvGetDirectDrawInfo</a> function returns a pointer to this structure in the <b>lpD3DHALCallbacks</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff551627">DD_HALINFO</a> structure.</p>

<p>Texture management is now handled though opcodes that are managed in the driver's implementation of <a href="https://msdn.microsoft.com/6128ff7a-0d2c-48df-8b5e-cab33c5a74f5">D3dDrawPrimitives2</a>.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>D3dhal.h (include D3dhal.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/c960c3f4-7565-4163-b8c2-a13643110c8c">D3dContextCreate</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/caed780c-06a1-4697-b102-bffb134ecf84">D3dContextDestroy</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/6128ff7a-0d2c-48df-8b5e-cab33c5a74f5">D3dDrawPrimitives2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544723">D3DHAL_CALLBACKS3</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/89a22163-a678-4c72-932a-ae4d17922e0b">DdGetDriverInfo</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff556229">DrvGetDirectDrawInfo</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3DHAL_CALLBACKS structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>