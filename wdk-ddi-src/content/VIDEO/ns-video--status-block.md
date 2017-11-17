---
UID: NS.video._STATUS_BLOCK
title: STATUS_BLOCK
author: windows-driver-content
description: The STATUS_BLOCK structure is a substructure within the VIDEO_REQUEST_PACKET structure. A miniport driver's HwVidStartIO function must set the status block of each VRP that it gets.
old-location: display\status_block.htm
ms.assetid: 8e3126df-d081-4545-a5db-8637ee27f15b
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: video.h
req.include-header: Video.h
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: STATUS_BLOCK
req.alt-loc: video.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: See Remarks section.
ms.keywords: STATUS_BLOCK, STATUS_BLOCK, *PSTATUS_BLOCK
req.iface: 
req.product: Windows 10 or later.
---

# STATUS_BLOCK structure



## -description
<p>The STATUS_BLOCK structure is a substructure within the VIDEO_REQUEST_PACKET structure. A miniport driver's <a href="https://msdn.microsoft.com/82951291-cf3e-486b-ad0e-f347fefe0370">HwVidStartIO</a> function must set the status block of each <a href="wdkgloss.v#wdkgloss.video_request_packet__vrp_#wdkgloss.video_request_packet__vrp_"><i>VRP</i></a> that it gets.</p>


## -syntax

````
typedef struct _STATUS_BLOCK {
  union {
    VP_STATUS Status;
    PVOID     Pointer;
  };
  ULONG_PTR Information;
} STATUS_BLOCK, *PSTATUS_BLOCK;
````


## -struct-fields
<dl>

### -field <b>Status</b>

<dd>
<p>Indicates the result of the requested operation. This member might be one of the following status codes:</p>
<p></p>
<dl>

### -field <a id="ERROR_INSUFFICIENT_BUFFER"></a><a id="error_insufficient_buffer"></a>ERROR_INSUFFICIENT_BUFFER

<dd>
<p>Either the VRP <b>InputBuffer</b> is too small to provide the data required to process the given request or the <b>OutputBuffer</b> is too small to return the requested data.</p>
</dd>
</dl>
<p></p>
<dl>

### -field <a id="ERROR_INVALID_FUNCTION"></a><a id="error_invalid_function"></a>ERROR_INVALID_FUNCTION

<dd>
<p>The miniport driver does not handle this request.</p>
</dd>
</dl>
<p></p>
<dl>

### -field <a id="ERROR_INVALID_PARAMETER"></a><a id="error_invalid_parameter"></a>ERROR_INVALID_PARAMETER

<dd>
<p>A parameter in the VRP is invalid.</p>
</dd>
</dl>
<p></p>
<dl>

### -field <a id="ERROR_IO_PENDING"></a><a id="error_io_pending"></a>ERROR_IO_PENDING

<dd>
<p>An operation has not yet completed.</p>
</dd>
</dl>
<p></p>
<dl>

### -field <a id="ERROR_MORE_DATA"></a><a id="error_more_data"></a>ERROR_MORE_DATA

<dd>
<p>The driver has additional data to be returned but has already filled the given VRP <b>OutputBuffer</b>.</p>
</dd>
</dl>
<p></p>
<dl>

### -field <a id="ERROR_NOT_ENOUGH_MEMORY"></a><a id="error_not_enough_memory"></a>ERROR_NOT_ENOUGH_MEMORY

<dd>
<p>There is insufficient memory to process the request.</p>
</dd>
</dl>
<p></p>
<dl>

### -field <a id="NO_ERROR"></a><a id="no_error"></a>NO_ERROR

<dd>
<p>The requested operation has been carried out and completed successfully.</p>
</dd>
</dl>
</dd>

### -field <b>Pointer</b>

<dd>
<p>Should be ignored by the miniport driver. This member of the union exists to guarantee field alignment across 32- and 64-bit systems.</p>
</dd>

### -field <b>Information</b>

<dd>
<p>Supplies additional information about the completed operation. The meaning of the value varies according to VRP. Generally, this member is used to return the minimum size required for the input buffer if the VRP passes data in the <b>InputBuffer</b>. Alternatively, it contains the number of bytes of data transferred if the requested operation returns data in the VRP <b>OutputBuffer</b>.</p>
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
<dt>Video.h (include Video.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/82951291-cf3e-486b-ad0e-f347fefe0370">HwVidStartIO</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff570547">VIDEO_REQUEST_PACKET</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [display\display]:%20STATUS_BLOCK structure%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>