---
UID: NC.d3dumddi.PFND3DDDI_CLOSEADAPTER
title: PFND3DDDI_CLOSEADAPTER
author: windows-driver-content
description: The CloseAdapter function releases resources for a graphics adapter object.
old-location: display\closeadapter.htm
ms.assetid: 9dc7f71a-753d-41ca-8eaa-bff6536e834f
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
req.alt-api: CloseAdapter
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

# PFND3DDDI_CLOSEADAPTER callback



## -description
<p>The <b>CloseAdapter</b> function releases resources for a graphics adapter object.</p>


## -prototype

````
PFND3DDDI_CLOSEADAPTER CloseAdapter;

__checkReturn HRESULT APIENTRY CloseAdapter(
  _In_ HANDLE hAdapter
)
{ ... }
````


## -parameters
<dl>

### -param <i>hAdapter</i> [in]

<dd>
<p> A handle to the graphics adapter object that was created with the <a href="https://msdn.microsoft.com/41dc9ee4-e9bc-4ebd-9b90-6446ded6ea16">OpenAdapter</a> function.</p>
</dd>
</dl>

## -returns
<p><b>CloseAdapter</b> returns S_OK if the operation succeeds. Otherwise, this function returns an appropriate error result. </p>

## -remarks
<p>The user-mode display driver's <b>CloseAdapter</b> function should free all of the resources that it allocated for the graphics adapter object.</p>

<p>Before <b>CloseAdapter</b> closes the graphics adapter object, all of the display devices that were created by using the graphics adapter object in calls to the user-mode display driver's <a href="https://msdn.microsoft.com/ce35bdac-af90-471f-af93-0e665be6c7f6">CreateDevice</a> function must be destroyed in calls to the driver's <a href="https://msdn.microsoft.com/a3c158c2-6c0d-4da0-80f4-569971b10673">DestroyDevice</a> function.</p>

<p>The user-mode display driver's <b>CloseAdapter</b> function should free all of the resources that it allocated for the graphics adapter object.</p>

<p>Before <b>CloseAdapter</b> closes the graphics adapter object, all of the display devices that were created by using the graphics adapter object in calls to the user-mode display driver's <a href="https://msdn.microsoft.com/ce35bdac-af90-471f-af93-0e665be6c7f6">CreateDevice</a> function must be destroyed in calls to the driver's <a href="https://msdn.microsoft.com/a3c158c2-6c0d-4da0-80f4-569971b10673">DestroyDevice</a> function.</p>

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
<a href="https://msdn.microsoft.com/ce35bdac-af90-471f-af93-0e665be6c7f6">CreateDevice</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544355">D3DDDI_ADAPTERFUNCS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/a3c158c2-6c0d-4da0-80f4-569971b10673">DestroyDevice</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/41dc9ee4-e9bc-4ebd-9b90-6446ded6ea16">OpenAdapter</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20PFND3DDDI_CLOSEADAPTER callback function%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>