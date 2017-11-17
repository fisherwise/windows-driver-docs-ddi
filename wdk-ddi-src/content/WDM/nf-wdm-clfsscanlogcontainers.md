---
UID: NF.wdm.ClfsScanLogContainers
title: ClfsScanLogContainers
author: windows-driver-content
description: The ClfsScanLogContainers routine retrieves descriptive information for a sequence of containers that belong to a particular CLFS log.
old-location: kernel\clfsscanlogcontainers.htm
ms.assetid: 76f97976-f48b-4ead-88d6-a9e1fdb21f08
ms.author: windowsdriverdev
ms.date: 11/2/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: kernel
req.header: wdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h
req.target-type: Desktop
req.target-min-winverclnt: Available in Windows Server 2003 R2, Windows Vista, and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: ClfsScanLogContainers
req.alt-loc: Clfs.sys,Ext-MS-Win-fs-clfs-l1-1-0.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Clfs.lib
req.dll: Clfs.sys
req.irql: <= APC_LEVEL
ms.keywords: ClfsScanLogContainers
req.iface: 
req.product: Windows 10 or later.
---

# ClfsScanLogContainers function



## -description
<p>The <b>ClfsScanLogContainers</b> routine retrieves descriptive information for a sequence of containers that belong to a particular CLFS log.</p>


## -syntax

````
NTSTATUS ClfsScanLogContainers(
  _Inout_ PCLFS_SCAN_CONTEXT pcxScan,
  _In_    CLFS_SCAN_MODE     eScanMode
);
````


## -parameters
<dl>

### -param <i>pcxScan</i> [in, out]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff541856">CLFS_SCAN_CONTEXT</a> structure. The caller previously allocated the structure and initialized it by calling <a href="https://msdn.microsoft.com/library/windows/hardware/ff541527">ClfsCreateScanContext</a>. In particular, the <b>pInfoContainer</b> member was initialized to point to an array of <a href="https://msdn.microsoft.com/library/windows/hardware/ff541782">CLFS_CONTAINER_INFORMATION</a> structures, and the <b>cContainers</b> member was initialized to the number of elements in the array. On return, the structures in the array receive descriptive information for the containers in the sequence.</p>
</dd>

### -param <i>eScanMode</i> [in]

<dd>
<p>A set of flags that specify the direction of the scan and whether the scan context should be closed. The following flags are available to callers of this routine.</p>
<table>
<tr>
<th>Value</th>
<th>Meaning</th>
</tr>
<tr>
<td>
<p>CLFS_SCAN_FORWARD</p>
</td>
<td>
<p>Scan in the forward direction. For example, if container 5 is the most recently scanned container and <i>pxcScan</i>-&gt;<b>cContainers</b> is equal to two, this routine will return descriptors for containers 6 and 7.</p>
</td>
</tr>
<tr>
<td>
<p>CLFS_SCAN_BACKWARD</p>
</td>
<td>
<p>Scan in the backward direction. For example, if container 5 is the most recently scanned container and <i>pxcScan</i>-&gt;<b>cContainers</b> is equal to two, this routine will return descriptors for containers 4 and 3.</p>
</td>
</tr>
<tr>
<td>
<p>CLFS_SCAN_CLOSE</p>
</td>
<td>
<p>Free all resources associated with the scan context pointed to by <i>pcxScan</i>.</p>
</td>
</tr>
</table>
<p> </p>
<p>If the CLFS_SCAN_CLOSE flag is set, both the CLFS_SCAN_FORWARD and CLFS_SCAN_BACKWARD flags must be clear.</p>
<p>If the CLFS_SCAN_CLOSE flag is clear, only one of the direction flags (CLFS_SCAN_FORWARD or CLFS_SCAN_BACKWARD) must be set.</p>
</dd>
</dl>

## -returns
<p><b>ClfsScanLogContainers</b> returns STATUS_SUCCESS if it succeeds; otherwise, it returns one of the error codes defined in Ntstatus.h.</p>

## -remarks
<p>CLFS uses the <a href="https://msdn.microsoft.com/library/windows/hardware/ff541856">CLFS_SCAN_CONTEXT</a> structure to track where a container scan starts (the <b>cIndex</b> member) and how many containers are scanned in each call to <b>ClfsScanLogContainers</b>. The value N of the <b>cContainers</b> member specifies that each time <b>ClfsScanLogContainers</b> is called, the next N containers are scanned.</p>

<p>The <b>cContainersReturned</b> member of the <b>CLFS_SCAN_CONTEXT</b> structure receives the number of containers actually scanned in a single call to <b>ClfsScanLogContainers</b>.</p>

<p>When <b>ClfsScanLogContainers</b> returns STATUS_NO_MORE_ENTRIES, there are no more containers to be scanned.</p>

<p>When you have finished using the scan context pointed to by <i>pcxScan</i>, you must call <b>ClfsScanLogContainers</b>, with <i>eScanMode</i> equal to CLFS_SCAN_CLOSE, to free any resources associated with the scan context.</p>

<p>For an explanation of CLFS concepts and terminology, see <a href="https://msdn.microsoft.com/a9685648-b08c-48ca-b020-e683068f2ea2">Common Log File System</a>.</p>

<p>CLFS uses the <a href="https://msdn.microsoft.com/library/windows/hardware/ff541856">CLFS_SCAN_CONTEXT</a> structure to track where a container scan starts (the <b>cIndex</b> member) and how many containers are scanned in each call to <b>ClfsScanLogContainers</b>. The value N of the <b>cContainers</b> member specifies that each time <b>ClfsScanLogContainers</b> is called, the next N containers are scanned.</p>

<p>The <b>cContainersReturned</b> member of the <b>CLFS_SCAN_CONTEXT</b> structure receives the number of containers actually scanned in a single call to <b>ClfsScanLogContainers</b>.</p>

<p>When <b>ClfsScanLogContainers</b> returns STATUS_NO_MORE_ENTRIES, there are no more containers to be scanned.</p>

<p>When you have finished using the scan context pointed to by <i>pcxScan</i>, you must call <b>ClfsScanLogContainers</b>, with <i>eScanMode</i> equal to CLFS_SCAN_CLOSE, to free any resources associated with the scan context.</p>

<p>For an explanation of CLFS concepts and terminology, see <a href="https://msdn.microsoft.com/a9685648-b08c-48ca-b020-e683068f2ea2">Common Log File System</a>.</p>

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
<p>Version</p>
</th>
<td width="70%">
<p>Available in Windows Server 2003 R2, Windows Vista, and later versions of Windows.</p>
</td>
</tr>
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
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Clfs.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>Clfs.sys</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&lt;= APC_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541782">CLFS_CONTAINER_INFORMATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541856">CLFS_SCAN_CONTEXT</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541527">ClfsCreateScanContext</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [kernel\kernel]:%20ClfsScanLogContainers routine%20 RELEASE:%20(11/2/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>