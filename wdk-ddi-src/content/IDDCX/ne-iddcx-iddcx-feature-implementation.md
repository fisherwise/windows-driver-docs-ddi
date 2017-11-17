---
UID: NE.iddcx.IDDCX_FEATURE_IMPLEMENTATION
title: IDDCX_FEATURE_IMPLEMENTATION
author: windows-driver-content
description: Enum used to indicate how a given supported feature is implemented.
old-location: display\iddcx_feature_implementation.htm
ms.assetid: 7bed6940-3f69-4cc0-b746-98cd7441f4b8
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: display
req.header: iddcx.h
req.include-header: 
req.target-type: Windows
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IDDCX_FEATURE_IMPLEMENTATION
req.alt-loc: iddcx.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: _requires_same_
ms.keywords: WcsTranslateColors
req.iface: 
---

# IDDCX_FEATURE_IMPLEMENTATION enumeration



## -description
<p>
                    Enum used to indicate how a given supported feature is implemented
                </p>


## -syntax

````
typedef enum _IDDCX_FEATURE_IMPLEMENTATION { 
  IDDCX_FEATURE_IMPLEMENTATION_UNINITIALIZED  = 0,
  IDDCX_FEATURE_IMPLEMENTATION_NONE           = 1,
  IDDCX_FEATURE_IMPLEMENTATION_HARDWARE       = 2,
  IDDCX_FEATURE_IMPLEMENTATION_SOFTWARE       = 3
} IDDCX_FEATURE_IMPLEMENTATION;
````


## -enum-fields
<dl>

### -field <a id="IDDCX_FEATURE_IMPLEMENTATION_UNINITIALIZED"></a><a id="iddcx_feature_implementation_uninitialized"></a><b>IDDCX_FEATURE_IMPLEMENTATION_UNINITIALIZED</b>

<dd>
<p>
                        
                    Indicates that an <b>IDDCX_FEATURE_IMPLEMENTATION</b> variable has not yet been assigned a meaningful value.</p>
</dd>

### -field <a id="IDDCX_FEATURE_IMPLEMENTATION_NONE"></a><a id="iddcx_feature_implementation_none"></a><b>IDDCX_FEATURE_IMPLEMENTATION_NONE</b>

<dd>
<p>
                        The feature is not implemented
                    </p>
</dd>

### -field <a id="IDDCX_FEATURE_IMPLEMENTATION_HARDWARE"></a><a id="iddcx_feature_implementation_hardware"></a><b>IDDCX_FEATURE_IMPLEMENTATION_HARDWARE</b>

<dd>
<p>
                        The feature is implemented and hardware is used in the implementation. For example, the adapter/ display pipeline blends the hardware cursor image into the signal sent to the monitor.
                    </p>
</dd>

### -field <a id="IDDCX_FEATURE_IMPLEMENTATION_SOFTWARE"></a><a id="iddcx_feature_implementation_software"></a><b>IDDCX_FEATURE_IMPLEMENTATION_SOFTWARE</b>

<dd>
<p>
                        The feature is implemented and software is used in the implementation. For example, the driver/ support hardware cursor by blending the cursor image into the display pixels as part of the processing.
                    </p>
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
<dt>Iddcx.h</dt>
</dl>
</td>
</tr>
</table>