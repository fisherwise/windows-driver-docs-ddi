---
UID: NN.wudfusb.IWDFUsbInterface~r1
title: IWDFUsbInterface
author: windows-driver-content
description: The IWDFUsbInterface interface exposes a USB interface that a USB device exposes.
old-location: wdf\iwdfusbinterface.htm
ms.assetid: 90770016-1267-437e-af70-99741231dc29
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: interface
ms.prod: windows-hardware
ms.technology: wdf
req.header: wudfusb.h
req.include-header: 
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 1.5
req.alt-api: IWDFUsbInterface
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
req.irql: 
ms.keywords: IWDFUsbTargetPipe2, ConfigureContinuousReader, IWDFUsbTargetPipe2::ConfigureContinuousReader
req.iface: IWDFUsbTargetPipe2
req.product: Windows 10 or later.
---

# IWDFUsbInterface interface



## -description
<p class="CCE_Message">[<b>Warning:</b> UMDF 2 is the latest version of UMDF and supersedes UMDF 1.  All new UMDF drivers should be written using UMDF 2.  No new features are being added to UMDF 1 and there is limited support for UMDF 1 on newer versions of Windows 10.  Universal Windows drivers must use UMDF 2.  For more info, see <a href="https://docs.microsoft.com/en-us/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2">Getting Started with UMDF</a>.]</p>
<p>
<p>The <b>IWDFUsbInterface</b> interface exposes a USB interface that a USB device exposes.</p>
</p>
<p>The <b>IWDFUsbInterface</b> interface exposes a USB interface that a USB device exposes.</p>


## -inheritance
<p>The <b xmlns:loc="http://microsoft.com/wdcml/l10n">IWDFUsbInterface</b> interface inherits from <a href="https://msdn.microsoft.com/library/windows/hardware/ff560200">IWDFObject</a>. <b>IWDFUsbInterface</b> also has these types of members:</p>

<p>The <b>IWDFUsbInterface</b> interface has these methods.</p>

<p>The <a href="https://msdn.microsoft.com/0deccfee-34e3-47ee-b141-9758cffcd0c2">GetConfiguredSettingIndex</a> method retrieves the current setting index for a USB interface.</p>

<p>The <a href="https://msdn.microsoft.com/ae4cffc8-65db-452c-9b85-19752c32c421">GetInterfaceDescriptor</a> method retrieves a descriptor for a USB interface.</p>

<p>The <a href="https://msdn.microsoft.com/de8de14a-94a8-49e2-912a-9c174f5a2c74">GetInterfaceNumber</a> method retrieves the index of a USB interface.</p>

<p>The <a href="https://msdn.microsoft.com/60ec8b38-8ab2-45d8-92ab-5943fd9bba79">GetNumEndPoints</a> method retrieves the number of endpoints (pipes) on a USB interface.</p>

<p>The <a href="https://msdn.microsoft.com/31c23596-21b2-4fb2-96bd-5372fe2432ab">GetWinUsbHandle</a> method retrieves the WinUsb interface handle that is associated with a USB interface.</p>

<p>The <a href="https://msdn.microsoft.com/abfaad6b-be42-4547-aa26-5b44e53118bc">RetrieveUsbPipeObject</a> method retrieves a USB pipe object for the specified pipe index.</p>

<p>The <a href="https://msdn.microsoft.com/c47b025b-1be9-4fdc-965a-a9a82a394177">SelectSetting</a> method selects the specified alternate setting on a USB interface.</p>

<p> </p>

