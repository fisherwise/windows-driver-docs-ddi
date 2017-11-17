---
UID: NN.wudfddi.IWDFIoRequest3
title: IWDFIoRequest3
author: windows-driver-content
description: To obtain the IWDFIoRequest3 interface, drivers call IWDFIoRequest::QueryInterface.
old-location: wdf\iwdfiorequest3.htm
ms.assetid: 12F4CDB7-EEA5-49D1-AD41-6F5F0C9ED6C3
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: interface
ms.prod: windows-hardware
ms.technology: wdf
req.header: wudfddi.h
req.include-header: 
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 1.11
req.alt-api: IWDFIoRequest3
req.alt-loc: WUDFx.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: Unavailable in UMDF 2.0 and later.
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: WUDFx.dll
req.irql: <= DISPATCH_LEVEL
ms.keywords: IWDFWorkItem, GetParentObject, IWDFWorkItem::GetParentObject
req.iface: IWDFWorkItem
req.product: Windows 10 or later.
---

# IWDFIoRequest3 interface



## -description
<p class="CCE_Message">[<b>Warning:</b> UMDF 2 is the latest version of UMDF and supersedes UMDF 1.  All new UMDF drivers should be written using UMDF 2.  No new features are being added to UMDF 1 and there is limited support for UMDF 1 on newer versions of Windows 10.  Universal Windows drivers must use UMDF 2.  For more info, see <a href="https://docs.microsoft.com/en-us/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2">Getting Started with UMDF</a>.]</p>
<p>To obtain the <b>IWDFIoRequest3</b> interface, drivers call <b>IWDFIoRequest::QueryInterface</b>.</p>


## -inheritance
<p>The <b xmlns:loc="http://microsoft.com/wdcml/l10n">IWDFIoRequest3</b> interface inherits from <a href="https://msdn.microsoft.com/library/windows/hardware/ff558988">IWDFIoRequest2</a>. <b>IWDFIoRequest3</b> also has these types of members:</p>

<p>The <b>IWDFIoRequest3</b> interface has these methods.</p>

<p>
   The 
  <a href="https://msdn.microsoft.com/library/windows/hardware/hh451341">GetUserModeDriverInitiatedIo</a> method determines whether an I/O request is marked as initiated by a UMDF driver.</p>

<p>
   The 
  <a href="https://msdn.microsoft.com/library/windows/hardware/hh451345">RetrieveActivityId</a> method retrieves the current activity identifier associated with an I/O request.</p>

<p>
   The 
  <a href="https://msdn.microsoft.com/library/windows/hardware/hh451350">SetActivityId</a> method associates an activity identifier with an I/O request.</p>

<p>The <a href="https://msdn.microsoft.com/library/windows/hardware/hh451354">SetUserModeDriverInitiatedIo</a> method 
   
  indicates to kernel-mode drivers that sit below the UMDF driver in the same device stack that a particular request should be treated as though it came from a UMDF driver.</p>

<p> </p>

## -members
<p>The <b>IWDFIoRequest3</b> interface has these methods.</p><table class="members" id="memberListMethods">
<tr>
<th align="left" width="37%">Method</th>
<th align="left" width="63%">Description</th>
</tr>
<tr data="declared;">
<td align="left" width="37%">
<a href="https://msdn.microsoft.com/library/windows/hardware/hh451341">GetUserModeDriverInitiatedIo</a>
</td>
<td align="left" width="63%">
<p>
   The 
  <a href="https://msdn.microsoft.com/library/windows/hardware/hh451341">GetUserModeDriverInitiatedIo</a> method determines whether an I/O request is marked as initiated by a UMDF driver.</p>
</td>
</tr>
<tr data="declared;">
<td align="left" width="37%">
<a href="https://msdn.microsoft.com/library/windows/hardware/hh451345">RetrieveActivityId</a>
</td>
<td align="left" width="63%">
<p>
   The 
  <a href="https://msdn.microsoft.com/library/windows/hardware/hh451345">RetrieveActivityId</a> method retrieves the current activity identifier associated with an I/O request.</p>
</td>
</tr>
<tr data="declared;">
<td align="left" width="37%">
<a href="https://msdn.microsoft.com/library/windows/hardware/hh451350">SetActivityId</a>
</td>
<td align="left" width="63%">
<p>
   The 
  <a href="https://msdn.microsoft.com/library/windows/hardware/hh451350">SetActivityId</a> method associates an activity identifier with an I/O request.</p>
</td>
</tr>
<tr data="declared;">
<td align="left" width="37%">
<a href="https://msdn.microsoft.com/library/windows/hardware/hh451354">SetUserModeDriverInitiatedIo</a>
</td>
<td align="left" width="63%">
<p>The <a href="https://msdn.microsoft.com/library/windows/hardware/hh451354">SetUserModeDriverInitiatedIo</a> method 
   
  indicates to kernel-mode drivers that sit below the UMDF driver in the same device stack that a particular request should be treated as though it came from a UMDF driver.</p>
</td>
</tr>
</table><p>
   The 
  <a href="https://msdn.microsoft.com/library/windows/hardware/hh451341">GetUserModeDriverInitiatedIo</a> method determines whether an I/O request is marked as initiated by a UMDF driver.</p>

<p>
   The 
  <a href="https://msdn.microsoft.com/library/windows/hardware/hh451345">RetrieveActivityId</a> method retrieves the current activity identifier associated with an I/O request.</p>

<p>
   The 
  <a href="https://msdn.microsoft.com/library/windows/hardware/hh451350">SetActivityId</a> method associates an activity identifier with an I/O request.</p>

<p>The <a href="https://msdn.microsoft.com/library/windows/hardware/hh451354">SetUserModeDriverInitiatedIo</a> method 
   
  indicates to kernel-mode drivers that sit below the UMDF driver in the same device stack that a particular request should be treated as though it came from a UMDF driver.</p>

<p> </p>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt>Desktop</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>End of support</p>
</th>
<td width="70%">
<p>Unavailable in UMDF 2.0 and later.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum UMDF version</p>
</th>
<td width="70%">
<p>1.11</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wudfddi.h</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>WUDFx.dll</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff558988">IWDFIoRequest2</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [wdf\wdf]:%20IWDFIoRequest3 interface%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>