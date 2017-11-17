---
UID: NS.ntddk._PCI_EXPRESS_SLOT_CAPABILITIES_REGISTER
title: PCI_EXPRESS_SLOT_CAPABILITIES_REGISTER
author: windows-driver-content
description: The PCI_EXPRESS_SLOT_CAPABILITIES_REGISTER structure describes a PCI Express (PCIe) slot capabilities register of a PCIe capability structure.
old-location: pci\pci_express_slot_capabilities_register.htm
ms.assetid: a5548777-a88e-40f8-891d-662e0892fd37
ms.author: windowsdriverdev
ms.date: 10/23/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: PCI
req.header: ntddk.h
req.include-header: Ntddk.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: PCI_EXPRESS_SLOT_CAPABILITIES_REGISTER
req.alt-loc: ntddk.h
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
ms.keywords: PCI_EXPRESS_SLOT_CAPABILITIES_REGISTER, PCI_EXPRESS_SLOT_CAPABILITIES_REGISTER, *PPCI_EXPRESS_SLOT_CAPABILITIES_REGISTER
req.iface: 
---

# PCI_EXPRESS_SLOT_CAPABILITIES_REGISTER structure



## -description
<p>The PCI_EXPRESS_SLOT_CAPABILITIES_REGISTER structure describes a PCI Express (PCIe) slot capabilities register of a PCIe capability structure.</p>


## -syntax

````
typedef union _PCI_EXPRESS_SLOT_CAPABILITIES_REGISTER {
  struct {
    ULONG AttentionButtonPresent  :1;
    ULONG PowerControllerPresent  :1;
    ULONG MRLSensorPresent  :1;
    ULONG AttentionIndicatorPresent  :1;
    ULONG PowerIndicatorPresent  :1;
    ULONG HotPlugSurprise  :1;
    ULONG HotPlugCapable  :1;
    ULONG SlotPowerLimit  :8;
    ULONG SlotPowerLimitScale  :2;
    ULONG ElectromechanicalLockPresent  :1;
    ULONG NoCommandCompletedSupport  :1;
    ULONG PhysicalSlotNumber  :13;
  };
  ULONG  AsULONG;
} PCI_EXPRESS_SLOT_CAPABILITIES_REGISTER, *PPCI_EXPRESS_SLOT_CAPABILITIES_REGISTER;
````


## -struct-fields
<dl>

### -field <b>AttentionButtonPresent</b>

<dd>
<p>A single bit that indicates that an attention button exists for the slot.</p>
</dd>

### -field <b>PowerControllerPresent</b>

<dd>
<p>A single bit that indicates that a software programmable power controller exists for the slot or for the adapter that is plugged into the slot.</p>
</dd>

### -field <b>MRLSensorPresent</b>

<dd>
<p>A single bit that indicates that a manually operated retention latch (MRL) sensor exists for the slot.</p>
</dd>

### -field <b>AttentionIndicatorPresent</b>

<dd>
<p>A single bit that indicates that an attention indicator exists for the slot.</p>
</dd>

### -field <b>PowerIndicatorPresent</b>

<dd>
<p>A single bit that indicates that a power indicator exists for the slot.</p>
</dd>

### -field <b>HotPlugSurprise</b>

<dd>
<p>A single bit that indicates that an adapter that is present in the slot can be removed from the system without any prior notification.</p>
</dd>

### -field <b>HotPlugCapable</b>

<dd>
<p>A single bit that indicates that the slot is capable of supporting hot-plug operations.</p>
</dd>

### -field <b>SlotPowerLimit</b>

<dd>
<p>The maximum amount of power that can be supplied by the slot. This value is used in combination with the value of the <b>SlotPowerLimitScale</b> member to compute the power in watts.</p>
</dd>

### -field <b>SlotPowerLimitScale</b>

<dd>
<p>The scale used for the value contained in the <b>SlotPowerLimit</b> member to compute the maximum power, in watts, that can be supplied by the slot. Possible values are:</p>
<p></p>
<dl>

### -field <a id="0"></a><b>0</b>

<dd>
<p>Multiply the value in the <b>SlotPowerLimit</b> member by 1.0.</p>
</dd>

### -field <a id="1"></a><b>1</b>

<dd>
<p>Multiply the value in the <b>SlotPowerLimit</b> member by 0.1.</p>
</dd>

### -field <a id="2"></a><b>2</b>

<dd>
<p>Multiply the value in the <b>SlotPowerLimit</b> member by 0.01.</p>
</dd>

### -field <a id="3"></a><b>3</b>

<dd>
<p>Multiply the value in the <b>SlotPowerLimit</b> member by 0.001.</p>
</dd>
</dl>
</dd>

### -field <b>ElectromechanicalLockPresent</b>

<dd>
<p>A single bit that indicates that an electromechanical interlock exists for the slot.</p>
</dd>

### -field <b>NoCommandCompletedSupport</b>

<dd>
<p>A single bit that indicates that the slot does not generate software notification when an issued command is completed by the hot-plug controller.</p>
</dd>

### -field <b>PhysicalSlotNumber</b>

<dd>
<p>The physical slot number in the system chassis that is attached to this port. This value is zero for ports that are connected to devices that are either integrated on the system board or integrated within the same physical component as the switch device or root port.</p>
</dd>

### -field <b>AsULONG</b>

<dd>
<p>A ULONG representation of the contents of the PCI_EXPRESS_SLOT_CAPABILITIES_REGISTER structure.</p>
</dd>
</dl>

## -remarks
<p>The PCI_EXPRESS_SLOT_CAPABILITIES_REGISTER structure is available in Windows Server 2008 and later versions of Windows.</p>

<p>A PCI_EXPRESS_SLOT_CAPABILITIES_REGISTER structure is contained in the <a href="https://msdn.microsoft.com/library/windows/hardware/ff537460">PCI_EXPRESS_CAPABILITY</a> structure.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntddk.h (include Ntddk.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff537460">PCI_EXPRESS_CAPABILITY</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [PCI\buses]:%20PCI_EXPRESS_SLOT_CAPABILITIES_REGISTER union%20 RELEASE:%20(10/23/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>