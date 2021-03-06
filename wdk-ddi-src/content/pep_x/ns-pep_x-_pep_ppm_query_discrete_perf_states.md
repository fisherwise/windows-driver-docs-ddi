---
UID: NS:pep_x._PEP_PPM_QUERY_DISCRETE_PERF_STATES
title: "_PEP_PPM_QUERY_DISCRETE_PERF_STATES"
author: windows-driver-content
description: Used in the PEP_NOTIFY_PPM_QUERY_DISCRETE_PERF_STATES notification that stores the list of discrete performance states that PEP supports, if the PEP_NOTIFY_PPM_QUERY_CAPABILITIES notification indicates support for discrete performance states. .
old-location: kernel\pep_ppm_query_discrete_perf_states.htm
old-project: kernel
ms.assetid: 506b3d8e-4aba-4e70-a6db-52a52d717c6b
ms.author: windowsdriverdev
ms.date: 3/28/2018
ms.keywords: "*PPEP_PPM_QUERY_DISCRETE_PERF_STATES, PEP_PPM_QUERY_DISCRETE_PERF_STATES, PEP_PPM_QUERY_DISCRETE_PERF_STATES structure [Kernel-Mode Driver Architecture], PPEP_PPM_QUERY_DISCRETE_PERF_STATES, PPEP_PPM_QUERY_DISCRETE_PERF_STATES structure pointer [Kernel-Mode Driver Architecture], _PEP_PPM_QUERY_DISCRETE_PERF_STATES, kernel.pep_ppm_query_discrete_perf_states, pepfx/PEP_PPM_QUERY_DISCRETE_PERF_STATES, pepfx/PPEP_PPM_QUERY_DISCRETE_PERF_STATES"
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: struct
req.header: pep_x.h
req.include-header: Pep_x.h
req.target-type: Windows
req.target-min-winverclnt: Windows 10, version 1709
req.target-min-winversvr: Windows Server 2016
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
req.irql: PASSIVE_LEVEL
topic_type:
-	APIRef
-	kbSyntax
api_type:
-	HeaderDef
api_location:
-	Pepfx.h
api_name:
-	PEP_PPM_QUERY_DISCRETE_PERF_STATES
product:
- Windows
targetos: Windows
req.typenames: PEP_PPM_QUERY_DISCRETE_PERF_STATES, *PPEP_PPM_QUERY_DISCRETE_PERF_STATES, PEP_PPM_QUERY_DISCRETE_PERF_STATES, *PPEP_PPM_QUERY_DISCRETE_PERF_STATES
---

# _PEP_PPM_QUERY_DISCRETE_PERF_STATES structure


## -description


Used in the <b>PEP_NOTIFY_PPM_QUERY_DISCRETE_PERF_STATES</b> notification that stores the list of discrete performance states that PEP supports, if the <b>PEP_NOTIFY_PPM_QUERY_CAPABILITIES</b> notification indicates support for discrete performance states. 


## -struct-fields




### -field Count

On input, the size of the array pointed to by <i>States</i>. 


### -field States

On output, an array of <a href="https://msdn.microsoft.com/46231ac0-2c34-4154-8b3e-f34c40cbff4a">PEP_PROCESSOR_PERF_STATE</a> structures that indicates performance states that is filled by  PEP. 


## -see-also




<a href="https://msdn.microsoft.com/library/windows/hardware/mt186820">PEP_PPM_QUERY_CAPABILITIES</a>



<a href="https://msdn.microsoft.com/library/windows/hardware/mt186881">Processor power management (PPM) notifications</a>
 

 

