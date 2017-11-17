---
UID: NC.61883.PBUS_RESET_ROUTINE
title: PBUS_RESET_ROUTINE
author: windows-driver-content
description: This is a caller-supplied function to be called by the protocol driver when the 1394 bus is reset.
old-location: ieee\pbus_reset_routine.htm
ms.assetid: 99555765-A58F-45A1-B146-3742C390E666
ms.author: windowsdriverdev
ms.date: 10/23/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: IEEE
req.header: 61883.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: BusResetRoutine
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
ms.keywords: TOPOLOGY_MAP, TOPOLOGY_MAP, *PTOPOLOGY_MAP
---

# PBUS_RESET_ROUTINE callback



## -description
<p>This is a caller-supplied function to be called by the protocol driver when the 1394 bus is reset.</p>


## -prototype

````
PBUS_RESET_ROUTINE BusResetRoutine;

void BusResetRoutine(
  _In_ PVOID                Context,
  _In_ PBUS_GENERATION_NODE BusResetInfo
)
{ ... }

typedef PBUS_RESET_ROUTINE BusResetRoutine;
````


## -parameters
<dl>

### -param <i><i>Context</i></i> [in]

<dd>
<p>Pointer to the context supplied by the caller at the <b>Context</b> member of the input BUS_RESET_NOTIFY structure. </p>
</dd>

### -param <i>BusResetInfo</i> [in]

<dd>
<p>The bus reset information. </p>
</dd>
</dl>

## -returns
<p>This callback does not return a value.</p>

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
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [IEEE\buses]:%20PBUS_RESET_ROUTINE callback function%20 RELEASE:%20(10/23/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>