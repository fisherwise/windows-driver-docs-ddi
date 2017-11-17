---
UID: NC.pcivirt.SRIOV_WRITE_BLOCK
title: SRIOV_WRITE_BLOCK
author: windows-driver-content
description: Writes data to the specified configuration block of a PCI Express SR-IOV Virtual Function (VF).
old-location: pci\sriov_write_block.htm
ms.assetid: da47d601-2fab-49bb-b669-909a2e5c95c0
ms.author: windowsdriverdev
ms.date: 10/23/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: PCI
req.header: pcivirt.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: *PSRIOV_WRITE_BLOCK
req.alt-loc: Pcivirt.h
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
ms.keywords: PARCLASS_INFORMATION, PARCLASS_INFORMATION, *PPARCLASS_INFORMATION
req.iface: 
---

# SRIOV_WRITE_BLOCK callback



## -description
<p>Writes data to the specified configuration block of a PCI Express SR-IOV Virtual Function (VF).</p>


## -prototype

````
SRIOV_WRITE_BLOCK SriovWriteBlock;

NTSTATUS SriovWriteBlock(
  _In_ PVOID  Context,
  _In_ USHORT VfIndex,
  _In_ ULONG  BlockId,
  _In_ PVOID  Buffer,
       ULONG  Length
)
{ ... }

typedef SRIOV_WRITE_BLOCK *PSRIOV_WRITE_BLOCK;
````


## -parameters
<dl>

### -param <i>Context</i> [in]

<dd>
<p>A pointer to a driver-defined context.
                    
                </p>
</dd>

### -param <i>VfIndex</i> [in]

<dd>
<p>A zero-based index of the VF to which this write operation applies.</p>
</dd>

### -param <i>BlockId</i> [in]

<dd>
<p>A number identifying the block to be written.  This is defined by the provider of the PF driver.</p>
</dd>

### -param <i>Buffer</i> [in]

<dd>
<p>A pointer to a buffer that contains the data to write to the VF's  configuration space.</p>
</dd>

### -param <i>Length</i> 

<dd>
<p>The length in bytes of this write operation.  Must not be greater than VPCI_MAX_READ_WRITE_BLOCK_SIZE defined in Pcivirt.h.</p>
</dd>
</dl>

## -returns
<p>
Return STATUS_SUCCESS if the operation succeeds. Otherwise, return an appropriate <a href="https://msdn.microsoft.com/7792201b-63bb-4db5-803d-2af02893d505">NTSTATUS</a> error code.</p>

## -remarks
<p>This callback function is implemented by the physical function (PF) driver. It is invoked  when the system wants to read a configuration block for one of its VFs.</p>

<p>The PF driver registers its implementation by setting the <b>WriteVfConfigBlock</b> member of the <a href="buses._sriov_device_interface_standard">SRIOV_DEVICE_INTERFACE_STANDARD</a>, configuring a <a href="https://msdn.microsoft.com/library/windows/hardware/ff552439">WDF_QUERY_INTERFACE_CONFIG</a> structure, and calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff545870">WdfDeviceAddQueryInterface</a>.</p>

<p>This callback function is implemented by the physical function (PF) driver. It is invoked  when the system wants to read a configuration block for one of its VFs.</p>

<p>The PF driver registers its implementation by setting the <b>WriteVfConfigBlock</b> member of the <a href="buses._sriov_device_interface_standard">SRIOV_DEVICE_INTERFACE_STANDARD</a>, configuring a <a href="https://msdn.microsoft.com/library/windows/hardware/ff552439">WDF_QUERY_INTERFACE_CONFIG</a> structure, and calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff545870">WdfDeviceAddQueryInterface</a>.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 10</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>Windows Server 2016</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Pcivirt.h</dt>
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