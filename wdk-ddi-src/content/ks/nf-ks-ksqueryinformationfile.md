---
UID: NF.ks.KsQueryInformationFile
title: KsQueryInformationFile
author: windows-driver-content
description: The KsQueryInformationFile function performs an information query against the specified file object. The function attempts to use FastIoDispatch if possible, or it generates an information request against the device object.
old-location: stream\ksqueryinformationfile.htm
ms.assetid: db1cce43-1eae-4af0-bb61-a5c295e3d325
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: stream
req.header: ks.h
req.include-header: Ks.h
req.target-type: Universal
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: KsQueryInformationFile
req.alt-loc: Ks.lib,Ks.dll
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: Ks.lib
req.dll: 
req.irql: 
ms.keywords: KsQueryInformationFile
req.iface: 
---

# KsQueryInformationFile function



## -description
<p>The <b>KsQueryInformationFile</b> function performs an information query against the specified file object. The function attempts to use <b>FastIoDispatch</b> if possible, or it generates an information request against the device object<i>.</i></p>


## -syntax

````
NTSTATUS KsQueryInformationFile(
  _In_  PFILE_OBJECT           FileObject,
  _Out_ PVOID                  FileInformation,
  _In_  ULONG                  Length,
  _In_  FILE_INFORMATION_CLASS FileInformationClass
);
````


## -parameters
<dl>

### -param <i>FileObject</i> [in]

<dd>
<p>Specifies the file object from which to query the standard information.</p>
</dd>

### -param <i>FileInformation</i> [out]

<dd>
<p>Indicates the place in which to put the file information. This is assumed to be a valid or probed address.</p>
</dd>

### -param <i>Length</i> [in]

<dd>
<p>Specifies the correct length of the <i>FileInformation</i> buffer.</p>
</dd>

### -param <i>FileInformationClass</i> [in]

<dd>
<p>Specifies the class of information being requested.</p>
</dd>
</dl>

## -returns
<p>The <b>KsQueryInformationFile</b> function returns STATUS_SUCCESS if successful, or if unsuccessful it returns a query error. </p>

## -remarks
<p>The <b>KsQueryInformationFile</b> function should only be used in cases where the query would result in an actual request to the underlying driver. For example, <b>FilePositionInformation</b> would not generate such a request and should not be used. It assumes the caller is serializing access to the file for operations against a FO_SYNCHRONOUS_IO file object.</p>

<p>The <b>KsQueryInformationFile</b> function should only be used in cases where the query would result in an actual request to the underlying driver. For example, <b>FilePositionInformation</b> would not generate such a request and should not be used. It assumes the caller is serializing access to the file for operations against a FO_SYNCHRONOUS_IO file object.</p>

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
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ks.h (include Ks.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>Ks.lib</dt>
</dl>
</td>
</tr>
</table>