---
UID: NF.dbgeng.IDebugRegisters2.GetDescriptionWide
title: IDebugRegisters2::GetDescriptionWide
author: windows-driver-content
description: The GetDescriptionWide method returns the description of a register.
old-location: debugger\getdescriptionwide.htm
ms.assetid: e599d960-aefb-4b68-8149-7e93150d90d5
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: debugger
req.header: dbgeng.h
req.include-header: DbgEng.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IDebugRegisters2.GetDescriptionWide
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
ms.keywords: IDebugRegisters2, GetDescriptionWide, IDebugRegisters2::GetDescriptionWide
req.iface: IDebugRegisters2
---

# IDebugRegisters2::GetDescriptionWide method



## -description
<p>The <b>GetDescriptionWide</b>  method returns the description of a register.</p>


## -syntax

````
HRESULT GetDescriptionWide(
  [in]            ULONG                       Register,
  [out, optional] PWSTR                       NameBuffer,
  [in]            ULONG                       NameBufferSize,
  [out, optional] PULONG                      NameSize,
  [out, optional] PDEBUG_REGISTER_DESCRIPTION Desc
);
````


## -parameters
<dl>

### -param <i>Register</i> [in]

<dd>
<p>Specifies the index of the register for which the description is requested.</p>
</dd>

### -param <i>NameBuffer</i> [out, optional]

<dd>
<p>Specifies the buffer in which to store the name of the register.  If <i>NameBuffer</i> is <b>NULL</b>, this information is not returned.</p>
</dd>

### -param <i>NameBufferSize</i> [in]

<dd>
<p>Specifies the size, in characters, of the buffer that  <i>NameBuffer</i> specifies.</p>
</dd>

### -param <i>NameSize</i> [out, optional]

<dd>
<p>Receives the size, in characters, of the register's name in <i>NameBuffer</i> buffer.  If <i>NameSize</i> is <b>NULL</b>, this information is not returned.</p>
</dd>

### -param <i>Desc</i> [out, optional]

<dd>
<p>Receives the description of the register.  See <a href="https://msdn.microsoft.com/library/windows/hardware/ff541538">DEBUG_REGISTER_DESCRIPTION</a> for more details.</p>
</dd>
</dl>

## -returns
<p>This list does not contain all the errors that might occur.  For a list of possible errors, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff549771">HRESULT Values</a>.</p><dl>
<dt><b>S_OK</b></dt>
</dl><p>The method was successful.</p><dl>
<dt><b>S_FALSE</b></dt>
</dl><p>The method was successful. However, the buffer was not large enough to hold the register's name, so it was truncated.</p><dl>
<dt><b>E_UNEXPECTED</b></dt>
</dl><p>No target machine has been specified, or a description of the register could not be found.</p><dl>
<dt><b>E_INVALIDARG</b></dt>
</dl><p>The index of the register requested is greater than the total number of registers on the target's machine.</p>

<p> </p>

## -remarks
<p>For an overview of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff550825">IDebugRegisters</a> interface and other register-related methods, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff554369">Registers</a>.</p>

<p>For an overview of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff550825">IDebugRegisters</a> interface and other register-related methods, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff554369">Registers</a>.</p>

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
<dt>Dbgeng.h (include DbgEng.h)</dt>
</dl>
</td>
</tr>
</table>