---
UID: NS.wdm._IO_INTERRUPT_MESSAGE_INFO_ENTRY
title: IO_INTERRUPT_MESSAGE_INFO_ENTRY
author: windows-driver-content
description: The IO_INTERRUPT_MESSAGE_INFO_ENTRY structure describes the properties of a single message-signaled interrupt.
old-location: kernel\io_interrupt_message_info_entry.htm
ms.assetid: e5007381-2436-4eb6-85cd-7145361ab793
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IO_INTERRUPT_MESSAGE_INFO_ENTRY
req.alt-loc: Wdm.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL (see Remarks section)
ms.keywords: IO_INTERRUPT_MESSAGE_INFO_ENTRY, IO_INTERRUPT_MESSAGE_INFO_ENTRY, *PIO_INTERRUPT_MESSAGE_INFO_ENTRY
req.iface: 
req.product: Windows 10 or later.
---

# IO_INTERRUPT_MESSAGE_INFO_ENTRY structure



## -description
<p>The <b>IO_INTERRUPT_MESSAGE_INFO_ENTRY</b> structure describes the properties of a single message-signaled interrupt.</p>


## -syntax

````
typedef struct _IO_INTERRUPT_MESSAGE_INFO_ENTRY {
  PHYSICAL_ADDRESS    MessageAddress;
  KAFFINITY           TargetProcessorSet;
  PKINTERRUPT         InterruptObject;
  ULONG               MessageData;
  ULONG               Vector;
  KIRQL               Irql;
  KINTERRUPT_MODE     Mode;
  KINTERRUPT_POLARITY Polarity;
} IO_INTERRUPT_MESSAGE_INFO_ENTRY, *PIO_INTERRUPT_MESSAGE_INFO_ENTRY;
````


## -struct-fields
<dl>

### -field <b>MessageAddress</b>

<dd>
<p>Specifies the physical address that triggers the interrupt message.</p>
</dd>

### -field <b>TargetProcessorSet</b>

<dd>
<p>Specifies a <a href="https://msdn.microsoft.com/library/windows/hardware/ff551830">KAFFINITY</a> value that determines the set of processors that can receive the interrupt.</p>
</dd>

### -field <b>InterruptObject</b>

<dd>
<p>Pointer to the interrupt object that represents the interrupt. </p>
</dd>

### -field <b>MessageData</b>

<dd>
<p>Specifies the value to be written to the address specified by <b>MessageAddress</b> to trigger the interrupt.</p>
</dd>

### -field <b>Vector</b>

<dd>
<p>Specifies the interrupt vector for the interrupt. </p>
</dd>

### -field <b>Irql</b>

<dd>
<p>Specifies the device IRQL (DIRQL) for the interrupt. </p>
</dd>

### -field <b>Mode</b>

<dd>
<p>Specifies a <a href="https://msdn.microsoft.com/library/windows/hardware/ff554239">KINTERRUPT_MODE</a> value that determines whether the interrupt is level-sensitive or latched. </p>
</dd>

### -field <b>Polarity</b>

<dd>
<p>Specifies a <a href="https://msdn.microsoft.com/library/windows/hardware/ff554243">KINTERRUPT_POLARITY</a> value that determines whether the interrupt is active-high or active-low. </p>
</dd>
</dl>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdm.h (include Wdm.h, Ntddk.h, or Ntifs.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550576">IO_INTERRUPT_MESSAGE_INFO</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20IO_INTERRUPT_MESSAGE_INFO_ENTRY structure%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>