---
UID: NS.d3dkmdt._D3DKMT_WDDM_1_2_CAPS
title: D3DKMT_WDDM_1_2_CAPS
author: windows-driver-content
description: Reserved for system use. Do not use in your driver.
old-location: display\d3dkmt_wddm_1_2_caps.htm
ms.assetid: 0cd26fad-4772-4631-81fc-da2ddb7dc9a1
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: d3dkmdt.h
req.include-header: D3dkmdt.h
req.target-type: Windows
req.target-min-winverclnt: Windows 8
req.target-min-winversvr: Windows Server 2012
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: D3DKMT_WDDM_1_2_CAPS
req.alt-loc: D3dkmdt.h
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
ms.keywords: D3DKMT_WDDM_1_2_CAPS, D3DKMT_WDDM_1_2_CAPS
req.iface: 
---

# D3DKMT_WDDM_1_2_CAPS structure



## -description
<p>Reserved for system use. Do not use in your driver.</p>


## -syntax

````
typedef struct _D3DKMT_WDDM_1_2_CAPS {
  D3DKMDT_PREEMPTION_CAPS PreemptionCaps;
  union {
    struct {
      UINT SupportNonVGA  :1;
      UINT SupportSmoothRotation  :1;
      UINT SupportPerEngineTDR  :1;
      UINT SupportKernelModeCommandBuffer  :1;
      UINT SupportCCD  :1;
      UINT SupportSoftwareDeviceBitmaps  :1;
      UINT SupportGammaRamp  :1;
      UINT SupportHWCursor  :1;
      UINT SupportHWVSync  :1;
      UINT SupportSurpriseRemovalInHibernation  :1;
      UINT Reserved  :22;
    };
    UINT   Value;
  };
} D3DKMT_WDDM_1_2_CAPS;
````


## -struct-fields
<dl>

### -field <b>PreemptionCaps</b>

<dd></dd>

### -field <b>SupportNonVGA</b>

<dd></dd>

### -field <b>SupportSmoothRotation</b>

<dd></dd>

### -field <b>SupportPerEngineTDR</b>

<dd></dd>

### -field <b>SupportKernelModeCommandBuffer</b>

<dd></dd>

### -field <b>SupportCCD</b>

<dd></dd>

### -field <b>SupportSoftwareDeviceBitmaps</b>

<dd></dd>

### -field <b>SupportGammaRamp</b>

<dd></dd>

### -field <b>SupportHWCursor</b>

<dd></dd>

### -field <b>SupportHWVSync</b>

<dd></dd>

### -field <b>SupportSurpriseRemovalInHibernation</b>

<dd></dd>

### -field <b>Reserved</b>

<dd></dd>

### -field <b>Value</b>

<dd></dd>
</dl>

## -remarks


## -requirements
<table>
<tr>
<th width="30%">
<p>Minimum supported client</p>
</th>
<td width="70%">
<p>Windows 8</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Minimum supported server</p>
</th>
<td width="70%">
<p>Windows Server 2012</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>D3dkmdt.h (include D3dkmdt.h)</dt>
</dl>
</td>
</tr>
</table>