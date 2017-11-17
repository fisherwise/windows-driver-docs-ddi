---
UID: NS.fwpsk.FWPS_CALLOUT2_
title: FWPS_CALLOUT2_
author: windows-driver-content
description: The FWPS_CALLOUT2 structure defines the data that is required for a callout driver to register a callout with the filter engine.Note  FWPS_CALLOUT2 is the specific version of FWPS_CALLOUT used in Windows 8 and later.
old-location: netvista\fwps_callout2.htm
ms.assetid: 88d5a5ad-b71a-49b3-a1cf-b0dff1a85745
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: netvista
req.header: fwpsk.h
req.include-header: Fwpsk.h
req.target-type: Windows
req.target-min-winverclnt: Available starting with Windows 8.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FWPS_CALLOUT2
req.alt-loc: fwpsk.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: <= DISPATCH_LEVEL
ms.keywords: FWPS_CALLOUT2_, FWPS_CALLOUT2
req.iface: 
---

# FWPS_CALLOUT2_ structure



## -description
<p>The <b>FWPS_CALLOUT2</b> structure defines the data that is required for a callout driver to register a
  callout with the filter engine.<div class="alert"><b>Note</b>  <b>FWPS_CALLOUT2</b> is the specific version of <b>FWPS_CALLOUT</b> used in Windows 8 and later. See <a href="fwp.wfp_version-independent_names_and_targeting_specific_versions_of_windows">WFP Version-Independent Names and Targeting Specific Versions of Windows</a> for more information. For Windows 7, <a href="https://msdn.microsoft.com/library/windows/hardware/ff551226">FWPS_CALLOUT1</a> is available. For Windows Vista, <a href="https://msdn.microsoft.com/library/windows/hardware/ff551224">FWPS_CALLOUT0</a> is available.</div>
<div> </div>
</p>


## -syntax

````
typedef struct FWPS_CALLOUT2_ {
  GUID                                calloutKey;
  UINT32                              flags;
  FWPS_CALLOUT_CLASSIFY_FN2           classifyFn;
  FWPS_CALLOUT_NOTIFY_FN2             notifyFn;
  FWPS_CALLOUT_FLOW_DELETE_NOTIFY_FN0 flowDeleteFn;
} FWPS_CALLOUT2;
````


## -struct-fields
<dl>

### -field <b>calloutKey</b>

<dd>
<p>A callout driver-defined <b>GUID</b> that uniquely identifies the callout.</p>
</dd>

### -field <b>flags</b>

<dd>
<p>Flags that specify callout-specific parameters. Possible flags are:
     </p>
<table>
<tr>
<th>Value</th>
<th>Meaning</th>
</tr>
<tr>
<td width="40%"><a id="FWP_CALLOUT_FLAG_CONDITIONAL_ON_FLOW"></a><a id="fwp_callout_flag_conditional_on_flow"></a><dl>

### -field <b>FWP_CALLOUT_FLAG_CONDITIONAL_ON_FLOW</b>


### -field 0x00000001

</dl>
</td>
<td width="60%">
<p>A callout driver can specify this flag when registering a callout that will be added at a layer
       that supports data flows. If this flag is specified, the filter engine calls the callout driver's 
       <a href="https://msdn.microsoft.com/de8220de-cf71-4718-876e-ef02c15fc948">classifyFn2</a> callout function only if there
       is a context associated with the data flow. A callout driver associates a context with a data flow by
       calling the 
       <a href="https://msdn.microsoft.com/library/windows/hardware/ff551165">FwpsFlowAssociateContext0</a> function.</p>
</td>
</tr>
<tr>
<td width="40%"><a id="FWP_CALLOUT_FLAG_ALLOW_OFFLOAD"></a><a id="fwp_callout_flag_allow_offload"></a><dl>

### -field <b>FWP_CALLOUT_FLAG_ALLOW_OFFLOAD</b>


### -field 0x00000002

</dl>
</td>
<td width="60%">
<p>A callout driver specifies this flag to indicate that the callout driver's 
       <a href="https://msdn.microsoft.com/de8220de-cf71-4718-876e-ef02c15fc948">classifyFn2</a> callout function is unaffected
       by offloading network data processing to offload-capable network interface cards (NICs). If this flag
       is not specified, then offloading of network data processing is disabled for all traffic that is
       processed by any filters that specify the callout for the filter's action.</p>
</td>
</tr>
<tr>
<td width="40%"><a id="FWP_CALLOUT_FLAG_ENABLE_COMMIT_ADD_NOTIFY"></a><a id="fwp_callout_flag_enable_commit_add_notify"></a><dl>

### -field <b>FWP_CALLOUT_FLAG_ENABLE_COMMIT_ADD_NOTIFY</b>


### -field 0x00000004

</dl>
</td>
<td width="60%">
<p>A callout driver specifies this flag to indicate that it can receive notifications about objects and filters that are added inside a transaction. The filter engine sends the notification after the transaction is committed.</p>
</td>
</tr>
<tr>
<td width="40%"><a id="FWP_CALLOUT_FLAG_ALLOW_MID_STREAM_INSPECTION"></a><a id="fwp_callout_flag_allow_mid_stream_inspection"></a><dl>

### -field <b>FWP_CALLOUT_FLAG_ALLOW_MID_STREAM_INSPECTION</b>


### -field 0x00000008

</dl>
</td>
<td width="60%">
<p>A callout driver specifies this flag to indicate that it can perform  dynamic stream inspection of data flows at stream level. See <a href="NULL">Stream Inspection</a>.</p>
</td>
</tr>
<tr>
<td width="40%"><a id="FWP_CALLOUT_FLAG_ALLOW_RECLASSIFY"></a><a id="fwp_callout_flag_allow_reclassify"></a><dl>

