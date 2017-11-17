---
UID: NC.d3dumddi.PFND3DDDI_UNLOCKCB
title: PFND3DDDI_UNLOCKCB
author: windows-driver-content
description: The pfnUnlockCb function unlocks an allocation that was locked by a call to the pfnLockCb function.
old-location: display\pfnunlockcb.htm
ms.assetid: 6684f350-da27-478d-ab7b-36e395f7df8d
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: display
req.header: d3dumddi.h
req.include-header: D3dumddi.h
req.target-type: Desktop
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: pfnUnlockCb
req.alt-loc: d3dumddi.h
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
ms.keywords: DXGK_MIRACAST_CHUNK_INFO, DXGK_MIRACAST_CHUNK_INFO
req.iface: 
---

# PFND3DDDI_UNLOCKCB callback



## -description
<p>The <b>pfnUnlockCb</b> function unlocks an allocation that was locked by a call to the <a href="https://msdn.microsoft.com/69022797-432a-410b-8cbf-e1ef7111e7ea">pfnLockCb</a> function. </p>


## -prototype

````
PFND3DDDI_UNLOCKCB pfnUnlockCb;

__checkReturn HRESULT APIENTRY pfnUnlockCb(
  _In_       HANDLE          hDevice,
  _In_ const D3DDDICB_UNLOCK *pData
)
{ ... }
````


## -parameters
<dl>

### -param <i>hDevice</i> [in]

<dd>
<p>A handle to the display device (graphics context).</p>
</dd>

### -param <i>pData</i> [in]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff544277">D3DDDICB_UNLOCK</a> structure that describes the allocation to unlock.</p>
</dd>
</dl>

## -returns
<p><b>pfnUnlockCb</b> returns one of the following values:</p><dl>
<dt><b>S_OK</b></dt>
</dl><p>The allocation was successfully unlocked.</p><dl>
<dt><b>E_OUTOFMEMORY</b></dt>
</dl><p><b>pfnUnlockCb</b> could not complete because of insufficient memory. (This error occurs when the system is in an extreme low memory situation and there is not sufficient space to allocate the array of pages.)</p><dl>
<dt><b>E_INVALIDARG</b></dt>
</dl><p>Parameters were validated and determined to be incorrect.</p>

<p> </p>

<p>This function might also return other HRESULT values.</p>

## -remarks
<p>The user-mode display driver must call the <b>pfnUnlockCb</b> function to unlock an allocation that was previously locked in a call to the <a href="https://msdn.microsoft.com/69022797-432a-410b-8cbf-e1ef7111e7ea">pfnLockCb</a> function. If the driver does not call <b>pfnUnlockCb</b>, coordination between the Microsoft Direct3D runtime, the user-mode display driver, and the display miniport driver is lost. </p>

<p>The user-mode display driver typically calls <b>pfnUnlockCb</b> in response to a call to its <a href="https://msdn.microsoft.com/23cc9c64-99d4-4602-a1b0-234fe7fcc3da">Unlock</a> or <a href="https://msdn.microsoft.com/fb2b714e-232d-40b2-88ad-ee8dcd70a057">ResourceUnmap</a> function (or other variations of <i>ResourceUnmap</i> such as <i>DynamicIABufferUnmap</i>) to unlock a resource or a surface within the resource. Before returning from the <i>Unlock</i> or <i>ResourceUnmap</i> call, the user-mode display driver must first map the resource or surface to the appropriate allocation and then call <b>pfnUnlockCb</b> to unlock the allocation. </p>

<p>The user-mode display driver can also call <b>pfnUnlockCb</b> in response to a call to its <a href="https://msdn.microsoft.com/a3c158c2-6c0d-4da0-80f4-569971b10673">DestroyDevice</a> or <a href="https://msdn.microsoft.com/90ada8c8-8ad8-4992-aac1-6eb7fdf3f249">DestroyDevice(D3D10)</a> function to free all of the resources that it allocated for the device. In the lifetime of a device, every call to <a href="https://msdn.microsoft.com/69022797-432a-410b-8cbf-e1ef7111e7ea">pfnLockCb</a> to lock an allocation must be paired with a call to the <b>pfnUnlockCb</b> function to unlock the allocation. </p>

<p>The user-mode display driver can unlock multiple allocations in one call to <b>pfnUnlockCb</b> by setting the <b>NumAllocations</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff544277">D3DDDICB_UNLOCK</a> structure to the number of allocations in the array that is specified by the <b>phAllocations</b> member of D3DDDICB_UNLOCK. </p>

<p>The user-mode display driver should call <b>pfnUnlockCb</b> to unlock all of the allocations that are referred to in the command stream before calling the <a href="https://msdn.microsoft.com/f242162e-6237-469c-b178-5a51dcf69e32">pfnRenderCb</a> function. The driver could have allocations locked to support--for example, the <b>NoOverwrite</b> bit-field flag. If the driver does not unlock all of these allocations, the video memory manager might be required to place these allocations in AGP memory. </p>

