---
UID: NI.sffdisk.IOCTL_SFFDISK_MMC_QUERY_EXT_CSD
title: IOCTL_SFFDISK_MMC_QUERY_EXT_CSD
author: windows-driver-content
description: 
ms.assetid: c64110a3-10dd-495c-9873-360aed718ad6
ms.author: windowsdriverdev
ms.date: 
ms.topic: ioctl
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: sffdisk.h
req.include-header:
req.target-type:
req.target-min-winverclnt:
req.target-min-winversvr:
req.kmdf-ver:
req.umdf-ver:
req.lib:
req.dll:
req.irql: 
req.ddi-compliance:
req.alt-api:
req.alt-loc:
req.unicode-ansi:
req.idl:
req.max-support:
req.namespace:
req.assembly:
req.type-library:
---

# IOCTL_SFFDISK_MMC_QUERY_EXT_CSD IOCTL

## Major Code:  [[XREF-LINK:IRP_MJ_DEVICE_CONTROL]

## -description



## -ioctlparameters

### -input-buffer

<text></text>

### -input-buffer-length 

<text></text>

### -output-buffer

<text></text>

### -output-buffer-length 

<text></text>

### -in-out-buffer

<text></text>

### -inout-buffer-length 

<text></text>

### -status-block

Irp->IoStatus.Status is set to STATUS_SUCCESS if the request is successful.
Otherwise, Status to the appropriate error condition as a NTSTATUS code. 
For more information, see [XREF-LINK:NTSTATUS Values].

## -remarks

## -see-also