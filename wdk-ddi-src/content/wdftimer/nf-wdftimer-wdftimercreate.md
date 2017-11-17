---
UID: NF.wdftimer.WdfTimerCreate
title: WdfTimerCreate
author: windows-driver-content
description: The WdfTimerCreate method creates a framework timer object.
old-location: wdf\wdftimercreate.htm
ms.assetid: 577b7629-13ff-4a2d-9f9f-a140d8442bd3
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: wdf
req.header: wdftimer.h
req.include-header: Wdf.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 1.0
req.umdf-ver: 2.0
req.alt-api: WdfTimerCreate
req.alt-loc: Wdf01000.sys,Wdf01000.sys.dll,WUDFx02000.dll,WUDFx02000.dll.dll
req.ddi-compliance: DriverCreate, KmdfIrql, KmdfIrql2
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Wdf01000.sys (KMDF); 
WUDFx02000.dll (UMDF)
req.dll: 
req.irql: <=DISPATCH_LEVEL
ms.keywords: WdfTimerCreate
req.iface: 
req.product: Windows 10 or later.
---

# WdfTimerCreate function



## -description
<p class="CCE_Message">[Applies to KMDF and UMDF]</p>
<p>The <b>WdfTimerCreate</b> method creates a framework timer object.</p>


## -syntax

````
NTSTATUS WdfTimerCreate(
  _In_  PWDF_TIMER_CONFIG      Config,
  _In_  PWDF_OBJECT_ATTRIBUTES Attributes,
  _Out_ WDFTIMER               *Timer
);
````


## -parameters
<dl>

### -param <i>Config</i> [in]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff552519">WDF_TIMER_CONFIG</a> structure.</p>
</dd>

### -param <i>Attributes</i> [in]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff552400">WDF_OBJECT_ATTRIBUTES</a> structure that contains object attributes for the new timer object. </p>
</dd>

### -param <i>Timer</i> [out]

<dd>
<p>A pointer to a location that receives a handle to the new framework timer object.</p>
</dd>
</dl>

## -returns
<p><b>WdfTimerCreate</b> returns STATUS_SUCCESS if the operation succeeds. Otherwise, this method might return one of the following values:</p><dl>
<dt><b>STATUS_WDF_PARENT_NOT_SPECIFIED</b></dt>
</dl><p>The <i>Attributes</i> parameter was <b>NULL</b>, or the <b>ParentObject</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff552400">WDF_OBJECT_ATTRIBUTES</a> structure that <i>Attributes</i> specifies was <b>NULL</b>.</p><dl>
<dt><b>STATUS_INVALID_PARAMETER</b></dt>
</dl><p>An invalid parameter was specified.</p><dl>
<dt><b>STATUS_INVALID_DEVICE_REQUEST</b></dt>
</dl><p>The <b>ParentObject</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff552400">WDF_OBJECT_ATTRIBUTES</a> structure did not reference a framework device object or an object whose chain of parents leads to a framework device object.</p><dl>
<dt><b>STATUS_INSUFFICIENT_RESOURCES</b></dt>
</dl><p>There was insufficient memory.</p><dl>
<dt><b>STATUS_WDF_INCOMPATIBLE_EXECUTION_LEVEL</b></dt>
</dl><p>The <b>AutomaticSerialization</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff552519">WDF_TIMER_CONFIG</a> structure was set to <b>TRUE</b>, but the parent device object's <a href="https://msdn.microsoft.com/82b1fe8e-054c-4710-9a32-d620a62a070e">execution level</a> was set to <b>WdfExecutionLevelPassive</b>.</p>

<p> </p>

<p>For a list of other return values that the <b>WdfTimerCreate</b> method might return, see <a href="wdf.framework_object_creation_errors">Framework Object Creation Errors</a>.</p>

<p>This method might also return other <a href="https://msdn.microsoft.com/library/windows/hardware/ff557697">NTSTATUS values</a>.</p>

## -remarks
<p>When your driver calls <b>WdfTimerCreate</b>, it must supply a <a href="https://msdn.microsoft.com/library/windows/hardware/ff552400">WDF_OBJECT_ATTRIBUTES</a> structure and must specify a parent object in the structure's <b>ParentObject</b> member. The parent object can be a framework device object or any object whose chain of parents leads to a framework device object. The framework will delete the timer object when it deletes the device object.</p>

<p>After creating a timer object, the driver calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff550054">WdfTimerStart</a> to start the timer's clock. </p>

<p>If your driver provides <a href="https://msdn.microsoft.com/aba2efca-7d1f-4594-af65-13356f0e3f8b">EvtCleanupCallback</a> or <a href="https://msdn.microsoft.com/4c3b08d2-bb25-40bd-b2fc-1b9ea2d452b3">EvtDestroyCallback</a> callback functions for the framework timer object, note that the framework calls these callback functions at IRQL = PASSIVE_LEVEL.</p>

<p>For more information about framework timer objects, see <a href="wdf.using_timers">Using Timers</a>.</p>

<p>The following code example initializes a <a href="https://msdn.microsoft.com/library/windows/hardware/ff552519">WDF_TIMER_CONFIG</a> structure and a <a href="https://msdn.microsoft.com/library/windows/hardware/ff552400">WDF_OBJECT_ATTRIBUTES</a> structure and then calls <b>WdfTimerCreate</b>.</p>

<p>When your driver calls <b>WdfTimerCreate</b>, it must supply a <a href="https://msdn.microsoft.com/library/windows/hardware/ff552400">WDF_OBJECT_ATTRIBUTES</a> structure and must specify a parent object in the structure's <b>ParentObject</b> member. The parent object can be a framework device object or any object whose chain of parents leads to a framework device object. The framework will delete the timer object when it deletes the device object.</p>

<p>After creating a timer object, the driver calls <a href="https://msdn.microsoft.com/library/windows/hardware/ff550054">WdfTimerStart</a> to start the timer's clock. </p>

<p>If your driver provides <a href="https://msdn.microsoft.com/aba2efca-7d1f-4594-af65-13356f0e3f8b">EvtCleanupCallback</a> or <a href="https://msdn.microsoft.com/4c3b08d2-bb25-40bd-b2fc-1b9ea2d452b3">EvtDestroyCallback</a> callback functions for the framework timer object, note that the framework calls these callback functions at IRQL = PASSIVE_LEVEL.</p>

<p>For more information about framework timer objects, see <a href="wdf.using_timers">Using Timers</a>.</p>

<p>The following code example initializes a <a href="https://msdn.microsoft.com/library/windows/hardware/ff552519">WDF_TIMER_CONFIG</a> structure and a <a href="https://msdn.microsoft.com/library/windows/hardware/ff552400">WDF_OBJECT_ATTRIBUTES</a> structure and then calls <b>WdfTimerCreate</b>.</p>

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
<p>1.0</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum UMDF version</p>
</th>
<td width="70%">
<p>2.0</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wdftimer.h (include Wdf.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Wdf01000.sys (KMDF); </dt>
<dt>WUDFx02000.dll (UMDF)</dt>
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
<tr>
<th width="30%">
<p>DDI compliance rules</p>
</th>
<td width="70%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544957">DriverCreate</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/ff548167">KmdfIrql</a>, <a href="https://msdn.microsoft.com/library/windows/hardware/hh975091">KmdfIrql2</a>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552400">WDF_OBJECT_ATTRIBUTES</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552402">WDF_OBJECT_ATTRIBUTES_INIT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552519">WDF_TIMER_CONFIG</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552522">WDF_TIMER_CONFIG_INIT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550054">WdfTimerStart</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20WdfTimerCreate method%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>