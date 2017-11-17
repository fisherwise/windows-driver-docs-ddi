---
UID: NS.dispmprt._DXGK_I2C_INTERFACE
title: DXGK_I2C_INTERFACE
author: windows-driver-content
description: The DXGK_I2C_INTERFACE structure contains pointers to functions in the I2C interface, which is implemented by the display miniport driver.
old-location: display\dxgk_i2c_interface.htm
ms.assetid: aba0ebc8-2c92-4d27-a35b-9ac25ac6e5ab
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: display
req.header: dispmprt.h
req.include-header: Dispmprt.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DXGK_I2C_INTERFACE
req.alt-loc: dispmprt.h
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
ms.keywords: DXGK_I2C_INTERFACE, DXGK_I2C_INTERFACE, *PDXGK_I2C_INTERFACE
req.iface: 
---

# DXGK_I2C_INTERFACE structure



## -description
<p>The DXGK_I2C_INTERFACE structure contains pointers to functions in the <a href="https://msdn.microsoft.com/library/windows/hardware/ff567386">I2C interface</a>, which is implemented by the display miniport driver.</p>


## -syntax

````
typedef struct _DXGK_I2C_INTERFACE {
  USHORT                                Size;
  USHORT                                Version;
  PVOID                                 Context;
  PINTERFACE_REFERENCE                  InterfaceReference;
  PINTERFACE_DEREFERENCE                InterfaceDereference;
  DXGKDDI_I2C_TRANSMIT_DATA_TO_DISPLAY  DxgkDdiI2CTransmitDataToDisplay;
  DXGKDDI_I2C_RECEIVE_DATA_FROM_DISPLAY DxgkDdiI2CReceiveDataFromDisplay;
} DXGK_I2C_INTERFACE, *PDXGK_I2C_INTERFACE;
````


## -struct-fields
<dl>

### -field <b>Size</b>

<dd>
<p>The size, in bytes, of this structure.</p>
</dd>

### -field <b>Version</b>

<dd>
<p>The version number of the I2C interface. Version number constants are defined in <i>Dispmprt.h</i> (for example, DXGK_I2C_INTERFACE_VERSION_1).</p>
</dd>

### -field <b>Context</b>

<dd>
<p>A pointer to a private context block.</p>
</dd>

### -field <b>InterfaceReference</b>

<dd>
<p>A pointer to an interface reference function that is implemented by the display miniport driver.</p>
</dd>

### -field <b>InterfaceDereference</b>

<dd>
<p>A pointer to an interface dereference function that is implemented by the display miniport driver.</p>
</dd>

### -field <b>DxgkDdiI2CTransmitDataToDisplay</b>

<dd>
<p>A pointer to the display miniport driver's <a href="https://msdn.microsoft.com/67a08982-5d2f-4cd8-be14-76977fde0aac">DxgkDdiI2CTransmitDataToDisplay</a> function.</p>
</dd>

### -field <b>DxgkDdiI2CReceiveDataFromDisplay</b>

<dd>
<p>A pointer to the display miniport driver's <a href="https://msdn.microsoft.com/7b412180-e453-4ae4-95a5-e5393e1d9197">DxgkDdiI2CReceiveDataFromDisplay</a> function.</p>
</dd>
</dl>

## -remarks
<p>A kernel-mode component that needs to use the I2C interface calls the display miniport driver's <a href="https://msdn.microsoft.com/d8255f36-be3a-4b19-ac8d-8748ac9b6a24">DxgkDdiQueryInterface</a> function.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Available in Windows Vista and later versions of the Windows operating systems.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Dispmprt.h (include Dispmprt.h)</dt>
</dl>
</td>
</tr>
</table>