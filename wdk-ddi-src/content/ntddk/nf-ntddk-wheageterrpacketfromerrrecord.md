---
UID: NF:ntddk.WheaGetErrPacketFromErrRecord
title: WheaGetErrPacketFromErrRecord function
author: windows-driver-content
description: The WheaGetErrPacketFromErrRecord function returns a pointer to the hardware error packet that is contained within a WHEA error record. The hardware error packet is formatted as a WHEA_ERROR_PACKET structure.
old-location: whea\wheageterrpacketfromerrrecord.htm
old-project: whea
ms.assetid: 8b4a835f-b1ec-4308-8e0d-a13c0f421dc8
ms.author: windowsdriverdev
ms.date: 2/20/2018
ms.keywords: WheaGetErrPacketFromErrRecord, WheaGetErrPacketFromErrRecord function [WHEA Drivers and Applications], ntddk/WheaGetErrPacketFromErrRecord, whea.wheageterrpacketfromerrrecord, whearef2_c7c202ca-0ed0-4a12-a3f0-64723e6483c6.xml
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: ntddk.h
req.include-header: Ntddk.h
req.target-type: Desktop
req.target-min-winverclnt: Supported in Windows Server 2008, Windows Vista SP1, and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: "<=DISPATCH_LEVEL"
topic_type:
-	APIRef
-	kbSyntax
api_type:
-	HeaderDef
api_location:
-	ntddk.h
api_name:
-	WheaGetErrPacketFromErrRecord
product:
- Windows
targetos: Windows
req.typenames: WHEA_RAW_DATA_FORMAT, *PWHEA_RAW_DATA_FORMAT
---

# WheaGetErrPacketFromErrRecord function


## -description


The <b>WheaGetErrPacketFromErrRecord</b> function returns a pointer to the hardware error packet that is contained within a WHEA <a href="https://msdn.microsoft.com/080da29a-b5cb-45a5-848d-048d9612ee2a">error record</a>. The hardware error packet is formatted as a <a href="https://msdn.microsoft.com/library/windows/hardware/ff560465">WHEA_ERROR_PACKET</a> structure.


## -parameters




### -param Record [in]

A pointer to a WHEA <a href="https://msdn.microsoft.com/080da29a-b5cb-45a5-848d-048d9612ee2a">error record</a> that is formatted as a <a href="https://msdn.microsoft.com/library/windows/hardware/ff560483">WHEA_ERROR_RECORD</a> structure.


## -returns



<b>WheaGetErrPacketFromErrRecord</b> returns a pointer to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff560465">WHEA_ERROR_PACKET</a> structure within the <a href="https://msdn.microsoft.com/library/windows/hardware/ff560483">WHEA_ERROR_RECORD</a> structure. If the function does not locate the WHEA_ERROR_PACKET structure, it returns <b>NULL</b>.




## -remarks



The <b>WheaGetErrPacketFromErrRecord</b> function returns a pointer to the hardware error packet that is contained within an error record.




## -see-also




<a href="https://msdn.microsoft.com/080da29a-b5cb-45a5-848d-048d9612ee2a">Error record</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/ff560465">WHEA_ERROR_PACKET</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/ff560483">WHEA_ERROR_RECORD</a>
 

 

