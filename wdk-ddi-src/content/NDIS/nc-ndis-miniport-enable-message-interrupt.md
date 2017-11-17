---
UID: NC.ndis.MINIPORT_ENABLE_MESSAGE_INTERRUPT
title: MINIPORT_ENABLE_MESSAGE_INTERRUPT
author: windows-driver-content
description: NDIS can call a miniport driver's MiniportEnableMessageInterrupt function to enable a message interrupt for diagnostic and troubleshooting purposes.
old-location: netvista\miniportenablemessageinterrupt.htm
ms.assetid: b0e1bbef-8116-4455-aa5c-7f47386a3700
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: netvista
req.header: ndis.h
req.include-header: Ndis.h
req.target-type: Windows
req.target-min-winverclnt: Supported in NDIS 6.0 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: MiniportEnableMessageInterrupt
req.alt-loc: Ndis.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: DIRQL (see Remarks section)
ms.keywords: RxNameCacheInitialize
req.iface: 
---

# MINIPORT_ENABLE_MESSAGE_INTERRUPT callback



## -description
<p>NDIS can call a miniport driver's 
   <i>MiniportEnableMessageInterrupt</i> function to enable a message interrupt for diagnostic and
   troubleshooting purposes.</p>


## -prototype

````
MINIPORT_ENABLE_MESSAGE_INTERRUPT MiniportEnableMessageInterrupt;

VOID MiniportEnableMessageInterrupt(
  _In_ NDIS_HANDLE MiniportInterruptContext,
  _In_ ULONG       MessageId
)
{ ... }
````


## -parameters
<dl>

### -param <i>MiniportInterruptContext</i> [in]

<dd>
<p>A handle to a block of context information. The miniport driver supplied this handle in the 
     <i>MiniportInterruptContext</i> parameter that the miniport driver passed to the 
     <a href="https://msdn.microsoft.com/db0b3d51-5bbb-45fb-8c45-dda8c2212b5f">
     NdisMRegisterInterruptEx</a> function.</p>
</dd>

### -param <i>MessageId</i> [in]

<dd>
<p>A message-signaled interrupt. 
     <i>MessageId</i> is an index to the 
     <a href="https://msdn.microsoft.com/e5007381-2436-4eb6-85cd-7145361ab793">
     IO_INTERRUPT_MESSAGE_INFO_ENTRY</a> structures inside a 
     <a href="https://msdn.microsoft.com/d740d55e-6549-494d-9b2a-39d5c2e670d3">
     IO_INTERRUPT_MESSAGE_INFO</a> structure. NDIS passes a pointer to the associated
     IO_INTERRUPT_MESSAGE_INFO structure at the 
     <b>MessageInfoTable</b> member when the driver successfully registers for MSI with the 
     <b>NdisMRegisterInterruptEx</b> function.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>A miniport driver must provide a
    <i>MiniportEnableMessageInterrupt</i> function if the driver calls the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff563649">NdisMRegisterInterruptEx</a> function
    to register an interrupt.</p>

<p>Miniport drivers should disable and enable a message interrupt as explained in the 
    <a href="https://msdn.microsoft.com/ec2e6f49-dc40-48e8-96dc-c9440a6662a3">MiniportMessageInterrupt</a> and 
    <a href="https://msdn.microsoft.com/c1eca20b-eda1-442c-8644-798fa864d5d7">
    MiniportMessageInterruptDpc</a> reference pages.</p>

<p>NDIS calls the 
    <i>MiniportEnableMessageInterrupt</i> and 
    <a href="https://msdn.microsoft.com/68d2076d-c991-4219-b6c3-2399ff5c11a3">
    MiniportDisableMessageInterrupt</a> functions to enable and disable a message interrupt for diagnostic
    and troubleshooting purposes. Typically, 
    <i>MiniportEnableMessageInterrupt</i> and 
    <i>MiniportDisableMessageInterrupt</i> access miniport driver resources that are shared by the 
    <a href="https://msdn.microsoft.com/ec2e6f49-dc40-48e8-96dc-c9440a6662a3">
    MiniportMessageInterrupt</a> function. Therefore, NDIS calls these handlers at DIRQL.</p>

<p>To define a <i>MiniportEnableMessageInterrupt</i> function, you must first provide a function declaration that identifies the type of function you're defining. Windows provides a set of function types for drivers. Declaring a function using the function types helps <a href="NULL">Code Analysis for Drivers</a>, <a href="NULL">Static Driver Verifier</a> (SDV), and other verification tools find errors, and it's a requirement for writing drivers for the Windows operating system.</p>

