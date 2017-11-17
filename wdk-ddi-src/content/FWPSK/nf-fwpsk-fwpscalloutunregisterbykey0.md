---
UID: NF.fwpsk.FwpsCalloutUnregisterByKey0
title: FwpsCalloutUnregisterByKey0
author: windows-driver-content
description: The FwpsCalloutUnregisterByKey0 function unregisters a callout from the filter engine.Note  FwpsCalloutUnregisterByKey0 is a specific version of FwpsCalloutUnregisterByKey.
old-location: netvista\fwpscalloutunregisterbykey0.htm
ms.assetid: 24254e56-c7f5-4424-98b5-3b99bf210d5b
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: netvista
req.header: fwpsk.h
req.include-header: Fwpsk.h
req.target-type: Universal
req.target-min-winverclnt: Available starting with Windows Vista.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FwpsCalloutUnregisterByKey0
req.alt-loc: fwpkclnt.lib,fwpkclnt.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Fwpkclnt.lib
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: FwpsCalloutUnregisterByKey0
req.iface: 
---

# FwpsCalloutUnregisterByKey0 function



## -description
<p>The 
  <b>FwpsCalloutUnregisterByKey0</b> function unregisters a callout from the filter engine.</p>


## -syntax

````
NTSTATUS NTAPI FwpsCalloutUnregisterByKey0(
  _In_ const GUID *calloutKey
);
````


## -parameters
<dl>

### -param <i>calloutKey</i> [in]

<dd>
<p>A pointer to a GUID that uniquely identifies the callout that is being unregistered from the
     filter engine. This must be a pointer to the same GUID that was specified when the callout driver called
     either the 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff551140">FwpsCalloutRegister0</a> or 
     <a href="https://msdn.microsoft.com/library/windows/hardware/ff551143">FwpsCalloutRegister1</a> functions to
     register the callout with the filter engine.</p>
</dd>
</dl>

## -returns
<p>The 
     <b>FwpsCalloutUnregisterByKey0</b> function returns one of the following NTSTATUS codes.</p><dl>
<dt><b>STATUS_SUCCESS</b></dt>
</dl><p>The callout was successfully unregistered from the filter engine.</p><dl>
<dt><b>STATUS_DEVICE_BUSY</b></dt>
</dl><p>There are one or more data flows being processed by the callout that have an outstanding context
       associated with the data flow. A callout driver must call the 
       <a href="https://msdn.microsoft.com/library/windows/hardware/ff551169">FwpsFlowRemoveContext0</a> function
       for each of these data flows to remove the associated context. After the context has been successfully
       removed from each of these data flows, the callout driver must call the 
       <b>FwpsCalloutUnregisterByKey0</b> function again to finish unregistering the callout from the filter
       engine.</p><dl>
<dt><b>STATUS_FWP_CALLOUT_NOT_FOUND</b></dt>
</dl><p>There is not a callout registered with the filter engine that matches the GUID specified in the 
       <i>calloutKey</i> parameter.</p><dl>
<dt><b>STATUS_FWP_IN_USE</b></dt>
</dl><p>The callout is already in the process of being registered or unregistered in another
       thread.</p><dl>
<dt><b>Other status codes</b></dt>
</dl><p>An error occurred.</p>

<p> </p>

## -remarks
<p>A callout driver calls the 
    <b>FwpsCalloutUnregisterByKey0</b> function to unregister a callout from the filter engine, using the GUID
    key to identify the callout to be unregistered. This function succeeds even if there are filters in
    the filter engine that specify the callout for the filter's action. In this situation, filters with an
    action type of <b>FWP_ACTION_CALLOUT_TERMINATING</b> or <b>FWP_ACTION_CALLOUT_UNKNOWN</b> are treated as
    <b>FWP_ACTION_BLOCK</b>, and filters with an action type of <b>FWP_ACTION_CALLOUT_INSPECTION</b> are ignored after the
    callout has been deregistered from the filter engine.</p>

<p>A callout driver cannot be unloaded until all of the callouts that were previously registered with the
    filter engine have been successfully unregistered.</p>

<p>A callout driver calls the 
    <b>FwpsCalloutUnregisterByKey0</b> function to unregister a callout from the filter engine, using the GUID
    key to identify the callout to be unregistered. This function succeeds even if there are filters in
    the filter engine that specify the callout for the filter's action. In this situation, filters with an
    action type of <b>FWP_ACTION_CALLOUT_TERMINATING</b> or <b>FWP_ACTION_CALLOUT_UNKNOWN</b> are treated as
    <b>FWP_ACTION_BLOCK</b>, and filters with an action type of <b>FWP_ACTION_CALLOUT_INSPECTION</b> are ignored after the
    callout has been deregistered from the filter engine.</p>

<p>A callout driver cannot be unloaded until all of the callouts that were previously registered with the
    filter engine have been successfully unregistered.</p>

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
<p>Available starting with Windows Vista.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Fwpsk.h (include Fwpsk.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Fwpkclnt.lib</dt>
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

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551140">FwpsCalloutRegister0</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551143">FwpsCalloutRegister1</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551144">FwpsCalloutUnregisterById0</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551169">FwpsFlowRemoveContext0</a>
</dt>
<dt>
<a href="NULL">Types of Callouts</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20FwpsCalloutUnregisterByKey0 function%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>