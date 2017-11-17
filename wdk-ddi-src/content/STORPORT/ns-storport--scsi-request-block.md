---
UID: NS.storport._SCSI_REQUEST_BLOCK
title: SCSI_REQUEST_BLOCK
author: windows-driver-content
description: 
ms.assetid: deb491e3-b227-4ea3-99b7-50aaa5fdd921
ms.author: windowsdriverdev
ms.date: 
ms.topic: struct
ms.prod: windows-hardware
ms.technology: windows-devices
ms.keywords: SCSI_REQUEST_BLOCK, SCSI_REQUEST_BLOCK, *PSCSI_REQUEST_BLOCK
req.header: storport.h
req.include-header:
req.target-type:
req.target-min-winverclnt:
req.target-min-winversvr:
req.kmdf-ver:
req.umdf-ver:
req.lib:
req.dll:
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

# SCSI_REQUEST_BLOCK structure

## -description



## -struct-fields

### -field struct _SCSI_REQUEST_BLOCK			
 	
### -field _SCSI_REQUEST_BLOCK * NextSrb			
 	
### -field union __unnamed_union_0c6c_1			
 	
### -field USHORT Length			
 	
### -field UCHAR Function			
 	
### -field UCHAR SrbStatus			
 	
### -field UCHAR ScsiStatus			
 	
### -field UCHAR PathId			
 	
### -field UCHAR TargetId			
 	
### -field UCHAR Lun			
 	
### -field UCHAR QueueTag			
 	
### -field UCHAR QueueAction			
 	
### -field UCHAR CdbLength			
 	
### -field UCHAR SenseInfoBufferLength			
 	
### -field ULONG SrbFlags			
 	
### -field ULONG DataTransferLength			
 	
### -field ULONG TimeOutValue			
 	
### -field PVOID DataBuffer			
 	
### -field PVOID SenseInfoBuffer			
 	
### -field PVOID OriginalRequest			
 	
### -field PVOID SrbExtension			
 	
### -field ULONG Reserved			
 	
### -field UCHAR [16] Cdb			
 	
### -field ULONG InternalStatus			
 	
### -field ULONG QueueSortKey			
 	
### -field ULONG LinkTimeoutValue			
 	
## -remarks

## -see-also