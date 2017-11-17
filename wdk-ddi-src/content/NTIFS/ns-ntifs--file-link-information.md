---
UID: NS.ntifs._FILE_LINK_INFORMATION
title: FILE_LINK_INFORMATION
author: windows-driver-content
description: The FILE_LINK_INFORMATION structure is used to create an NTFS hard link to an existing file.
old-location: ifsk\file_link_information.htm
ms.assetid: c0c47dc7-d672-4094-af17-9de2b01886aa
ms.author: windowsdriverdev
ms.date: 10/26/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: ifsk
req.header: ntifs.h
req.include-header: Ntifs.h, Fltkernel.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FILE_LINK_INFORMATION
req.alt-loc: ntifs.h
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
ms.keywords: FILE_LINK_INFORMATION, FILE_LINK_INFORMATION, *PFILE_LINK_INFORMATION
req.iface: 
---

# FILE_LINK_INFORMATION structure



## -description
<p>The FILE_LINK_INFORMATION structure is used to create an NTFS hard link to an existing file. </p>


## -syntax

````
typedef struct _FILE_LINK_INFORMATION {
  BOOLEAN ReplaceIfExists;
  HANDLE  RootDirectory;
  ULONG   FileNameLength;
  WCHAR   FileName[1];
} FILE_LINK_INFORMATION, *PFILE_LINK_INFORMATION;
````


## -struct-fields
<dl>

### -field <b>ReplaceIfExists</b>

<dd>
<p>Set to <b>TRUE</b> to specify that if the link already exists, it should be replaced with the new link. Set to <b>FALSE</b> if the link creation operation should fail if the link already exists. </p>
</dd>

### -field <b>RootDirectory</b>

<dd>
<p>If the link is to be created in the same directory as the file that is being linked to, or if the <b>FileName</b> member contains the full pathname for the link to be created, this is <b>NULL</b>. Otherwise it is a handle for the directory where the link is to be created. </p>
</dd>

### -field <b>FileNameLength</b>

<dd>
<p>Length, in bytes, of the file name string. </p>
</dd>

### -field <b>FileName</b>

<dd>
<p>The first character of the name to be assigned to the newly created link. This is followed in memory by the remainder of the string. If the <b>RootDirectory</b> member is <b>NULL</b> and the link is to be created in a different directory from the file that is being linked to, this member specifies the full pathname for the link to be created. Otherwise, it specifies only the file name. (See the Remarks section for <a href="https://msdn.microsoft.com/library/windows/hardware/ff567052">ZwQueryInformationFile</a> for details on the syntax of this file name string.) </p>
</dd>
</dl>

## -remarks
<p>The FILE_LINK_INFORMATION structure is used to create an NTFS hard link to an existing file. This operation can be performed in either of the following ways: </p>

<p>Call <a href="https://msdn.microsoft.com/library/windows/hardware/ff544516">FltSetInformationFile</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff567096">ZwSetInformationFile</a>, passing FileLinkInformation as the value of FileInformationClass and passing a caller-allocated, FILE_LINK_INFORMATION-structured buffer as the value of <i>FileInformation</i>. The <i>FileHandle</i> parameter specifies the existing file to which the hard link should point. </p>

<p>Create an IRP with major function code IRP_MJ_SET_INFORMATION. </p>

<p>No specific access rights are required to set this information. </p>

<p>File system minifilters must use <a href="https://msdn.microsoft.com/library/windows/hardware/ff544516">FltSetInformationFile</a>, not <a href="https://msdn.microsoft.com/library/windows/hardware/ff567096">ZwSetInformationFile</a>, to set this information for a file. </p>

<p>For more information about NTFS hard links, see the Microsoft Windows SDK documentation for the Win32 <b>CreateHardLink</b> function. </p>

<p>The size of the <i>FileInformation</i> buffer passed to <a href="https://msdn.microsoft.com/library/windows/hardware/ff544516">FltSetInformationFile</a> or <a href="https://msdn.microsoft.com/library/windows/hardware/ff567096">ZwSetInformationFile</a> must be at least <b>sizeof</b>(FILE_LINK_INFORMATION). </p>

<p>This structure must be aligned on a LONG (4-byte) boundary. </p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntifs.h (include Ntifs.h or Fltkernel.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff544516">FltSetInformationFile</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff549366">IRP_MJ_SET_INFORMATION</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567052">ZwQueryInformationFile</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff567096">ZwSetInformationFile</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [ifsk\ifsk]:%20FILE_LINK_INFORMATION structure%20 RELEASE:%20(10/26/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>