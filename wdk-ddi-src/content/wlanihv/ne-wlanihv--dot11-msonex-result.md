---
UID: NE.wlanihv._DOT11_MSONEX_RESULT
title: DOT11_MSONEX_RESULT
author: windows-driver-content
description: Important  The Native 802.11 Wireless LAN interface is deprecated in Windows 10 and later.
old-location: netvista\dot11_msonex_result.htm
ms.assetid: d5870125-2c0f-4cb9-ad2a-dc4939745504
ms.author: windowsdriverdev
ms.date: 11/1/2017
ms.topic: enum
ms.prod: windows-hardware
ms.technology: netvista
req.header: wlanihv.h
req.include-header: Wlanihv.h
req.target-type: Windows
req.target-min-winverclnt: Available in Windows Vista and later versions of the Windows operating
   systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: DOT11_MSONEX_RESULT
req.alt-loc: wlanihv.h
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
ms.keywords: PrintPropertyValue, PrintPropertyValue
req.iface: 
req.product: Windows 10 or later.
---

# DOT11_MSONEX_RESULT enumeration



## -description

## -syntax

````
typedef enum _DOT11_MSONEX_RESULT { 
  DOT11_MSONEX_SUCCESS      = 0,
  DOT11_MSONEX_FAILURE      = 1,
  DOT11_MSONEX_IN_PROGRESS  = 2
} DOT11_MSONEX_RESULT, *PDOT11_MSONEX_RESULT;
````


## -enum-fields
<dl>

### -field <a id="DOT11_MSONEX_SUCCESS"></a><a id="dot11_msonex_success"></a><b>DOT11_MSONEX_SUCCESS</b>

<dd>
<p>The 802.1X authentication operation succeeded.</p>
</dd>

### -field <a id="DOT11_MSONEX_FAILURE"></a><a id="dot11_msonex_failure"></a><b>DOT11_MSONEX_FAILURE</b>

<dd>
<p>The 802.1X authentication operation failed.</p>
</dd>

### -field <a id="DOT11_MSONEX_IN_PROGRESS"></a><a id="dot11_msonex_in_progress"></a><b>DOT11_MSONEX_IN_PROGRESS</b>

<dd>
<p>The 802.1X authentication operation is in progress.</p>
</dd>
</dl>

## -remarks
<p>After the IHV Extensions DLL initiates an 802.1X authentication operation, the operating system calls
    the 
    <a href="https://msdn.microsoft.com/bf865b33-6e44-4724-868d-73150cf5b589">
    Dot11ExtIhvOneXIndicateResult</a> IHV handler function to complete the operation. When it calls this
    function, the operating system passes a DOT11_MSONEX_RESULT value to the 
    <i>OneXResult</i> parameter to specify the result of the authentication operation.</p>

<p>After the IHV Extensions DLL initiates an 802.1X authentication operation, the operating system calls
    the 
    <a href="https://msdn.microsoft.com/bf865b33-6e44-4724-868d-73150cf5b589">
    Dot11ExtIhvOneXIndicateResult</a> IHV handler function to complete the operation. When it calls this
    function, the operating system passes a DOT11_MSONEX_RESULT value to the 
    <i>OneXResult</i> parameter to specify the result of the authentication operation.</p>

<p>After the IHV Extensions DLL initiates an 802.1X authentication operation, the operating system calls
    the 
    <a href="https://msdn.microsoft.com/bf865b33-6e44-4724-868d-73150cf5b589">
    Dot11ExtIhvOneXIndicateResult</a> IHV handler function to complete the operation. When it calls this
    function, the operating system passes a DOT11_MSONEX_RESULT value to the 
    <i>OneXResult</i> parameter to specify the result of the authentication operation.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Available in Windows Vista and later versions of the Windows operating
   systems.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Wlanihv.h (include Wlanihv.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/bf865b33-6e44-4724-868d-73150cf5b589">
   Dot11ExtIhvOneXIndicateResult</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff547610">Dot11ExtStartOneX</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [netvista\netvista]:%20DOT11_MSONEX_RESULT enumeration%20 RELEASE:%20(11/1/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>