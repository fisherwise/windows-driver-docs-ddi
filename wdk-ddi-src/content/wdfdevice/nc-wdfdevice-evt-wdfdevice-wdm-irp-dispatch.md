---
UID: NC.wdfdevice.EVT_WDFDEVICE_WDM_IRP_DISPATCH
title: EVT_WDFDEVICE_WDM_IRP_DISPATCH
author: windows-driver-content
description: A driver's EvtDeviceWdmIrpDispatch event callback function receives an IRP before the framework processes the IRP.
old-location: wdf\evtdevicewdmirpdispatch.htm
ms.assetid: C6BED59F-066E-42F6-86AE-B0423E0E847F
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: wdf
req.header: wdfdevice.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.11
req.umdf-ver: 2.17
req.alt-api: EvtDeviceWdmIrpDispatch
req.alt-loc: Wdfdevice.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: <=DISPATCH_LEVEL
ms.keywords: WDF_REL_TIMEOUT_IN_US
req.iface: 
req.product: Windows 10 or later.
---

# EVT_WDFDEVICE_WDM_IRP_DISPATCH callback



## -description
<p class="CCE_Message">[Applies to KMDF and UMDF]</p>
<p>A driver's <i>EvtDeviceWdmIrpDispatch</i> event callback function receives an IRP before the framework processes the IRP.</p>


## -prototype

````
EVT_WDFDEVICE_WDM_IRP_DISPATCH EvtDeviceWdmIrpDispatch;

NTSTATUS EvtDeviceWdmIrpDispatch(
  _In_    WDFDEVICE  Device,
  _In_    UCHAR      MajorFunction,
  _In_    UCHAR      MinorFunction,
  _In_    ULONG      Code,
  _In_    WDFCONTEXT DriverContext,
  _Inout_ PIRP       Irp,
  _In_    WDFCONTEXT DispatchContext
)
{ ... }
````


## -parameters
<dl>

### -param <i>Device</i> [in]

<dd>
<p>A handle to a framework device object.</p>
</dd>

### -param <i>MajorFunction</i> [in]

<dd>
<p>One of the IRP major function codes that are defined in wdm.h.</p>
</dd>

### -param <i>MinorFunction</i> [in]

<dd>
<p>One of the I/O IRP minor function codes that are defined in wdm.h for the <i>MajorFunction</i> code.</p>
</dd>

### -param <i>Code</i> [in]

<dd>
<p>Specifies an I/O control code value.  This parameter is valid only if <i>MajorFunction</i> is set to IRP_MJ_DEVICE_CONTROL.</p>
</dd>

### -param <i>DriverContext</i> [in]

<dd>
<p>An untyped pointer to driver-defined context information that the driver provided when it called <a href="https://msdn.microsoft.com/library/windows/hardware/hh451093">WdfDeviceConfigureWdmIrpDispatchCallback</a>.</p>
</dd>

### -param <i>Irp</i> [in, out]

<dd>
<p>A pointer to an IRP structure.</p>
</dd>

### -param <i>DispatchContext</i> [in]

<dd>
<p>An untyped pointer to the framework's dispatch  context information. The driver must provide this parameter when it calls <a href="https://msdn.microsoft.com/library/windows/hardware/hh451100">WdfDeviceWdmDispatchIrp</a>.</p>
</dd>
</dl>

## -returns
<p>The <i>EvtDeviceWdmIrpDispatch</i> callback function must:</p>

<p><b>KMDF only</b></p>

<p><b>KMDF only</b></p>

<p><b>KMDF only</b></p>

## -remarks
<p>The <i>EvtDeviceWdmIrpDispatch</i> callback function should only be used to select a specific queue for an IRP. To do so, the driver calls the <a href="https://msdn.microsoft.com/library/windows/hardware/hh451105">WdfDeviceWdmDispatchIrpToIoQueue</a> method from within the callback function.</p>

<p>If, after examining an IRP in this callback function, the driver does not  know how to dispatch the IRP, the driver can call <a href="https://msdn.microsoft.com/library/windows/hardware/hh451100">WdfDeviceWdmDispatchIrp</a> to return the IRP to the framework for default handling.</p>

<p>A UMDF driver must call either <a href="https://msdn.microsoft.com/library/windows/hardware/hh451100">WdfDeviceWdmDispatchIrp</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/hh451105">WdfDeviceWdmDispatchIrpToIoQueue</a> from this callback function.  A KMDF driver has the additional option of calling neither, and instead completing the IRP or marking it pending.</p>

<p>To register an <i>EvtDeviceWdmIrpDispatch</i> callback function, your driver must call <a href="https://msdn.microsoft.com/library/windows/hardware/hh451093">WdfDeviceConfigureWdmIrpDispatchCallback</a>.</p>

<p>In its <i>EvtDeviceWdmIrpDispatch</i> callback function, a driver should not set a completion routine. If a completion routine is needed, a KMDF driver can provide a  <a href="https://msdn.microsoft.com/aff9cb60-d61b-47a8-aae4-6ffd2a1b7a9a">EvtDeviceWdmIrpPreprocess</a> callback function instead of <i>EvtDeviceWdmIrpDispatch</i>.</p>

<p> For more information about specifying queues for IRPs as they arrive, see <a href="wdf.dispatching_irps_to_i_o_queues">Dispatching IRPs to I/O Queues</a>.</p>

