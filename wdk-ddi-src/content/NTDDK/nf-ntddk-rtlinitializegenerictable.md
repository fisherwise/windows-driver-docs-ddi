---
UID: NF.ntddk.RtlInitializeGenericTable
title: RtlInitializeGenericTable
author: windows-driver-content
description: The RtlInitializeGenericTable routine initializes a generic table.
old-location: ifsk\rtlinitializegenerictable.htm
ms.assetid: 99a91bb4-4fcd-4b49-bd1e-4551027b5d1f
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: ifsk
req.header: ntddk.h
req.include-header: Ntddk.h, Ntifs.h, Fltkernel.h
req.target-type: Universal
req.target-min-winverclnt: This routine is available on Microsoft Windows 2000 and later versions of all Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RtlInitializeGenericTable
req.alt-loc: NtosKrnl.exe
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: <= DISPATCH_LEVEL (see Remarks section)
ms.keywords: RtlInitializeGenericTable
req.iface: 
---

# RtlInitializeGenericTable function



## -description
<p>The <b>RtlInitializeGenericTable</b> routine initializes a generic table. </p>


## -syntax

````
VOID RtlInitializeGenericTable(
  _Out_    PRTL_GENERIC_TABLE            Table,
  _In_     PRTL_GENERIC_COMPARE_ROUTINE  CompareRoutine,
  _In_     PRTL_GENERIC_ALLOCATE_ROUTINE AllocateRoutine,
  _In_     PRTL_GENERIC_FREE_ROUTINE     FreeRoutine,
  _In_opt_ PVOID                         TableContext
);
````


## -parameters
<dl>

### -param <i>Table</i> [out]

<dd>
<p>A pointer to a caller-allocated buffer, which must be at least <b>sizeof</b>(<a href="https://msdn.microsoft.com/library/windows/hardware/ff553345">RTL_GENERIC_TABLE</a>) bytes in size, to contain the initialized generic table structure. </p>
</dd>

### -param <i>CompareRoutine</i> [in]

<dd>
<p>An entry point of a comparison callback routine, declared as follows:</p>
<div class="code"><span codelanguage=""><table>
<tr>
<th></th>
</tr>
<tr>
<td>
<pre>RTL_GENERIC_COMPARE_RESULTS
(*PRTL_GENERIC_COMPARE_ROUTINE) (
    __in struct _RTL_GENERIC_TABLE  *Table,
    __in PVOID  FirstStruct,
    __in PVOID  SecondStruct
    ); </pre>
</td>
</tr>
</table></span></div>
<p>The <i>CompareRoutine</i> parameters are as follows:</p>
<p></p>
<dl>

### -param <a id="Table"></a><a id="table"></a><a id="TABLE"></a><i>Table</i>

<dd>
<p>A pointer to the generic table.</p>
</dd>

### -param <a id="FirstStruct"></a><a id="firststruct"></a><a id="FIRSTSTRUCT"></a><i>FirstStruct</i>

<dd>
<p>A pointer to the first item to be compared.</p>
</dd>

### -param <a id="SecondStruct"></a><a id="secondstruct"></a><a id="SECONDSTRUCT"></a><i>SecondStruct</i>

<dd>
<p>A pointer to the second item to be compared.</p>
</dd>
</dl>
<p>The <i>CompareRoutine</i> must strictly track the ordering of all elements in the generic table so that it can identify any particular element. The caller-defined structure for element data usually includes a member whose value is unique and can be used as a sorting key. All <i>Rtl...GenericTable</i> routines that call the <i>CompareRoutine</i> take a buffer pointer as a parameter, which is passed in turn to the <i>CompareRoutine</i>. The buffer contains a caller-supplied key value to be matched by the <i>CompareRoutine</i> to the key of the element that is being searched for. </p>
<p>Given two such key values, the <i>CompareRoutine</i> returns <b>GenericLessThan</b>, <b>GenericGreaterThan</b>, or <b>GenericEqual</b>. </p>
</dd>

### -param <i>AllocateRoutine</i> [in]

<dd>
<p>An entry point of an allocation callback routine, declared as follows:</p>
<div class="code"><span codelanguage=""><table>
<tr>
<th></th>
</tr>
<tr>
<td>
<pre>PVOID
(*PRTL_GENERIC_ALLOCATE_ROUTINE) (
    __in struct _RTL_GENERIC_TABLE  *Table,
    __in CLONG  ByteSize
    );</pre>
