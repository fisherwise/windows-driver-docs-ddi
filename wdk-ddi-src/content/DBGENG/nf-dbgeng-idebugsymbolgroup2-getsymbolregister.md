---
UID: NF.dbgeng.IDebugSymbolGroup2.GetSymbolRegister
title: IDebugSymbolGroup2::GetSymbolRegister
author: windows-driver-content
description: The GetSymbolRegister method returns the register that contains the value or a pointer to the value of a symbol in a symbol group.
old-location: debugger\getsymbolregister.htm
ms.assetid: 6b95ca8c-604b-4497-9798-02f362095709
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: debugger
req.header: dbgeng.h
req.include-header: Dbgeng.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IDebugSymbolGroup2.GetSymbolRegister
req.alt-loc: dbgeng.h
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
ms.keywords: IDebugSymbolGroup2, GetSymbolRegister, IDebugSymbolGroup2::GetSymbolRegister
req.iface: IDebugSymbolGroup2
---

# IDebugSymbolGroup2::GetSymbolRegister method



## -description
<p>The <b>GetSymbolRegister</b> method returns the register that contains the value or a pointer to the value of a symbol in a symbol group.</p>


## -syntax

````
HRESULT GetSymbolRegister(
  [in]  ULONG  Index,
  [out] PULONG Register
);
````


## -parameters
<dl>

### -param <i>Index</i> [in]

<dd>
<p>The index of the symbol to return the register for. The index of a symbol is an identification number. The index ranges from zero through the number of symbols in the symbol group minus one.</p>
</dd>

### -param <i>Register</i> [out]

<dd>
<p>The index of the register that contains the value or a pointer to the value of the symbol.</p>
</dd>
</dl>

## -returns
<dl>
<dt><b>S_OK</b></dt>
</dl><p>The method was successful.</p><dl>
<dt><b>E_NOINTERFACE</b></dt>
</dl><p>The symbol's value and a pointer to it are not contained in a register, or the register is not known.</p>

<p> </p>

<p>This method can also return error values.  For more information, see <a href="https://msdn.microsoft.com/713f3ee2-2f5b-415e-9908-90f5ae428b43">Return Values</a>.</p>

## -remarks
<p>For more information about symbol groups, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff554702">Scopes and Symbol Groups</a>.  For more information about registers and the register index, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff554369">Registers</a>.</p>

<p>For more information about symbol groups, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff554702">Scopes and Symbol Groups</a>.  For more information about registers and the register index, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff554369">Registers</a>.</p>

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
<a href="https://msdn.microsoft.com/library/windows/hardware/ff550846">IDebugSymbolGroup2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547975">GetNumberSymbols</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [debugger\debugger]:%20IDebugSymbolGroup2::GetSymbolRegister method%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>