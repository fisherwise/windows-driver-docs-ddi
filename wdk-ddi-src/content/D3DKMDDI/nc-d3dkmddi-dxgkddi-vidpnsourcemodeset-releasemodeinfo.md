---
UID: NC.d3dkmddi.DXGKDDI_VIDPNSOURCEMODESET_RELEASEMODEINFO
title: DXGKDDI_VIDPNSOURCEMODESET_RELEASEMODEINFO
author: windows-driver-content
description: The pfnReleaseModeInfo function releases a D3DKMDT_VIDPN_SOURCE_MODE structure that the VidPN manager previously provided to the display miniport driver.
old-location: display\dxgk_vidpnsourcemodeset_interface_pfnreleasemodeinfo.htm
ms.assetid: 614283cc-90bf-44f2-bab2-1aeec5e7de01
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmddi.h
req.include-header: D3dkmddi.h
req.target-type: Desktop
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: pfnReleaseModeInfo
req.alt-loc: d3dkmddi.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: DD_MULTISAMPLEQUALITYLEVELSDATA, DD_MULTISAMPLEQUALITYLEVELSDATA
req.iface: 
---

# DXGKDDI_VIDPNSOURCEMODESET_RELEASEMODEINFO callback



## -description
<p>The <b>pfnReleaseModeInfo</b> function releases a <a href="https://msdn.microsoft.com/library/windows/hardware/ff546724">D3DKMDT_VIDPN_SOURCE_MODE</a> structure that the VidPN manager previously provided to the display miniport driver.</p>


## -prototype

````
DXGKDDI_VIDPNSOURCEMODESET_RELEASEMODEINFO pfnReleaseModeInfo;

NTSTATUS APIENTRY pfnReleaseModeInfo(
  _In_ const D3DKMDT_HVIDPNSOURCEMODESET     hVidPnSourceModeSet,
  _In_ const D3DKMDT_VIDPN_SOURCE_MODE CONST *pVidPnSourceModeInfo
)
{ ... }
````


## -parameters
<dl>

### -param <i>hVidPnSourceModeSet</i> [in]

<dd>
<p>[in] A handle to a VidPN source mode set object. The display miniport driver previously obtained this handle by calling the <a href="https://msdn.microsoft.com/cf19f468-86c1-4cc9-8945-e23f73a85c91">pfnAcquireSourceModeSet</a> function of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff562108">DXGK_VIDPN_INTERFACE</a> interface.</p>
</dd>

### -param <i>pVidPnSourceModeInfo</i> [in]

<dd>
<p>[in] A pointer to the D3DKMDT_VIDPN_SOURCE_MODE structure that is to be released.</p>
</dd>
</dl>

## -returns
<p>The <b>pfnReleaseModeInfo</b> function returns one of the following values:</p><dl>
<dt><b>STATUS_SUCCESS</b></dt>
</dl><p>The function succeeded. </p><dl>
<dt><b>STATUS_GRAPHICS_INVALID_VIDPN_SOURCEMODESET</b></dt>
</dl><p>The handle supplied in <i>hVidPnSourceModeSet</i> was invalid.</p><dl>
<dt><b>STATUS_GRAPHICS_INVALID_VIDEO_PRESENT_SOURCE_MODE</b></dt>
</dl><p>The pointer supplied in <i>pVidPnSourceModeInfo </i>was invalid.</p>

<p> </p>

## -remarks
<p>When you have finished using a D3DKMDT_VIDPN_SOURCE_MODE structure that you obtained by calling any of the following functions, you must release the structure by calling <b>pfnReleaseModeInfo</b>.</p>

<p>
<a href="https://msdn.microsoft.com/3af816e0-f1a4-4477-8735-6400aadfb57b">pfnAcquireFirstModeInfo</a>
</p>

<p>
<a href="https://msdn.microsoft.com/d9cb1ff1-c428-46e5-884a-5fc39e16300e">pfnAcquireNextModeInfo</a>
</p>

<p>
<a href="https://msdn.microsoft.com/e757852b-ee68-4b07-83c8-9dfd089d1ab7">pfnAcquirePinnedModeInfo</a>
</p>

<p>If you obtain a D3DKMDT_VIDPN_SOURCE_MODE structure by calling <a href="https://msdn.microsoft.com/b18aab68-7457-45eb-8641-0b6180cfa70e">pfnCreateNewModeInfo</a> and then pass that structure to <a href="https://msdn.microsoft.com/754078c2-f79b-4237-a14c-96903856f3a5">pfnAddMode</a>, you do not need to release the structure.</p>

<p>If you obtain a handle by calling <b>pfnCreateNewModeInfo</b> and then you decide not to add the new mode to a source mode set, you must release the newly created structure by calling <b>pfnReleaseModeInfo</b>.</p>

<p>The D3DKMDT_HVIDPNSOURCEMODESET data type is defined in <i>D3dkmdt.h</i>. </p>

<p>When you have finished using a D3DKMDT_VIDPN_SOURCE_MODE structure that you obtained by calling any of the following functions, you must release the structure by calling <b>pfnReleaseModeInfo</b>.</p>

<p>
<a href="https://msdn.microsoft.com/3af816e0-f1a4-4477-8735-6400aadfb57b">pfnAcquireFirstModeInfo</a>
</p>

<p>
<a href="https://msdn.microsoft.com/d9cb1ff1-c428-46e5-884a-5fc39e16300e">pfnAcquireNextModeInfo</a>
</p>

<p>
<a href="https://msdn.microsoft.com/e757852b-ee68-4b07-83c8-9dfd089d1ab7">pfnAcquirePinnedModeInfo</a>
</p>

<p>If you obtain a D3DKMDT_VIDPN_SOURCE_MODE structure by calling <a href="https://msdn.microsoft.com/b18aab68-7457-45eb-8641-0b6180cfa70e">pfnCreateNewModeInfo</a> and then pass that structure to <a href="https://msdn.microsoft.com/754078c2-f79b-4237-a14c-96903856f3a5">pfnAddMode</a>, you do not need to release the structure.</p>

<p>If you obtain a handle by calling <b>pfnCreateNewModeInfo</b> and then you decide not to add the new mode to a source mode set, you must release the newly created structure by calling <b>pfnReleaseModeInfo</b>.</p>

<p>The D3DKMDT_HVIDPNSOURCEMODESET data type is defined in <i>D3dkmdt.h</i>. </p>

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
<dt>D3dkmddi.h (include D3dkmddi.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>PASSIVE_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/3af816e0-f1a4-4477-8735-6400aadfb57b">pfnAcquireFirstModeInfo</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/d9cb1ff1-c428-46e5-884a-5fc39e16300e">pfnAcquireNextModeInfo</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/e757852b-ee68-4b07-83c8-9dfd089d1ab7">pfnAcquirePinnedModeInfo</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546724">D3DKMDT_VIDPN_SOURCE_MODE</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20DXGKDDI_VIDPNSOURCEMODESET_RELEASEMODEINFO callback function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>