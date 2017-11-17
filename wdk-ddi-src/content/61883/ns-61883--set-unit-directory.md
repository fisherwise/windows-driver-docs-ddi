---
UID: NS.61883._SET_UNIT_DIRECTORY
title: SET_UNIT_DIRECTORY
author: windows-driver-content
description: This structure is used to assign settings for a unit directory.
old-location: ieee\set_unit_directory.htm
ms.assetid: C4021856-835D-4B4B-9795-4FEEEFAC06B8
ms.author: windowsdriverdev
ms.date: 10/23/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: IEEE
req.header: 61883.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: SET_UNIT_DIRECTORY
req.alt-loc: 61883.h
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
ms.keywords: SET_UNIT_DIRECTORY, SET_UNIT_DIRECTORY, *PSET_UNIT_DIRECTORY
---

# SET_UNIT_DIRECTORY structure



## -description
<p>This structure is used to assign settings for a unit directory.</p>


## -syntax

````
typedef struct _SET_UNIT_DIRECTORY {
  ULONG  Flags;
  ULONG  UnitSpecId;
  ULONG  UnitSwVersion;
  HANDLE hCromEntry;
} SET_UNIT_DIRECTORY, *PSET_UNIT_DIRECTORY;
````


## -struct-fields
<dl>

### -field <b><b>Flags</b></b>

<dd>
<p>Specifies whether to add or remove a unit directory. Can be ADD_UNIT_DIRECTORY_ENTRY to add a unit directory, or REMOVE_UNIT_DIRECTORY_ENTRY to remove a unit directory. If ISSUE_BUS_RESET_AFTER_MODIFY is also set, a bus reset will be issued after the add or remove.</p>
</dd>

### -field <b><b>UnitSpecId</b></b>

<dd>
<p>The UnitSpecId value to use within the unit directory, as defined in the <i>IEEE 1394-1995 Specification</i>. </p>
</dd>

### -field <b><b>UnitSwVersion</b></b>

<dd>
<p>The UnitSwVersion value to use within the unit directory, as defined in the <i>IEEE 1394-1995 Specification</i>. </p>
</dd>

### -field <b><b>hCromEntry</b></b>

<dd>
<p>A handle to the Configuration ROM entry. </p>
<p>If ADD-UNIT_DIRECTORY_ENTRY is set in <b>Flags</b>, <b>hCromEntry</b> is ignored. </p>
<p>If REMOVE_UNIT_DIRECTORY_ENTRY is set in <b>Flags</b>, <b>hCromEntry</b> is a handle to the Configuration ROM entry to remove. </p>
</dd>
</dl>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>61883.h</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff537008">AV_61883_REQUEST</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [IEEE\buses]:%20SET_UNIT_DIRECTORY structure%20 RELEASE:%20(10/23/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>