<p>For example, to define a <i>MiniportEnableMessageInterrupt</i> function that is named "MyEnableMessageInterrupt", use the <b>MINIPORT_ENABLE_MESSAGE_INTERRUPT</b> type as shown in this code example:</p>

<p>Then, implement your function as follows:</p>

<p>The <b>MINIPORT_ENABLE_MESSAGE_INTERRUPT</b> function type is defined in the Ndis.h header file. To more accurately identify errors when you run the code analysis tools, be sure to add the _Use_decl_annotations_ annotation to your function definition.  The _Use_decl_annotations_ annotation ensures that the annotations that are applied to the <b>MINIPORT_ENABLE_MESSAGE_INTERRUPT</b> function type in the header file are used.  For more information about the requirements for function declarations, see <a href="NULL">Declaring Functions by Using Function Role Types for NDIS Drivers</a>.

For information about  _Use_decl_annotations_, see <a href="http://go.microsoft.com/fwlink/p/?linkid=286697">Annotating Function Behavior</a>. </p>

<p>A miniport driver must provide a
    <i>MiniportEnableMessageInterrupt</i> function if the driver calls the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff563649">NdisMRegisterInterruptEx</a> function
    to register an interrupt.</p>

<p>Miniport drivers should disable and enable a message interrupt as explained in the 
    <a href="https://msdn.microsoft.com/ec2e6f49-dc40-48e8-96dc-c9440a6662a3">MiniportMessageInterrupt</a> and 
    <a href="https://msdn.microsoft.com/c1eca20b-eda1-442c-8644-798fa864d5d7">
    MiniportMessageInterruptDpc</a> reference pages.</p>

<p>NDIS calls the 
    <i>MiniportEnableMessageInterrupt</i> and 
    <a href="https://msdn.microsoft.com/68d2076d-c991-4219-b6c3-2399ff5c11a3">
    MiniportDisableMessageInterrupt</a> functions to enable and disable a message interrupt for diagnostic
    and troubleshooting purposes. Typically, 
    <i>MiniportEnableMessageInterrupt</i> and 
    <i>MiniportDisableMessageInterrupt</i> access miniport driver resources that are shared by the 
    <a href="https://msdn.microsoft.com/ec2e6f49-dc40-48e8-96dc-c9440a6662a3">
    MiniportMessageInterrupt</a> function. Therefore, NDIS calls these handlers at DIRQL.</p>

<p>To define a <i>MiniportEnableMessageInterrupt</i> function, you must first provide a function declaration that identifies the type of function you're defining. Windows provides a set of function types for drivers. Declaring a function using the function types helps <a href="NULL">Code Analysis for Drivers</a>, <a href="NULL">Static Driver Verifier</a> (SDV), and other verification tools find errors, and it's a requirement for writing drivers for the Windows operating system.</p>

<p>For example, to define a <i>MiniportEnableMessageInterrupt</i> function that is named "MyEnableMessageInterrupt", use the <b>MINIPORT_ENABLE_MESSAGE_INTERRUPT</b> type as shown in this code example:</p>

<p>Then, implement your function as follows:</p>

<p>The <b>MINIPORT_ENABLE_MESSAGE_INTERRUPT</b> function type is defined in the Ndis.h header file. To more accurately identify errors when you run the code analysis tools, be sure to add the _Use_decl_annotations_ annotation to your function definition.  The _Use_decl_annotations_ annotation ensures that the annotations that are applied to the <b>MINIPORT_ENABLE_MESSAGE_INTERRUPT</b> function type in the header file are used.  For more information about the requirements for function declarations, see <a href="NULL">Declaring Functions by Using Function Role Types for NDIS Drivers</a>.

For information about  _Use_decl_annotations_, see <a href="http://go.microsoft.com/fwlink/p/?linkid=286697">Annotating Function Behavior</a>. </p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Supported in NDIS 6.0 and later.</p>
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
<p>DIRQL (see Remarks section)</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550576">IO_INTERRUPT_MESSAGE_INFO</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/e5007381-2436-4eb6-85cd-7145361ab793">
   IO_INTERRUPT_MESSAGE_INFO_ENTRY</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/68d2076d-c991-4219-b6c3-2399ff5c11a3">
   MiniportDisableMessageInterrupt</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/ec2e6f49-dc40-48e8-96dc-c9440a6662a3">MiniportMessageInterrupt</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/c1eca20b-eda1-442c-8644-798fa864d5d7">MiniportMessageInterruptDPC</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/f4176e2d-d8d2-4e75-bccb-0c452da4d703">
   NDIS_MINIPORT_INTERRUPT_CHARACTERISTICS</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff563649">NdisMRegisterInterruptEx</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20MINIPORT_ENABLE_MESSAGE_INTERRUPT callback function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>