### -field <b>FWP_CALLOUT_FLAG_ALLOW_RECLASSIFY</b>


### -field 0x00000010

</dl>
</td>
<td width="60%">
<p>A callout driver specifies this flag to register itself to be called when an existing socket operation is reclassified.</p>
</td>
</tr>
<tr>
<td width="40%"><a id="FWP_CALLOUT_FLAG_RESERVED1"></a><a id="fwp_callout_flag_reserved1"></a><dl>

### -field <b>FWP_CALLOUT_FLAG_RESERVED1</b>


### -field 0x00000020

</dl>
</td>
<td width="60%">
<p>Reserved for system use. Callout drivers should ignore this flag.</p>
</td>
</tr>
<tr>
<td width="40%"><a id="FWP_CALLOUT_FLAG_ALLOW_RSC"></a><a id="fwp_callout_flag_allow_rsc"></a><dl>

### -field <b>FWP_CALLOUT_FLAG_ALLOW_RSC</b>


### -field 0x00000040

</dl>
</td>
<td width="60%">
<p>A callout driver specifies this flag to indicate that the callout supports receive segment coalescing (RSC) with large packets of up to 64K. If this flag is not specified, and a callout is registered, then RSC is disabled for all traffic that is processed by any filters that specify the callout for the filter's action.</p>
</td>
</tr>
<tr>
<td width="40%"><a id="FWP_CALLOUT_FLAG_ALLOW_L2_BATCH_CLASSIFY"></a><a id="fwp_callout_flag_allow_l2_batch_classify"></a><dl>

### -field <b>FWP_CALLOUT_FLAG_ALLOW_L2_BATCH_CLASSIFY</b>


### -field 0x00000080

</dl>
</td>
<td width="60%">
<p>A callout driver specifies this flag when registering a callout that will be added at layer 2, to indicate that its <a href="https://msdn.microsoft.com/de8220de-cf71-4718-876e-ef02c15fc948">classifyFn2</a> callout function can classify multiple chained <a href="https://msdn.microsoft.com/library/windows/hardware/ff568388">NET_BUFFER_LIST</a> structures. For more info, see <a href="NULL">Using Layer 2 Filtering</a>.</p>
<div class="alert"><b>Caution</b>  <p class="note">If a callout driver sets this flag, it cannot use the following functions to modify NET_BUFFER_LISTs.</p>
<ul>
<li>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551206">FwpsReferenceNetBufferList0</a>
</li>
<li>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551159">FwpsDereferenceNetBufferList0</a>
</li>
<li>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551134">FwpsAllocateCloneNetBufferList0</a>
</li>
<li>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551170">FwpsFreeCloneNetBufferList0</a>
</li>
</ul>
<p class="note">With this flag set, <b>FwpsAllocateCloneNetBufferList0</b> will always return an <b>INVALID_PARAMETER</b> error. This may unexpectedly cause a 3rd party callout driver to fail to manage the reference count of NET_BUFFER_LISTs, causing send and receive operations to stop.</p>
</div>
<div> </div>
</td>
</tr>
</table>
<p> </p>
</dd>

### -field <b>classifyFn</b>

<dd>
<p>A pointer to the callout driver's 
     <a href="https://msdn.microsoft.com/de8220de-cf71-4718-876e-ef02c15fc948">classifyFn2</a> callout function. The filter
     engine calls this function whenever there is network data to be processed by the callout.</p>
</dd>

### -field <b>notifyFn</b>

<dd>
<p>A pointer to the callout driver's 
     <a href="https://msdn.microsoft.com/c70c987b-5b4c-4ddd-8eb8-8c3c40003ab3">notifyFn2</a> function. The filter engine calls
     this function to notify the callout driver about events that are associated with the callout.</p>
</dd>

### -field <b>flowDeleteFn</b>

<dd>
<p>A pointer to the callout driver's 
     <a href="https://msdn.microsoft.com/65449a23-da5d-4884-b98e-030461eb019a">flowDeleteFn</a> callout function. The filter
     engine calls this function whenever a data flow that is being processed by the callout is terminated.
     </p>
<p>If a callout driver does not associate a context with the data flows that the callout processes, then
     this member should be set to NULL.</p>
</dd>
</dl>

## -remarks
<p>A callout driver passes a pointer to an initialized <b>FWPS_CALLOUT2</b> structure to the 
    <a href="https://msdn.microsoft.com/library/windows/hardware/hh439576">FwpsCalloutRegister2</a> function when it
    registers a callout with the filter engine.</p>

<p>A callout can set the <b>FWP_CALLOUT_FLAG_CONDITIONAL_ON_FLOW</b> flag only for connections on which
    the driver is interested in performing stream inspections. This callout will be ignored on all other
    connections. Performance will be improved and the driver will not have to maintain unnecessary state
    data.</p>

<p>This structure is essentially identical to the previous version, 
    <a href="https://msdn.microsoft.com/library/windows/hardware/ff551226">FWPS_CALLOUT1</a>. The only differences are that
    the members of this version store the updated versions of the callout function pointers, and additional flags are available for callout drivers to set.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Available starting with Windows 8.</p>
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
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/de8220de-cf71-4718-876e-ef02c15fc948">classifyFn2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/c70c987b-5b4c-4ddd-8eb8-8c3c40003ab3">notifyFn2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/65449a23-da5d-4884-b98e-030461eb019a">flowDeleteFn</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551224">FWPS_CALLOUT0</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff551226">FWPS_CALLOUT1</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh439576">FwpsCalloutRegister2</a>
</dt>
<dt>
<a href="NULL">Using Layer 2 Filtering</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20FWPS_CALLOUT2 structure%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>