</td>
</tr>
</table></span></div>
<p>The <i>AllocateRoutine</i> parameters are as follows:</p>
<p></p>
<dl>

### -param <a id="Table"></a><a id="table"></a><a id="TABLE"></a><i>Table</i>

<dd>
<p>A pointer to the generic table.</p>
</dd>

### -param <a id="ByteSize"></a><a id="bytesize"></a><a id="BYTESIZE"></a><i>ByteSize</i>

<dd>
<p>The number of bytes to allocate.</p>
</dd>
</dl>
<p>For each new element, the <i>AllocateRoutine</i> is called to allocate memory for caller-supplied data plus some additional memory for use by the <i>Rtl...GenericTable</i> routines. Note that because of this "additional memory," caller-supplied routines must not access the first (<b>sizeof</b>(RTL_SPLAY_LINKS) + <b>sizeof</b>(LIST_ENTRY)) bytes of any element in the generic table. </p>
</dd>

### -param <i>FreeRoutine</i> [in]

<dd>
<p>An entry point of a deallocation callback routine, declared as follows:</p>
<div class="code"><span codelanguage=""><table>
<tr>
<th></th>
</tr>
<tr>
<td>
<pre>VOID
(*PRTL_GENERIC_FREE_ROUTINE) (
    __in struct _RTL_GENERIC_TABLE  *Table,
    __in PVOID  Buffer
    );</pre>
</td>
</tr>
</table></span></div>
<p>The <i>FreeRoutine</i> parameters are as follows:</p>
<p></p>
<dl>

### -param <a id="Table"></a><a id="table"></a><a id="TABLE"></a><i>Table</i>

<dd>
<p>A pointer to the generic table.</p>
</dd>

### -param <a id="Buffer"></a><a id="buffer"></a><a id="BUFFER"></a><i>Buffer</i>

<dd>
<p>A pointer to the element that is being deleted.</p>
</dd>
</dl>
<p><i>Rtl...GenericTable</i> routines call the <i>FreeRoutine</i> to deallocate memory for elements to be deleted from the generic table. The <i>FreeRoutine</i> is the opposite of the <i>AllocateRoutine</i>. </p>
</dd>

### -param <i>TableContext</i> [in, optional]

<dd>
<p>An optional pointer to a caller-supplied context for the generic table. This parameter can be <b>NULL</b>.</p>
</dd>
</dl>

## -returns
<p>None</p>

## -remarks
<p>File systems call <b>RtlInitializeGenericTable</b> to initialize a generic table to store file system-specific data, such as name-lookup information for currently open files. The sort order, structure, and contents of the elements are caller-defined. </p>

<p>File systems must call <b>RtlInitializeGenericTable</b> to initialize the generic table before they use any other <i>Rtl...GenericTable</i> routines on the new generic table. The initialized generic table structure should be considered opaque.</p>

<p>Callers of the <i>Rtl...GenericTable</i> routines are responsible for exclusively synchronizing access to the generic table. An exclusive fast mutex is the most efficient synchronization mechanism to use for this purpose. </p>

<p>The caller-supplied <i>CompareRoutine</i> is called before the <i>AllocateRoutine</i> to locate an appropriate location at which a new element should be inserted. The <i>CompareRoutine</i> also is called before the <i>FreeRoutine</i> to locate an element to be deleted.</p>

<p>By default, the operating system uses splay trees to implement generic tables. Under some circumstances, operations on a splay tree will make the tree deep and narrow and might even turn it into a straight line. Very deep trees degrade the performance of searches. You can ensure a more balanced, shallower tree implementation of generic tables by using Adelson-Velsky/Landis (AVL) trees. If you want to configure the generic table routines to use AVL trees instead of splay trees in your driver, insert the following define statement in a common header file before including <i>Ntddk.h</i>:</p>

<p>If RTL_USE_AVL_TABLES is not defined, you must use the AVL form of the generic table routines. For example, use the <a href="https://msdn.microsoft.com/library/windows/hardware/hh406465">RtlInitializeGenericTableAvl</a> routine instead of <b>RtlInitializeGenericTable</b>. <b>RtlInitializeGenericTableAvl</b> returns an initialized <a href="https://msdn.microsoft.com/library/windows/hardware/ff553327">RTL_AVL_TABLE</a> table structure in the buffer to which the <i>Table</i> parameter points. In the call to <b>RtlInitializeGenericTableAvl</b>, the caller must pass a PRTL_AVL_COMPARE_ROUTINE-typed comparison callback routine, a PRTL_AVL_ALLOCATE_ROUTINE-typed allocation callback routine, and a PRTL_AVL_FREE_ROUTINE-typed deallocation callback routine rather than the similar PRTL_GENERIC_<i>Xxx</i>-typed routines.</p>