## -members
<p>The <b>IWDFUsbInterface</b> interface has these methods.</p><table class="members" id="memberListMethods">
<tr>
<th align="left" width="37%">Method</th>
<th align="left" width="63%">Description</th>
</tr>
<tr data="declared;">
<td align="left" width="37%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff560317">IWDFUsbInterface::GetConfiguredSettingIndex</a>
</td>
<td align="left" width="63%">
<p>The <a href="https://msdn.microsoft.com/0deccfee-34e3-47ee-b141-9758cffcd0c2">GetConfiguredSettingIndex</a> method retrieves the current setting index for a USB interface.</p>
</td>
</tr>
<tr data="declared;">
<td align="left" width="37%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff560320">IWDFUsbInterface::GetInterfaceDescriptor</a>
</td>
<td align="left" width="63%">
<p>The <a href="https://msdn.microsoft.com/ae4cffc8-65db-452c-9b85-19752c32c421">GetInterfaceDescriptor</a> method retrieves a descriptor for a USB interface.</p>
</td>
</tr>
<tr data="declared;">
<td align="left" width="37%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff560327">IWDFUsbInterface::GetInterfaceNumber</a>
</td>
<td align="left" width="63%">
<p>The <a href="https://msdn.microsoft.com/de8de14a-94a8-49e2-912a-9c174f5a2c74">GetInterfaceNumber</a> method retrieves the index of a USB interface.</p>
</td>
</tr>
<tr data="declared;">
<td align="left" width="37%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff560334">IWDFUsbInterface::GetNumEndPoints</a>
</td>
<td align="left" width="63%">
<p>The <a href="https://msdn.microsoft.com/60ec8b38-8ab2-45d8-92ab-5943fd9bba79">GetNumEndPoints</a> method retrieves the number of endpoints (pipes) on a USB interface.</p>
</td>
</tr>
<tr data="declared;">
<td align="left" width="37%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff560337">IWDFUsbInterface::GetWinUsbHandle</a>
</td>
<td align="left" width="63%">
<p>The <a href="https://msdn.microsoft.com/31c23596-21b2-4fb2-96bd-5372fe2432ab">GetWinUsbHandle</a> method retrieves the WinUsb interface handle that is associated with a USB interface.</p>
</td>
</tr>
<tr data="declared;">
<td align="left" width="37%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff560339">IWDFUsbInterface::RetrieveUsbPipeObject</a>
</td>
<td align="left" width="63%">
<p>The <a href="https://msdn.microsoft.com/abfaad6b-be42-4547-aa26-5b44e53118bc">RetrieveUsbPipeObject</a> method retrieves a USB pipe object for the specified pipe index.</p>
</td>
</tr>
<tr data="declared;">
<td align="left" width="37%">
<a href="https://msdn.microsoft.com/library/windows/hardware/ff560343">IWDFUsbInterface::SelectSetting</a>
</td>
<td align="left" width="63%">
<p>The <a href="https://msdn.microsoft.com/c47b025b-1be9-4fdc-965a-a9a82a394177">SelectSetting</a> method selects the specified alternate setting on a USB interface.</p>
</td>
</tr>
</table><p>The <a href="https://msdn.microsoft.com/0deccfee-34e3-47ee-b141-9758cffcd0c2">GetConfiguredSettingIndex</a> method retrieves the current setting index for a USB interface.</p>

<p>The <a href="https://msdn.microsoft.com/ae4cffc8-65db-452c-9b85-19752c32c421">GetInterfaceDescriptor</a> method retrieves a descriptor for a USB interface.</p>

<p>The <a href="https://msdn.microsoft.com/de8de14a-94a8-49e2-912a-9c174f5a2c74">GetInterfaceNumber</a> method retrieves the index of a USB interface.</p>

<p>The <a href="https://msdn.microsoft.com/60ec8b38-8ab2-45d8-92ab-5943fd9bba79">GetNumEndPoints</a> method retrieves the number of endpoints (pipes) on a USB interface.</p>

<p>The <a href="https://msdn.microsoft.com/31c23596-21b2-4fb2-96bd-5372fe2432ab">GetWinUsbHandle</a> method retrieves the WinUsb interface handle that is associated with a USB interface.</p>

<p>The <a href="https://msdn.microsoft.com/abfaad6b-be42-4547-aa26-5b44e53118bc">RetrieveUsbPipeObject</a> method retrieves a USB pipe object for the specified pipe index.</p>

<p>The <a href="https://msdn.microsoft.com/c47b025b-1be9-4fdc-965a-a9a82a394177">SelectSetting</a> method selects the specified alternate setting on a USB interface.</p>

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
<p>1.5</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wudfusb.h</dt>
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