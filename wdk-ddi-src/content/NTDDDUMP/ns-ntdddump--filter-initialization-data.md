---
UID: NS.ntdddump._FILTER_INITIALIZATION_DATA
title: FILTER_INITIALIZATION_DATA
author: windows-driver-content
description: The filter driver fills in a FILTER_INITIALIZATION_DATA structure and returns it to the crash dump driver.
old-location: storage\filter_initialization_data.htm
ms.assetid: 71f9d0c2-ffc9-4fe1-ae95-f38a1d1e82df
ms.author: windowsdriverdev
ms.date: 10/24/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: Storage
req.header: ntdddump.h
req.include-header: Ntdddump.h
req.target-type: Windows
req.target-min-winverclnt: Available starting with Windows Vista and Windows Server 2008.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: FILTER_INITIALIZATION_DATA
req.alt-loc: ntdddump.h
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
ms.keywords: FILTER_INITIALIZATION_DATA, FILTER_INITIALIZATION_DATA, *PFILTER_INITIALIZATION_DATA
req.iface: 
---

# FILTER_INITIALIZATION_DATA structure



## -description
<p>The filter driver fills in a <b>FILTER_INITIALIZATION_DATA</b> structure and returns it to the crash dump driver.</p>


## -syntax

````
typedef struct _FILTER_INITIALIZATION_DATA {
  ULONG        MajorVersion;
  ULONG        MinorVersion;
  PDUMP_START  DumpStart;
  PDUMP_WRITE  DumpWrite;
  PDUMP_FINISH DumpFinish;
  PDUMP_UNLOAD DumpUnload;
  PVOID        DumpData;
  ULONG        MaxPagesPerWrite;
  ULONG        Flags;
  PDUMP_READ   DumpRead;
} FILTER_INITIALIZATION_DATA, *PFILTER_INITIALIZATION_DATA;
````


## -struct-fields
<dl>

### -field <b>MajorVersion</b>

<dd>
<p>Set to one of the following major version values:</p>
<dl>

### -field <a id="DUMP_FILTER_MAJOR_VERSION_1"></a><a id="dump_filter_major_version_1"></a><b>DUMP_FILTER_MAJOR_VERSION_1</b> (0x1)


### -field <a id="DUMP_FILTER_MAJOR_VERSION"></a><a id="dump_filter_major_version"></a><b>DUMP_FILTER_MAJOR_VERSION</b> (0x2)

</dl>
</dd>

### -field <b>MinorVersion</b>

<dd>
<p>Set to <b>DUMP_FILTER_MINOR_VERSION</b>.</p>
</dd>

### -field <b>DumpStart</b>

<dd>
<p>A pointer to the dump initialization routine. This routine is called when the crash dump starts.</p>
</dd>

### -field <b>DumpWrite</b>

<dd>
<p>A pointer to the write routine. This routine is called before every crash dump write request.</p>
</dd>

### -field <b>DumpFinish</b>

<dd>
<p>A pointer to the dump finish routine.  This routine is called when the crash dump is finished.</p>
</dd>

### -field <b>DumpUnload</b>

<dd>
<p>A pointer to the dump unload routine. This routine is called before the driver is unloaded.</p>
</dd>

### -field <b>DumpData</b>

<dd>
<p>The filter driver can pass a pointer to internal context data in this member. This pointer is passed back to the filter driver in a <a href="https://msdn.microsoft.com/library/windows/hardware/ff553862">FILTER_EXTENSION</a> structure during each callback.</p>
</dd>

### -field <b>MaxPagesPerWrite</b>

<dd>
<p>The maximum number of pages for each dump read or write request.</p>
</dd>

### -field <b>Flags</b>

<dd>
<p>A set of flags for  dump filter initialization. This value is set to either 0 or the following:</p>
<table>
<tr>
<th>Value</th>
<th>Meaning</th>
</tr>
<tr>
<td width="40%"><a id="DUMP_FILTER_FLAG_SYSTEM_SUPPORT_READ"></a><a id="dump_filter_flag_system_support_read"></a><dl>

### -field <b>DUMP_FILTER_FLAG_SYSTEM_SUPPORT_READ</b>

</dl>
</td>
<td width="60%">
<p>The dump filter supports filtering reads, and a read callback routine is set for <b>DumpRead</b>. This flag is supported starting in Windows 8.</p>
</td>
</tr>
<tr>
<td width="40%"><a id="DUMP_FILTER_CRITICAL"></a><a id="dump_filter_critical"></a><dl>

### -field <b>DUMP_FILTER_CRITICAL</b>

</dl>
</td>
<td width="60%">
<p>Fail the filter initialization  immediately if the  dump filter driver's <b>DriverEntry</b> routine does not return STATUS_SUCCESS. This flag is supported starting in Windows 8.</p>
</td>
</tr>
</table>
<p> </p>
</dd>

### -field <b>DumpRead</b>

<dd>
<p>A pointer to the read routine. This routine is called after every crash dump read request. This member is available starting in Windows 8.</p>
</dd>
</dl>

## -remarks
<p>For a dump filter driver to support read filtering, the following settings are required:</p>

<p>If any of these members are not set, the dump filter driver will be marked as not supporting dump reads by the crashdump stack.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Available starting with Windows Vista and Windows Server 2008.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntdddump.h (include Ntdddump.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552764">Dump_Finish</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh439713">Dump_Read</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552767">Dump_Start</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553709">Dump_Write</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff552773">Dump_Unload</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff553862">FILTER_EXTENSION</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [Storage\storage]:%20FILTER_INITIALIZATION_DATA structure%20 RELEASE:%20(10/24/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>