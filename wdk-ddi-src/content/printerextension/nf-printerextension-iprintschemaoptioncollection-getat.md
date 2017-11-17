---
UID: NF.printerextension.IPrintSchemaOptionCollection.GetAt
title: IPrintSchemaOptionCollection::GetAt
author: windows-driver-content
description: Gets a pointer to an IPrintSchemaOption object.
old-location: print\iprintschemaoptioncollection_getat.htm
ms.assetid: B77297BF-09F7-46BD-A75F-D36E5E233E05
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: print
req.header: printerextension.h
req.include-header: 
req.target-type: Desktop
req.target-min-winverclnt: Windows 8
req.target-min-winversvr: Windows Server 2012
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IPrintSchemaOptionCollection.GetAt
req.alt-loc: Printerextension.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: <= APC_LEVEL
ms.keywords: IPrintSchemaOptionCollection, GetAt, IPrintSchemaOptionCollection::GetAt
req.iface: IPrintSchemaOptionCollection
req.product: Windows 10 or later.
---

# IPrintSchemaOptionCollection::GetAt method



## -description
<p>Gets a pointer to an <a href="https://msdn.microsoft.com/library/windows/hardware/hh451335">IPrintSchemaOption</a> object.</p>


## -syntax

````
HRESULT GetAt(
  [in]                    ULONG              ulIndex,
  [out, retval, optional] IPrintSchemaOption **ppOption
);
````


## -parameters
<dl>

### -param <i>ulIndex</i> [in]

<dd>
<p>Index of the <b>IPrintSchemaOption</b> object within the collection.</p>
</dd>

### -param <i>ppOption</i> [out, retval, optional]

<dd>
<p>Pointer to an <a href="https://msdn.microsoft.com/library/windows/hardware/hh451335">IPrintSchemaOption</a> object.</p>
</dd>
</dl>

## -returns
<p>Returns an <b>HRESULT</b> value. If the method call was not successful,  it returns the appropriate <b>HRESULT</b> error code.</p>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 8</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>Windows Server 2012</p>
</td>
</tr>
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
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Printerextension.h</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh451335">IPrintSchemaOption</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh846198">IPrintSchemaOptionCollection</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [print\print]:%20IPrintSchemaOptionCollection::GetAt method%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>