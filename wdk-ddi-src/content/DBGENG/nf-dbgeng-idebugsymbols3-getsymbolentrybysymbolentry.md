---
UID: NF.dbgeng.IDebugSymbols3.GetSymbolEntryBySymbolEntry
title: IDebugSymbols3::GetSymbolEntryBySymbolEntry
author: windows-driver-content
description: Allows navigation within the symbol entry hierarchy.
old-location: debugger\idebugsymbols3_getsymbolentrybysymbolentry.htm
ms.assetid: 39AD3C10-C6E8-463F-BDDE-5941CB4B2830
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: debugger
req.header: dbgeng.h
req.include-header: Dbgeng.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IDebugSymbols3.GetSymbolEntryBySymbolEntry
req.alt-loc: Dbgeng.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: 
ms.keywords: IDebugSymbols3, GetSymbolEntryBySymbolEntry, IDebugSymbols3::GetSymbolEntryBySymbolEntry
req.iface: IDebugSymbols3
---

# IDebugSymbols3::GetSymbolEntryBySymbolEntry method



## -description
<p>Allows navigation within the
    symbol entry hierarchy.</p>


## -syntax

````
HRESULT GetSymbolEntryBySymbolEntry(
  [in]  PDEBUG_MODULE_AND_ID FromId,
  [in]  ULONG                Flags,
  [out] PDEBUG_MODULE_AND_ID ToId
);
````


## -parameters
<dl>

### -param <i>FromId</i> [in]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff541511">DEBUG_MODULE_AND_ID</a> structure as the input ID.</p>
</dd>

### -param <i>Flags</i> [in]

<dd>
<p>A bit-set that contains options that affect the behavior of this method. </p>
</dd>

### -param <i>ToId</i> [out]

<dd>
<p>A pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff541511">DEBUG_MODULE_AND_ID</a> structure as the output ID.</p>
</dd>
</dl>

## -returns
<p>If this method succeeds, it returns <b xmlns:loc="http://microsoft.com/wdcml/l10n">S_OK</b>. Otherwise, it returns an <b xmlns:loc="http://microsoft.com/wdcml/l10n">HRESULT</b> error code.</p>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Dbgeng.h (include Dbgeng.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff541511">DEBUG_MODULE_AND_ID</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550870">IDebugSymbols3</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [debugger\debugger]:%20IDebugSymbols3::GetSymbolEntryBySymbolEntry method%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>