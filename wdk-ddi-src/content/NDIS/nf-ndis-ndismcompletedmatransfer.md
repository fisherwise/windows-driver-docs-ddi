---
UID: NF.ndis.NdisMCompleteDmaTransfer
title: NdisMCompleteDmaTransfer
author: windows-driver-content
description: The NdisMCompleteDmaTransfer function indicates that a system DMA transfer operation has completed. It resets the system DMA controller in preparation for further DMA transfers.
old-location: netvista\ndismcompletedmatransfer.htm
ms.assetid: 12a8062a-6d4b-4757-a076-56aeb5e4e48c
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: netvista
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Universal
req.target-min-winverclnt: Supported for NDIS 6.0 and NDIS 5.1 drivers (see 
   NdisMCompleteDmaTransfer (NDIS
   5.1)) in Windows Vista. Supported for NDIS 5.1 drivers (see 
   NdisMCompleteDmaTransfer (NDIS
   5.1)) in Windows XP.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NdisMCompleteDmaTransfer
req.alt-loc: ndis.h
req.ddi-compliance: Irql_MCO_Function
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: <= DISPATCH_LEVEL
ms.keywords: NdisMCompleteDmaTransfer
req.iface: 
---

# NdisMCompleteDmaTransfer function



## -description
<p>The 
  <b>NdisMCompleteDmaTransfer</b> function indicates that a system DMA transfer operation has completed. It
  resets the system DMA controller in preparation for further DMA transfers.</p>


## -syntax

````
VOID NdisMCompleteDmaTransfer(
  _Out_ PNDIS_STATUS Status,
  _In_  NDIS_HANDLE  MiniportDmaHandle,
  _In_  PNDIS_BUFFER Buffer,
  _In_  ULONG        Offset,
  _In_  ULONG        Length,
  _In_  BOOLEAN      WriteToDevice
);
````


## -parameters
<dl>

### -param <i>Status</i> [out]

<dd>
<p>A pointer to a caller-supplied variable in which this function returns the final status of the DMA
     transfer, which can be one of the following:
     </p>
<p></p>
<dl>

### -param <a id="NDIS_STATUS_SUCCESS"></a><a id="ndis_status_success"></a>NDIS_STATUS_SUCCESS

<dd>
<p>The data has been transferred and flushed to host memory or to the device to maintain data
       integrity.</p>
</dd>

### -param <a id="NDIS_STATUS_RESOURCES"></a><a id="ndis_status_resources"></a>NDIS_STATUS_RESOURCES

<dd>
<p>The DMA controller was released but the data transfer might be incoherent.</p>
</dd>
</dl>
</dd>

### -param <i>MiniportDmaHandle</i> [in]

<dd>
<p>The handle returned when the 
     <a href="https://msdn.microsoft.com/b146fa81-005b-4a6c-962d-4cb023ea790e">MiniportInitializeEx</a> function
     called the 
     <a href="https://msdn.microsoft.com/32e92f77-8f45-408b-a284-c00d3b5bd1b4">
     NdisMRegisterDmaChannel</a> function.</p>
</dd>

### -param <i>Buffer</i> [in]

<dd>
<p>A pointer to the buffer descriptor previously passed to 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff563675">NdisMSetupDmaTransfer</a>.</p>
</dd>

### -param <i>Offset</i> [in]

<dd>
<p>The byte offset at which the transfer began. This value also was passed to 
     <b>NdisMSetupDmaTransfer</b>.</p>
</dd>

### -param <i>Length</i> [in]

<dd>
<p>The length in bytes of the transfer. This value also was passed to 
     <b>NdisMSetupDmaTransfer</b>.</p>
</dd>

### -param <i>WriteToDevice</i> [in]

<dd>
<p><b>TRUE</b> if the transfer was from the host to the NIC, as, for example, a send operation.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p><b>NdisMCompleteDmaTransfer</b> must be called with 
    <i>WriteToDevice</i> set to <b>TRUE</b> before the transferred data is considered present in the NIC's memory. 
    <b>NdisMCompleteDmaTransfer</b> must be called with 
    <i>WriteToDevice</i> set to <b>FALSE</b> before the transferred data can be read from host memory.</p>

<p><b>NdisMCompleteDmaTransfer</b> must be called with 
    <i>WriteToDevice</i> set to <b>TRUE</b> before the transferred data is considered present in the NIC's memory. 
    <b>NdisMCompleteDmaTransfer</b> must be called with 
    <i>WriteToDevice</i> set to <b>FALSE</b> before the transferred data can be read from host memory.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt><a href="http://go.microsoft.com/fwlink/p/?linkid=531356" target="_blank">Universal</a></dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Supported for NDIS 6.0 and NDIS 5.1 drivers (see 
   <a href="https://msdn.microsoft.com/e9b25a34-2f6d-4fec-a4df-37708ae87dfd">NdisMCompleteDmaTransfer (NDIS
   5.1)</a>) in Windows Vista. Supported for NDIS 5.1 drivers (see 
   <b>NdisMCompleteDmaTransfer (NDIS
   5.1)</b>) in Windows XP.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ndis.h (include Ndis.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&lt;= DISPATCH_LEVEL</p>
</td>
</tr>
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547971">Irql_MCO_Function</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/b146fa81-005b-4a6c-962d-4cb023ea790e">MiniportInitializeEx</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563646">NdisMRegisterDmaChannel</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563675">NdisMSetupDmaTransfer</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NdisMCompleteDmaTransfer function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>