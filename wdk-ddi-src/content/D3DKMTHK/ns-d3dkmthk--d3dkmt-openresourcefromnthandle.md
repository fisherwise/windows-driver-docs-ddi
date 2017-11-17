---
UID: NS.d3dkmthk._D3DKMT_OPENRESOURCEFROMNTHANDLE
title: D3DKMT_OPENRESOURCEFROMNTHANDLE
author: windows-driver-content
description: Describes information that is required to open a shared resource from an NT handle to the process. The shared resource can be a set of allocations, a keyed mutex, or a synchronization object.
old-location: display\d3dkmt_openresourcefromnthandle.htm
ms.assetid: 3f595816-29b5-4efc-a00c-77597dd9fa48
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmthk.h
req.include-header: D3dkmthk.h
req.target-type: Windows
req.target-min-winverclnt: Windows 8
req.target-min-winversvr: Windows Server 2012
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3DKMT_OPENRESOURCEFROMNTHANDLE
req.alt-loc: D3dkmthk.h
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
ms.keywords: D3DKMT_OPENRESOURCEFROMNTHANDLE, D3DKMT_OPENRESOURCEFROMNTHANDLE
req.iface: 
---

# D3DKMT_OPENRESOURCEFROMNTHANDLE structure



## -description
<p>Describes information that is required to open a shared resource from an NT handle to the process. The shared resource can be a set of allocations, a keyed mutex, or a synchronization object.</p>


## -syntax

````
typedef struct _D3DKMT_OPENRESOURCEFROMNTHANDLE {
  D3DKMT_HANDLE              hDevice;
  HANDLE                     hNtHandle;
  UINT                       NumAllocations;
  D3DDDI_OPENALLOCATIONINFO2 *pOpenAllocationInfo2;
  UINT                       PrivateRuntimeDataSize;
  VOID                       *pPrivateRuntimeData;
  UINT                       ResourcePrivateDriverDataSize;
  VOID                       *pResourcePrivateDriverData;
  UINT                       TotalPrivateDriverDataBufferSize;
  VOID                       *pTotalPrivateDriverDataBuffer;
  D3DKMT_HANDLE              hResource;
  D3DKMT_HANDLE              hKeyedMutex;
  VOID                       *pKeyedMutexPrivateRuntimeData;
  UINT                       KeyedMutexPrivateRuntimeDataSize;
  D3DKMT_HANDLE              hSyncObject;
} D3DKMT_OPENRESOURCEFROMNTHANDLE;
````


## -struct-fields
<dl>

### -field <b>hDevice</b>

<dd>
<p>[in] A D3DKMT_HANDLE data type that represents the device.</p>
</dd>

### -field <b>hNtHandle</b>

<dd>
<p>[in] An NT handle to the process.</p>
</dd>

### -field <b>NumAllocations</b>

<dd>
<p>[in] The number of allocations associated with the resource.</p>
</dd>

### -field <b>pOpenAllocationInfo2</b>

<dd>
<p>[in] This member is reserved and should be set to zero.</p>
</dd>

### -field <b>PrivateRuntimeDataSize</b>

<dd>
<p>[in] The size, in bytes, of the buffer pointed to by the <b>pPrivateRuntimeData</b> member.</p>
</dd>

### -field <b>pPrivateRuntimeData</b>

<dd>
<p>[in] A caller-supplied buffer where the runtime private data associated with this resource will be copied to.</p>
</dd>

### -field <b>ResourcePrivateDriverDataSize</b>

<dd>
<p>[in] The size, in bytes, of the  buffer pointed to by the <b>pResourcePrivateDriverData</b> member.</p>
</dd>

### -field <b>pResourcePrivateDriverData</b>

<dd>
<p>[in] A caller-supplied buffer where the driver private data associated with the resource will be copied to.</p>
</dd>

### -field <b>TotalPrivateDriverDataBufferSize</b>

<dd>
<p>[in] The size, in bytes, of the buffer pointed to by the <b>pTotalPrivateDriverDataBuffer</b> member.</p>
<p>[out] The size, in bytes, of  the data written to <b>pTotalPrivateDriverDataBuffer</b>.</p>
</dd>

### -field <b>pTotalPrivateDriverDataBuffer</b>

<dd>
<p>[in] A pointer to a caller-supplied buffer where the driver private data will be stored.</p>
</dd>

### -field <b>hResource</b>

<dd>
<p>[out] A handle to the resource in this process.</p>
</dd>

### -field <b>hKeyedMutex</b>

<dd>
<p>[out] A handle to the keyed mutex in this process.</p>
</dd>

### -field <b>pKeyedMutexPrivateRuntimeData</b>

<dd>
<p>[in] A buffer that contains initial private data.</p>
<p>The data in this buffer will be copied only if the keyed mutex does not already have private data.</p>
<p>If this member has a value of <b>NULL</b>, the value of the <b>KeyedMutexPrivateRuntimeDataSize</b> member must be zero.</p>
</dd>

### -field <b>KeyedMutexPrivateRuntimeDataSize</b>

<dd>
<p>[in] The size, in bytes, of the buffer pointed to by the <b>pKeyedMutexPrivateRuntimeData</b> member.</p>
</dd>

### -field <b>hSyncObject</b>

<dd>
<p>[out] A handle to the synchronization object in this process.</p>
</dd>
</dl>

## -remarks


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
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>D3dkmthk.h (include D3dkmthk.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh439280">D3DDDI_OPENALLOCATIONINFO2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh439409">D3DKMTOpenNtHandleFromName</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh780251">D3DKMTShareObjects</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20D3DKMT_OPENRESOURCEFROMNTHANDLE structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>