<p>To define an <i>EvtDeviceWdmIrpDispatch</i> callback function, you must first provide a function declaration that identifies the type of callback function you’re defining. Windows provides a set of callback function types for drivers. Declaring a function using the callback function types helps <a href="NULL">Code Analysis for Drivers</a>, <a href="NULL">Static Driver Verifier</a> (SDV), and other verification tools find errors, and it’s a requirement for writing drivers for the Windows operating system.</p>

<p>For example, to define an <i>EvtDeviceWdmIrpDispatch</i> callback function that is named <i>MyDeviceWdmIrpDispatch</i>, use the <b>EVT_WDFDEVICE_WDM_IRP_DISPATCH</b> type as shown in this code example:</p>

<p>Then, implement your callback function:</p>

<p>The <b>EVT_WDFDEVICE_WDM_IRP_DISPATCH</b> function type is defined in the Wdfdevice.h header file. To more accurately identify errors when you run the code analysis tools, be sure to add the _Use_decl_annotations_ annotation to your function definition. The _Use_decl_annotations_ annotation ensures that the annotations that are applied to the <b>EVT_WDFDEVICE_WDM_IRP_DISPATCH</b> function type in the header file are used. For more information about the requirements for function declarations, see <a href="NULL">Declaring Functions by Using Function Role Types for KMDF Drivers</a>. For information about _Use_decl_annotations_, see <a href="https://msdn.microsoft.com/en-US/library/c0aa268d-6fa3-4ced-a8c6-f7652b152e61">Annotating Function Behavior</a>.</p>

<p>The <i>EvtDeviceWdmIrpDispatch</i> callback function should only be used to select a specific queue for an IRP. To do so, the driver calls the <a href="https://msdn.microsoft.com/library/windows/hardware/hh451105">WdfDeviceWdmDispatchIrpToIoQueue</a> method from within the callback function.</p>

<p>If, after examining an IRP in this callback function, the driver does not  know how to dispatch the IRP, the driver can call <a href="https://msdn.microsoft.com/library/windows/hardware/hh451100">WdfDeviceWdmDispatchIrp</a> to return the IRP to the framework for default handling.</p>

<p>A UMDF driver must call either <a href="https://msdn.microsoft.com/library/windows/hardware/hh451100">WdfDeviceWdmDispatchIrp</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/hh451105">WdfDeviceWdmDispatchIrpToIoQueue</a> from this callback function.  A KMDF driver has the additional option of calling neither, and instead completing the IRP or marking it pending.</p>

<p>To register an <i>EvtDeviceWdmIrpDispatch</i> callback function, your driver must call <a href="https://msdn.microsoft.com/library/windows/hardware/hh451093">WdfDeviceConfigureWdmIrpDispatchCallback</a>.</p>

<p>In its <i>EvtDeviceWdmIrpDispatch</i> callback function, a driver should not set a completion routine. If a completion routine is needed, a KMDF driver can provide a  <a href="https://msdn.microsoft.com/aff9cb60-d61b-47a8-aae4-6ffd2a1b7a9a">EvtDeviceWdmIrpPreprocess</a> callback function instead of <i>EvtDeviceWdmIrpDispatch</i>.</p>

<p> For more information about specifying queues for IRPs as they arrive, see <a href="wdf.dispatching_irps_to_i_o_queues">Dispatching IRPs to I/O Queues</a>.</p>

<p>To define an <i>EvtDeviceWdmIrpDispatch</i> callback function, you must first provide a function declaration that identifies the type of callback function you’re defining. Windows provides a set of callback function types for drivers. Declaring a function using the callback function types helps <a href="NULL">Code Analysis for Drivers</a>, <a href="NULL">Static Driver Verifier</a> (SDV), and other verification tools find errors, and it’s a requirement for writing drivers for the Windows operating system.</p>

<p>For example, to define an <i>EvtDeviceWdmIrpDispatch</i> callback function that is named <i>MyDeviceWdmIrpDispatch</i>, use the <b>EVT_WDFDEVICE_WDM_IRP_DISPATCH</b> type as shown in this code example:</p>

<p>Then, implement your callback function:</p>

<p>The <b>EVT_WDFDEVICE_WDM_IRP_DISPATCH</b> function type is defined in the Wdfdevice.h header file. To more accurately identify errors when you run the code analysis tools, be sure to add the _Use_decl_annotations_ annotation to your function definition. The _Use_decl_annotations_ annotation ensures that the annotations that are applied to the <b>EVT_WDFDEVICE_WDM_IRP_DISPATCH</b> function type in the header file are used. For more information about the requirements for function declarations, see <a href="NULL">Declaring Functions by Using Function Role Types for KMDF Drivers</a>. For information about _Use_decl_annotations_, see <a href="https://msdn.microsoft.com/en-US/library/c0aa268d-6fa3-4ced-a8c6-f7652b152e61">Annotating Function Behavior</a>.</p>

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
<p>Minimum KMDF version</p>
</th>
<td width="70%">
<p>1.11</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum UMDF version</p>
</th>
<td width="70%">
<p>2.17</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdfdevice.h (include Wdf.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&lt;=DISPATCH_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh451093">WdfDeviceConfigureWdmIrpDispatchCallback</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh451100">WdfDeviceWdmDispatchIrp</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh451105">WdfDeviceWdmDispatchIrpToIoQueue</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20EVT_WDFDEVICE_WDM_IRP_DISPATCH callback function%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>