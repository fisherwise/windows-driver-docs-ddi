---
UID: NF.ksproxy.IKsPin.KsDeliver
title: IKsPin::KsDeliver
author: windows-driver-content
description: The KsDeliver method delivers a media sample from an output pin to an input pin, continues an I/O operation by retrieving the next buffer from an allocator, and submits the buffer to the associated device.
old-location: stream\ikspin_ksdeliver.htm
ms.assetid: e527a659-7ed5-4262-bed2-3bab58919401
ms.author: windowsdriverdev
ms.date: 10/25/2017
ms.topic: function
ms.prod: windows-hardware
ms.technology: stream
req.header: ksproxy.h
req.include-header: Ksproxy.h
req.target-type: Desktop
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: IKsPin.KsDeliver
req.alt-loc: ksproxy.h
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
ms.keywords: IKsPin, KsDeliver, IKsPin::KsDeliver
req.iface: IKsPin
---

# IKsPin::KsDeliver method



## -description
<p>The <b>KsDeliver</b> method delivers a media sample from an output pin to an input pin, continues an I/O operation by retrieving the next buffer from an allocator, and submits the buffer to the associated device.</p>


## -syntax

````
HRESULT KsDeliver(
  [in] IMediaSample *Sample,
  [in] ULONG        Flags
);
````


## -parameters
<dl>

### -param <i>Sample</i> [in]

<dd>
<p>Pointer to the <b>IMediaSample</b> interface for the associated media sample.</p>
</dd>

### -param <i>Flags</i> [in]

<dd>
<p>Specifies a bitmask enumerating information about the stream header of the media sample. A bitwise OR combination of the following flags is possible:</p>
<dl>
<dd>
<p>KSSTREAM_HEADER_OPTIONSF_SPLICEPOINT</p>
</dd>
<dd>
<p>KSSTREAM_HEADER_OPTIONSF_PREROLL</p>
</dd>
<dd>
<p>KSSTREAM_HEADER_OPTIONSF_DATADISCONTINUITY</p>
</dd>
<dd>
<p>KSSTREAM_HEADER_OPTIONSF_TYPECHANGED</p>
</dd>
<dd>
<p>KSSTREAM_HEADER_OPTIONSF_TIMEVALID</p>
</dd>
<dd>
<p>KSSTREAM_HEADER_OPTIONSF_TIMEDISCONTINUITY</p>
</dd>
<dd>
<p>KSSTREAM_HEADER_OPTIONSF_FLUSHONPAUSE</p>
</dd>
<dd>
<p>KSSTREAM_HEADER_OPTIONSF_DURATIONVALID</p>
</dd>
<dd>
<p>KSSTREAM_HEADER_OPTIONSF_ENDOFSTREAM</p>
</dd>
<dd>
<p>KSSTREAM_HEADER_OPTIONSF_LOOPEDDATA</p>
</dd>
</dl>
<p>These flags are defined in the <b>OptionsFlags</b> member of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff567138">KSSTREAM_HEADER</a> structure description.</p>
<p>The pin connection checks for the end-of-stream flag (KSSTREAM_HEADER_OPTIONSF_ENDOFSTREAM) to determine if it must deliver an end-of-stream event after the sample completes.</p>
</dd>
</dl>

## -returns
<p>Returns NOERROR if successful; otherwise, returns an error code.</p>

## -remarks
<p>An interface handler (<a href="https://msdn.microsoft.com/library/windows/hardware/ff559855">IKsInterfaceHandler</a>) calls <b>KsDeliver</b> on the output pin of a filter to deliver a media sample to the input pin of another filter. These input and output pins are connected. </p>

<p>For an input pin, <b>KsDeliver</b> is an invalid entry point and returns EFAIL. </p>

<p>For more information about <b>IMediaSample</b>, see the Microsoft Windows SDK documentation.</p>

<p>An interface handler (<a href="https://msdn.microsoft.com/library/windows/hardware/ff559855">IKsInterfaceHandler</a>) calls <b>KsDeliver</b> on the output pin of a filter to deliver a media sample to the input pin of another filter. These input and output pins are connected. </p>

<p>For an input pin, <b>KsDeliver</b> is an invalid entry point and returns EFAIL. </p>

<p>For more information about <b>IMediaSample</b>, see the Microsoft Windows SDK documentation.</p>

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
<dt>Ksproxy.h (include Ksproxy.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff559855">IKsInterfaceHandler</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff559862">IKsInterfaceHandler::KsCompleteIo</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [stream\stream]:%20IKsPin::KsDeliver method%20 RELEASE:%20(10/25/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>