<p>Callers of <b>RtlInitializeGenericTable</b> must be running at IRQL &lt;= DISPATCH_LEVEL. Note that if <i>Rtl...GenericTable</i> routines are to be used at IRQL DISPATCH_LEVEL, the <i>CompareRoutine</i>, <i>AllocateRoutine</i>, and <i>FreeRoutine</i> must all be nonpageable code, and the <i>AllocateRoutine</i> should allocate memory from nonpaged pool.</p>

<p>File systems call <b>RtlInitializeGenericTable</b> to initialize a generic table to store file system-specific data, such as name-lookup information for currently open files. The sort order, structure, and contents of the elements are caller-defined. </p>

<p>File systems must call <b>RtlInitializeGenericTable</b> to initialize the generic table before they use any other <i>Rtl...GenericTable</i> routines on the new generic table. The initialized generic table structure should be considered opaque.</p>

<p>Callers of the <i>Rtl...GenericTable</i> routines are responsible for exclusively synchronizing access to the generic table. An exclusive fast mutex is the most efficient synchronization mechanism to use for this purpose. </p>

<p>The caller-supplied <i>CompareRoutine</i> is called before the <i>AllocateRoutine</i> to locate an appropriate location at which a new element should be inserted. The <i>CompareRoutine</i> also is called before the <i>FreeRoutine</i> to locate an element to be deleted.</p>

<p>By default, the operating system uses splay trees to implement generic tables. Under some circumstances, operations on a splay tree will make the tree deep and narrow and might even turn it into a straight line. Very deep trees degrade the performance of searches. You can ensure a more balanced, shallower tree implementation of generic tables by using Adelson-Velsky/Landis (AVL) trees. If you want to configure the generic table routines to use AVL trees instead of splay trees in your driver, insert the following define statement in a common header file before including <i>Ntddk.h</i>:</p>

<p>If RTL_USE_AVL_TABLES is not defined, you must use the AVL form of the generic table routines. For example, use the <a href="https://msdn.microsoft.com/library/windows/hardware/hh406465">RtlInitializeGenericTableAvl</a> routine instead of <b>RtlInitializeGenericTable</b>. <b>RtlInitializeGenericTableAvl</b> returns an initialized <a href="https://msdn.microsoft.com/library/windows/hardware/ff553327">RTL_AVL_TABLE</a> table structure in the buffer to which the <i>Table</i> parameter points. In the call to <b>RtlInitializeGenericTableAvl</b>, the caller must pass a PRTL_AVL_COMPARE_ROUTINE-typed comparison callback routine, a PRTL_AVL_ALLOCATE_ROUTINE-typed allocation callback routine, and a PRTL_AVL_FREE_ROUTINE-typed deallocation callback routine rather than the similar PRTL_GENERIC_<i>Xxx</i>-typed routines.</p>

<p>Callers of <b>RtlInitializeGenericTable</b> must be running at IRQL &lt;= DISPATCH_LEVEL. Note that if <i>Rtl...GenericTable</i> routines are to be used at IRQL DISPATCH_LEVEL, the <i>CompareRoutine</i>, <i>AllocateRoutine</i>, and <i>FreeRoutine</i> must all be nonpageable code, and the <i>AllocateRoutine</i> should allocate memory from nonpaged pool.</p>

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
<p>Version</p>
</th>
<td width="70%">
<p>This routine is available on Microsoft Windows 2000 and later versions of all Windows operating systems. </p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntddk.h (include Ntddk.h, Ntifs.h, or Fltkernel.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Library</p>
</th>
<td width="70%">
<dl>
<dt>NtosKrnl.lib</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>DLL</p>
</th>
<td width="70%">
<dl>
<dt>NtosKrnl.exe</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>&lt;= DISPATCH_LEVEL (see Remarks section)</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff545293">ExInitializeFastMutex</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552209">RtlDeleteElementGenericTable</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552243">RtlEnumerateGenericTable</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552247">RtlEnumerateGenericTableWithoutSplaying</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552297">RtlGetElementGenericTable</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553024">RtlInsertElementGenericTable</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553091">RtlLookupElementGenericTable</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553134">RtlNumberGenericTableElements</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20RtlInitializeGenericTable routine%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>