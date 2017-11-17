---
UID: NC.hdaudio.PREGISTER_EVENT_CALLBACK
title: PREGISTER_EVENT_CALLBACK
author: windows-driver-content
description: The RegisterEventCallback routine registers a callback routine for an unsolicited response from a codec or codecs.The function pointer type for a RegisterEventCallback routine is defined as:
old-location: audio\registereventcallback.htm
ms.assetid: 0f94146b-aa60-4106-aba6-0f1cb3e53008
ms.author: windowsdriverdev
ms.date: 10/30/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: audio
req.header: hdaudio.h
req.include-header: Hdaudio.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: RegisterEventCallback
req.alt-loc: hdaudio.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL (See Remarks section)
ms.keywords: SM_SetRNIDMgmtInfo_OUT, SM_SetRNIDMgmtInfo_OUT, *PSM_SetRNIDMgmtInfo_OUT
req.iface: 
---

# PREGISTER_EVENT_CALLBACK callback



## -description
<p>The <i>RegisterEventCallback</i> routine registers a callback routine for an unsolicited response from a codec or codecs.</p>
<p>The function pointer type for a <i>RegisterEventCallback</i> routine is defined as:</p>


## -prototype

````
PREGISTER_EVENT_CALLBACK RegisterEventCallback;

NTSTATUS RegisterEventCallback(
  _In_  PVOID                                  context,
  _In_  PHDAUDIO_UNSOLICITED_RESPONSE_CALLBACK routine,
  _In_  PVOID                                  callbackContext,
  _Out_ PUCHAR                                 tag
)
{ ... }
````


## -parameters
<dl>

### -param <i>context</i> [in]

<dd>
<p>Specifies the context value from the <b>Context</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff536413">HDAUDIO_BUS_INTERFACE</a><u>, </u><a href="https://msdn.microsoft.com/library/windows/hardware/ff536418">HDAUDIO_BUS_INTERFACE_V2</a>, or <a href="https://msdn.microsoft.com/library/windows/hardware/ff536416">HDAUDIO_BUS_INTERFACE_BDL</a> structure.</p>
</dd>

### -param <i>routine</i> [in]

<dd>
<p>Function pointer to a callback routine. This parameter must be a valid, non-NULL function pointer of type PHDAUDIO_UNSOLICITED_RESPONSE_CALLBACK. For more information, see the following Remarks section.</p>
</dd>

### -param <i>callbackContext</i> [in]

<dd>
<p>Specifies a context value for the callback routine. The caller casts the context value to type PVOID. When a codec generates an unsolicited response that contains the specified tag, the HD Audio bus driver passes the context value to the callback routine as a call parameter.</p>
</dd>

### -param <i>tag</i> [out]

<dd>
<p>Retrieves a tag value that identifies the unsolicited response. This parameter points to a caller-allocated UCHAR variable into which the routine writes the tag value. The caller should specify this tag value when programming the codec or codecs to generate the unsolicited response. For more information, see the following Remarks section.</p>
</dd>
</dl>

## -returns
<p><i>RegisterEventCallback</i> returns STATUS_SUCCESS if the call succeeds in registering the event. Otherwise, the routine returns an appropriate error code. The following table shows a possible return status code.</p><dl>
<dt><b>STATUS_INSUFFICIENT_RESOURCES</b></dt>
</dl><p>Indicates that not enough resources are available to complete the operation.</p>

<p> </p>

## -remarks
<p>This routine registers a callback routine for an unsolicited response from a codec. The routine outputs a tag to identify the unsolicited response. When the HD Audio bus driver encounters an unsolicited response from any codec with a matching tag value, the routine calls the specified callback routine at IRQL DISPATCH_LEVEL and passes the specified context value to the routine as a call parameter.</p>

<p>Following the call to <i>RegisterEventCallback</i>, the function driver is responsible for programming the codec or codecs to generate unsolicited responses with the specified tag.</p>

<p>The routine assigns a unique tag to each registered callback routine. The unique association between tag and callback routine persists as long as the callback routine remains registered. The function driver can delete the registration of a callback routine by calling <a href="https://msdn.microsoft.com/698017a0-13d5-4ed5-a1ce-1a50a62135e0">UnregisterEventCallback</a>.</p>

<p>Currently, the bus driver can supply up to 64 unique tags per codec.</p>

<p>The callback parameter is a function pointer to a callback routine in the function driver. The function pointer type for the callback routine is defined as:</p>

<p>The first call parameter is a structure of type <a href="https://msdn.microsoft.com/library/windows/hardware/ff536422">HDAUDIO_CODEC_RESPONSE</a> that specifies the codec's response to the command. This structure is passed by value. The second call parameter is the <i>callbackContext</i> value that was passed previously to <i>RegisterEventCallback</i>. The HD Audio bus driver calls the callback routine at IRQL DISPATCH_LEVEL.</p>

<p>This routine registers a callback routine for an unsolicited response from a codec. The routine outputs a tag to identify the unsolicited response. When the HD Audio bus driver encounters an unsolicited response from any codec with a matching tag value, the routine calls the specified callback routine at IRQL DISPATCH_LEVEL and passes the specified context value to the routine as a call parameter.</p>

<p>Following the call to <i>RegisterEventCallback</i>, the function driver is responsible for programming the codec or codecs to generate unsolicited responses with the specified tag.</p>

<p>The routine assigns a unique tag to each registered callback routine. The unique association between tag and callback routine persists as long as the callback routine remains registered. The function driver can delete the registration of a callback routine by calling <a href="https://msdn.microsoft.com/698017a0-13d5-4ed5-a1ce-1a50a62135e0">UnregisterEventCallback</a>.</p>

<p>Currently, the bus driver can supply up to 64 unique tags per codec.</p>

<p>The callback parameter is a function pointer to a callback routine in the function driver. The function pointer type for the callback routine is defined as:</p>

<p>The first call parameter is a structure of type <a href="https://msdn.microsoft.com/library/windows/hardware/ff536422">HDAUDIO_CODEC_RESPONSE</a> that specifies the codec's response to the command. This structure is passed by value. The second call parameter is the <i>callbackContext</i> value that was passed previously to <i>RegisterEventCallback</i>. The HD Audio bus driver calls the callback routine at IRQL DISPATCH_LEVEL.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Target platform</p>
</th>
<td width="70%">
<dl>
<dt>Desktop</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Hdaudio.h (include Hdaudio.h)</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>PASSIVE_LEVEL (See Remarks section)</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536413">HDAUDIO_BUS_INTERFACE</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536418">HDAUDIO_BUS_INTERFACE_V2</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536416">HDAUDIO_BUS_INTERFACE_BDL</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/698017a0-13d5-4ed5-a1ce-1a50a62135e0">UnregisterEventCallback</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff536422">HDAUDIO_CODEC_RESPONSE</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [audio\audio]:%20PREGISTER_EVENT_CALLBACK callback function%20 RELEASE:%20(10/30/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>