<p>The user-mode display driver should not call <b>pfnUnlockCb</b> to unlock an allocation that an application could be using. The driver is notified that the application is no longer reading from or writing to the allocation when the driver receives a call to its <a href="https://msdn.microsoft.com/23cc9c64-99d4-4602-a1b0-234fe7fcc3da">Unlock</a> or <a href="https://msdn.microsoft.com/fb2b714e-232d-40b2-88ad-ee8dcd70a057">ResourceUnmap</a> function on the corresponding resource. </p>

<p>The following code example shows how to unlock an allocation.</p>

<p>The user-mode display driver must call the <b>pfnUnlockCb</b> function to unlock an allocation that was previously locked in a call to the <a href="https://msdn.microsoft.com/69022797-432a-410b-8cbf-e1ef7111e7ea">pfnLockCb</a> function. If the driver does not call <b>pfnUnlockCb</b>, coordination between the Microsoft Direct3D runtime, the user-mode display driver, and the display miniport driver is lost. </p>

<p>The user-mode display driver typically calls <b>pfnUnlockCb</b> in response to a call to its <a href="https://msdn.microsoft.com/23cc9c64-99d4-4602-a1b0-234fe7fcc3da">Unlock</a> or <a href="https://msdn.microsoft.com/fb2b714e-232d-40b2-88ad-ee8dcd70a057">ResourceUnmap</a> function (or other variations of <i>ResourceUnmap</i> such as <i>DynamicIABufferUnmap</i>) to unlock a resource or a surface within the resource. Before returning from the <i>Unlock</i> or <i>ResourceUnmap</i> call, the user-mode display driver must first map the resource or surface to the appropriate allocation and then call <b>pfnUnlockCb</b> to unlock the allocation. </p>

<p>The user-mode display driver can also call <b>pfnUnlockCb</b> in response to a call to its <a href="https://msdn.microsoft.com/a3c158c2-6c0d-4da0-80f4-569971b10673">DestroyDevice</a> or <a href="https://msdn.microsoft.com/90ada8c8-8ad8-4992-aac1-6eb7fdf3f249">DestroyDevice(D3D10)</a> function to free all of the resources that it allocated for the device. In the lifetime of a device, every call to <a href="https://msdn.microsoft.com/69022797-432a-410b-8cbf-e1ef7111e7ea">pfnLockCb</a> to lock an allocation must be paired with a call to the <b>pfnUnlockCb</b> function to unlock the allocation. </p>

<p>The user-mode display driver can unlock multiple allocations in one call to <b>pfnUnlockCb</b> by setting the <b>NumAllocations</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff544277">D3DDDICB_UNLOCK</a> structure to the number of allocations in the array that is specified by the <b>phAllocations</b> member of D3DDDICB_UNLOCK. </p>

<p>The user-mode display driver should call <b>pfnUnlockCb</b> to unlock all of the allocations that are referred to in the command stream before calling the <a href="https://msdn.microsoft.com/f242162e-6237-469c-b178-5a51dcf69e32">pfnRenderCb</a> function. The driver could have allocations locked to support--for example, the <b>NoOverwrite</b> bit-field flag. If the driver does not unlock all of these allocations, the video memory manager might be required to place these allocations in AGP memory. </p>

<p>The user-mode display driver should not call <b>pfnUnlockCb</b> to unlock an allocation that an application could be using. The driver is notified that the application is no longer reading from or writing to the allocation when the driver receives a call to its <a href="https://msdn.microsoft.com/23cc9c64-99d4-4602-a1b0-234fe7fcc3da">Unlock</a> or <a href="https://msdn.microsoft.com/fb2b714e-232d-40b2-88ad-ee8dcd70a057">ResourceUnmap</a> function on the corresponding resource. </p>

<p>The following code example shows how to unlock an allocation.</p>

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
<dt>D3dumddi.h (include D3dumddi.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544277">D3DDDICB_UNLOCK</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544512">D3DDDI_DEVICECALLBACKS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/a3c158c2-6c0d-4da0-80f4-569971b10673">DestroyDevice</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/90ada8c8-8ad8-4992-aac1-6eb7fdf3f249">DestroyDevice(D3D10)</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/69022797-432a-410b-8cbf-e1ef7111e7ea">pfnLockCb</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/f242162e-6237-469c-b178-5a51dcf69e32">pfnRenderCb</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/fb2b714e-232d-40b2-88ad-ee8dcd70a057">ResourceUnmap</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/23cc9c64-99d4-4602-a1b0-234fe7fcc3da">Unlock</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20PFND3DDDI_UNLOCKCB callback function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>