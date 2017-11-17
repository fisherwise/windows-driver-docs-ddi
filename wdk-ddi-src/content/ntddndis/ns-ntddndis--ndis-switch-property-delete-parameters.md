---
UID: NS.ntddndis._NDIS_SWITCH_PROPERTY_DELETE_PARAMETERS
title: NDIS_SWITCH_PROPERTY_DELETE_PARAMETERS
author: windows-driver-content
description: The NDIS_SWITCH_PROPERTY_DELETE_PARAMETERS structure specifies the parameters for a Hyper-V extensible switch profile property that will be deleted.
old-location: netvista\ndis_switch_property_delete_parameters.htm
ms.assetid: dcedbdd0-178b-4e44-aaaa-25a5b219324a
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: netvista
req.header: ntddndis.h
req.include-header: Ndis.h
req.target-type: Windows
req.target-min-winverclnt: Supported in NDIS 6.30 and later.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: NDIS_SWITCH_PROPERTY_DELETE_PARAMETERS
req.alt-loc: Ntddndis.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL
ms.keywords: NDIS_SWITCH_PROPERTY_DELETE_PARAMETERS, NDIS_SWITCH_PROPERTY_DELETE_PARAMETERS, *PNDIS_SWITCH_PROPERTY_DELETE_PARAMETERS
req.iface: 
---

# NDIS_SWITCH_PROPERTY_DELETE_PARAMETERS structure



## -description
<p>The <b>NDIS_SWITCH_PROPERTY_DELETE_PARAMETERS</b> structure specifies the parameters for a Hyper-V extensible switch profile property that will be deleted. </p>


## -syntax

````
typedef struct _NDIS_SWITCH_PROPERTY_DELETE_PARAMETERS {
  NDIS_OBJECT_HEADER             Header;
  ULONG                          Flags;
  NDIS_SWITCH_PROPERTY_TYPE      PropertyType;
  NDIS_SWITCH_OBJECT_ID          PropertyId;
  NDIS_SWITCH_OBJECT_INSTANCE_ID PropertyInstanceId;
} NDIS_SWITCH_PROPERTY_DELETE_PARAMETERS, *PNDIS_SWITCH_PROPERTY_DELETE_PARAMETERS;
````


## -struct-fields
<dl>

### -field <b>Header</b>

<dd>
<p>The type, revision, and size of the <b>NDIS_SWITCH_PROPERTY_DELETE_PARAMETERS</b> structure. This member is formatted as an <a href="https://msdn.microsoft.com/library/windows/hardware/ff566588">NDIS_OBJECT_HEADER</a> structure.</p>
<p>The <b>Type</b> member of <b>Header</b> must be set to NDIS_OBJECT_TYPE_DEFAULT. To specify the version of the <b>NDIS_SWITCH_PROPERTY_DELETE_PARAMETERS</b> structure, the <b>Revision</b> member of <b>Header</b> must be set to the following value:</p>
<p></p>
<dl>

### -field <a id="NDIS_SWITCH_PROPERTY_DELETE_PARAMETERS_REVISION_1"></a><a id="ndis_switch_property_delete_parameters_revision_1"></a>NDIS_SWITCH_PROPERTY_DELETE_PARAMETERS_REVISION_1

<dd>
<p>Original version for NDIS 6.30 and later.</p>
<p>Set the <b>Size</b> member to NDIS_SIZEOF_NDIS_SWITCH_PROPERTY_DELETE_PARAMETERS_REVISION_1.</p>
</dd>
</dl>
</dd>

### -field <b>Flags</b>

<dd>
<p>A ULONG value that contains a bitwise <b>OR</b> of flags. This member is reserved for NDIS.</p>
</dd>

### -field <b>PropertyType</b>

<dd>
<p> An <a href="https://msdn.microsoft.com/library/windows/hardware/hh598257">NDIS_SWITCH_PROPERTY_TYPE</a> enumeration value that specifies the type of extensible switch property that will be deleted.</p>
</dd>

### -field <b>PropertyId</b>

<dd>
<p>A GUID value that identifies the property for the extensible switch.

</p>
</dd>

### -field <b>PropertyInstanceId</b>

<dd>
<p>An NDIS_SWITCH_OBJECT_INSTANCE_ID value that specifies the instance identifier of the  extensible switch property.

</p>
</dd>
</dl>

## -remarks
<p>The <b>NDIS_SWITCH_PROPERTY_DELETE_PARAMETERS</b> structure is used in OID set requests of <a href="https://msdn.microsoft.com/library/windows/hardware/hh598281">OID_SWITCH_PROPERTY_DELETE</a>.</p>

<p>For more information about extensible switch policies, see <a href="NULL">Hyper-V Extensible Switch Policies</a>.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Supported in NDIS 6.30 and later.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntddndis.h (include Ndis.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt><b></b></dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff566588">NDIS_OBJECT_HEADER</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh598257">NDIS_SWITCH_PROPERTY_TYPE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh598281">OID_SWITCH_PROPERTY_DELETE</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20NDIS_SWITCH_PROPERTY_DELETE_PARAMETERS structure%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>