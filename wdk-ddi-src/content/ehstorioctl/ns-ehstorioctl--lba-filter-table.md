---
UID: NS.ehstorioctl._LBA_FILTER_TABLE
title: LBA_FILTER_TABLE
author: windows-driver-content
description: The LBA_FILTER_TABLE structure contains the LBA ranges whose access is controlled by a silo driver.
old-location: storage\lba_filter_table.htm
ms.assetid: 656A413C-C0EF-4847-93F5-02DCCF40F348
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: Storage
req.header: ehstorioctl.h
req.include-header: EhStorIoctl.h
req.target-type: Windows
req.target-min-winverclnt: Available starting with Windows 8
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: LBA_FILTER_TABLE
req.alt-loc: EhStorIoctl.h
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
ms.keywords: LBA_FILTER_TABLE, LBA_FILTER_TABLE, *PLBA_FILTER_TABLE
req.iface: 
---

# LBA_FILTER_TABLE structure



## -description
<p>The <b>LBA_FILTER_TABLE</b> structure contains the LBA ranges whose access is controlled by a silo driver. The LBA filter entries in the table define bands on a storage device that are managed by a silo driver.  A silo drivers send the LBA filter table to the enhanced storage class driver in an <a href="https://msdn.microsoft.com/library/windows/hardware/hh406723">IOCTL_EHSTOR_DRIVER_UPDATE_LBA_FILTER_TABLE</a> request.</p>


## -syntax

````
typedef struct _LBA_FILTER_TABLE {
  ULONG   StructSize;
  BOOLEAN GlobalReadLock;
  ULONG   Reserved1;
  BOOLEAN GlobalWriteLock;
  ULONG   Reserved2;
  ULONG   LbaFilterCount;
  ULONG   LbaFilterSize;
  ULONG   LbaFilterOffset;
} LBA_FILTER_TABLE, *PLBA_FILTER_TABLE;
````


## -struct-fields
<dl>

### -field <b>StructSize</b>

<dd>
<p>The size of this structure. This is set to <b>sizeof</b>(LBA_FILTER_TABLE).</p>
</dd>

### -field <b>GlobalReadLock</b>

<dd>
<p>If TRUE, LBAs not included in the filter table are not readable. Otherwise unfiltered LBAs are readable if FALSE.</p>
</dd>

### -field <b>Reserved1</b>

<dd>
<p>Reserved.</p>
</dd>

### -field <b>GlobalWriteLock</b>

<dd>
<p>If TRUE, LBAs not included in the filter table are not writeable. Otherwise unfiltered LBAs are writeable if FALSE.</p>
</dd>

### -field <b>Reserved2</b>

<dd>
<p>Reserved.</p>
</dd>

### -field <b>LbaFilterCount</b>

<dd>
<p>The number of filter entries in the filter table.</p>
</dd>

### -field <b>LbaFilterSize</b>

<dd>
<p>The size in bytes of a filter table entry. This must be set to <b>sizeof</b>(LBA_FILTER_TABLE_ENTRY).</p>
</dd>

### -field <b>LbaFilterOffset</b>

<dd>
<p>The offset of the LBA filter table from the beginning of this structure. This will typically be <b>sizeof</b>(LBA_FILTER_TABLE).</p>
</dd>
</dl>

## -remarks
<p>LBA ranges not included in any filter table entries are considered part of the global band for the device. These ranges are managed independently by the Enhanced Storage Class driver. Access for these ranges is determined by the settings in <i>GlobalReadLock</i> and <i>GlobalWriteLock</i>.</p>

<p>Following the <b>LBA_FILTER_TABLE</b> structure is an array of 0 or more <a href="https://msdn.microsoft.com/library/windows/hardware/hh463962">LBA_FILTER_TABLE_ENTRY</a> structures. Each <b>LBA_FILTER_TABLE_ENTRY</b> defines an individual band whose access is controlled by the silo driver through the direction of band management requests forwarded by the Enhanced Storage Class driver. <b>LBA_FILTER_TABLE_ENTRY</b> structures can occur in any order, however, an LBA range in  a table entry must not overlap with an LBA range from another table entry. </p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Available starting with Windows 8</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>EhStorIoctl.h (include EhStorIoctl.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh406723">IOCTL_EHSTOR_DRIVER_UPDATE_LBA_FILTER_TABLE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh463962">LBA_FILTER_TABLE_ENTRY</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20LBA_FILTER_TABLE structure%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>