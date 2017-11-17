---
UID: NF.ks.KsUnserializeObjectPropertiesFromRegistry
title: KsUnserializeObjectPropertiesFromRegistry
author: windows-driver-content
description: The KsUnserializeObjectPropertiesFromRegistry function, when given a destination object and a registry path, enumerates the named values and applies them as serialized data to the specified property sets listed in the serialized data.
old-location: stream\ksunserializeobjectpropertiesfromregistry.htm
ms.assetid: e08ddef7-5942-4943-9dbe-9658279892f0
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
req.alt-api: KsUnserializeObjectPropertiesFromRegistry
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
ms.keywords: KsUnserializeObjectPropertiesFromRegistry
req.iface: 
---

# KsUnserializeObjectPropertiesFromRegistry function



## -description
<p>The <b>KsUnserializeObjectPropertiesFromRegistry</b> function, when given a destination object and a registry path, enumerates the named values and applies them as serialized data to the specified property sets listed in the serialized data. An IRP is generated when sending the serialized data, so no assumption is made on use of KS property structures to internally define the property sets. The function does not use the names of the values.</p>


## -syntax

````
NTSTATUS KsUnserializeObjectPropertiesFromRegistry(
  _In_     PFILE_OBJECT    FileObject ,
  _In_opt_ HANDLE          ParentKey ,
  _In_opt_ PUNICODE_STRING RegistryPath 
);
````


## -parameters
<dl>

### -param <i>FileObject </i> [in]

<dd>
<p>Specifies the file object whose properties are being set.</p>
</dd>

### -param <i>ParentKey </i> [in, optional]

<dd>
<p>Optionally contains a handle to the parent of the path, or <b>NULL</b>. The Parent Key and/or the <i>RegistryPath</i> must be passed.</p>
</dd>

### -param <i>RegistryPath </i> [in, optional]

<dd>
<p>Optionally contains the path to the key whose subkeys will be enumerated as property sets, or otherwise <b>NULL</b>. The <i>ParentKey</i> and/or the Registry Path must be passed.</p>
</dd>
</dl>

## -returns
<p>The <b>KsUnserializeObjectPropertiesFromRegistry</b> function returns STATUS_SUCCESS if the property sets were unserialized. The function returns an error if the registry path was invalid, one of the subkeys was invalid, setting a property was unsuccessful, the serialized format was invalid, or a property set was not supported on the object. </p>

## -remarks


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