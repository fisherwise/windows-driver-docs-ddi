---
UID: NC.sercx.EVT_SERCX_CONTROL
title: EVT_SERCX_CONTROL
author: windows-driver-content
description: The EvtSerCxControl event callback function handles an I/O control request that has an I/O control code (IOCTL) that the serial framework extension (SerCx) supports.
old-location: serports\evtsercxcontrol.htm
ms.assetid: 2A88BA68-48A7-4C00-8031-CCC50A0C090D
ms.author: windowsdriverdev
ms.date: 10/23/2017
ms.topic: callback
ms.prod: windows-hardware
ms.technology: serports
req.header: sercx.h
req.include-header: 
req.target-type: Desktop
req.target-min-winverclnt: Available starting with Windows 8.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: EvtSerCxControl
req.alt-loc: 1.0\Sercx.h
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: Called at IRQL <= DISPATCH_LEVEL
ms.keywords: SENSOR_VALUE_PAIR, SENSOR_VALUE_PAIR, *PSENSOR_VALUE_PAIR
req.iface: 
req.product: Windows 10 or later.
---

# EVT_SERCX_CONTROL callback



## -description
<p>The <i>EvtSerCxControl</i> event callback function handles an I/O control request that has an I/O control code (IOCTL) that the serial framework extension (SerCx) supports.</p>


## -prototype

````
EVT_SERCX_CONTROL EvtSerCxControl;

NTSTATUS EvtSerCxControl(
  _In_ WDFDEVICE  Device,
  _In_ WDFREQUEST Request,
  _In_ size_t     OutputBufferLength,
  _In_ size_t     InputBufferLength,
  _In_ ULONG      IoControlCode
)
{ ... }
````


## -parameters
<dl>

### -param <i>Device</i> [in]

<dd>
<p>A WDFDEVICE handle to the framework device object that represents the serial controller.</p>
</dd>

### -param <i>Request</i> [in]

<dd>
<p>A WDFREQUEST handle to the framework request object that represents the I/O control request.</p>
</dd>

### -param <i>OutputBufferLength</i> [in]

<dd>
<p>Specifies the length, in bytes, of the output buffer for the I/O control request specified by the <i>Request</i> parameter.</p>
</dd>

### -param <i>InputBufferLength</i> [in]

<dd>
<p>Specifies the length, in bytes, of the input buffer for the I/O control request specified by the <i>Request</i> parameter.</p>
</dd>

### -param <i>IoControlCode</i> [in]

<dd>
<p>Specifies the IOCTL from the I/O control request specified by the <i>Request</i> parameter.</p>
</dd>
</dl>

## -returns
<p>The <i>EvtSerCxControl</i> function returns STATUS_SUCCESS if the call is successful. Otherwise, it returns an appropriate error status code. For more information, see the following Remarks section.</p>

## -remarks
<p>The serial controller driver is required to implement this callback function. SerCx calls this function to hand off an I/O control request to the controller driver for processing. Before this function returns, it must complete the request either by performing the requested operation or by returning an error status. A driver that does not implement support for a particular request should return the STATUS_NOT_IMPLEMENTED error status for this request.</p>

<p>Typically, the <i>EvtSerCxControl</i> function should synchronize to the controller driver's ISR before this function changes the settings in the hardware registers of the serial controller.</p>

<p>The <i>EvtSerCxControl</i> function's return value must match the status value that this function writes to the status block of the I/O control request. SerCx uses the return value to track the state of the controller driver and the serial controller hardware.</p>

<p>The following is a list of the IOCTLs that this callback function must be prepared to handle:</p><dl>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546538">IOCTL_SERIAL_CLEAR_STATS</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546541">IOCTL_SERIAL_CLR_DTR</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546545">IOCTL_SERIAL_CLR_RTS</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546554">IOCTL_SERIAL_GET_BAUD_RATE</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546558">IOCTL_SERIAL_GET_CHARS</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546562">IOCTL_SERIAL_GET_COMMSTATUS</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546566">IOCTL_SERIAL_GET_DTRRTS</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546574">IOCTL_SERIAL_GET_HANDFLOW</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546620">IOCTL_SERIAL_IMMEDIATE_CHAR</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546582">IOCTL_SERIAL_GET_LINE_CONTROL</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546591">IOCTL_SERIAL_GET_MODEM_CONTROL</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546587">IOCTL_SERIAL_GET_MODEMSTATUS</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546597">IOCTL_SERIAL_GET_PROPERTIES</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546600">IOCTL_SERIAL_GET_STATS</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546649">IOCTL_SERIAL_LSRMST_INSERT</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546672">IOCTL_SERIAL_SET_BAUD_RATE</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546680">IOCTL_SERIAL_SET_BREAK_OFF</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546685">IOCTL_SERIAL_SET_BREAK_ON</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546688">IOCTL_SERIAL_SET_CHARS</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546696">IOCTL_SERIAL_SET_DTR</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546720">IOCTL_SERIAL_SET_FIFO_CONTROL</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546736">IOCTL_SERIAL_SET_HANDFLOW</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546740">IOCTL_SERIAL_SET_LINE_CONTROL</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546748">IOCTL_SERIAL_SET_MODEM_CONTROL</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546760">IOCTL_SERIAL_SET_RTS</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546784">IOCTL_SERIAL_SET_XOFF</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546793">IOCTL_SERIAL_SET_XON</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546812">IOCTL_SERIAL_XOFF_COUNTER</a>
</dd>
</dl><p>To register an <i>EvtSerCxControl</i> callback function, the controller driver calls the <a href="https://msdn.microsoft.com/library/windows/hardware/hh406711">SerCxInitialize</a> method during the <a href="https://msdn.microsoft.com/b20db029-ee2c-4fb1-bd69-ccd2e37fdc9a">EvtDriverDeviceAdd</a> callback.</p>

<p>The function type for this callback is declared in Sercx.h, as follows.</p>

<p>To define an <i>EvtSerCxControl</i> callback function that is named <code>MyEvtSerCxControl</code>, you must first provide a function declaration that <a href="NULL">Static Driver Verifier</a> (SDV) and other verification tools require, as follows.</p>

<p>Then, implement your callback function as follows.</p>

<p>For more information about SDV requirements for function declarations, see <a href="https://msdn.microsoft.com/73a408ba-0219-4fde-8dad-ca330e4e67c3">Declaring Functions Using Function Role Types for KMDF Drivers</a>.</p>

<p>The serial controller driver is required to implement this callback function. SerCx calls this function to hand off an I/O control request to the controller driver for processing. Before this function returns, it must complete the request either by performing the requested operation or by returning an error status. A driver that does not implement support for a particular request should return the STATUS_NOT_IMPLEMENTED error status for this request.</p>

<p>Typically, the <i>EvtSerCxControl</i> function should synchronize to the controller driver's ISR before this function changes the settings in the hardware registers of the serial controller.</p>

<p>The <i>EvtSerCxControl</i> function's return value must match the status value that this function writes to the status block of the I/O control request. SerCx uses the return value to track the state of the controller driver and the serial controller hardware.</p>

<p>The following is a list of the IOCTLs that this callback function must be prepared to handle:</p><dl>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546538">IOCTL_SERIAL_CLEAR_STATS</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546541">IOCTL_SERIAL_CLR_DTR</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546545">IOCTL_SERIAL_CLR_RTS</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546554">IOCTL_SERIAL_GET_BAUD_RATE</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546558">IOCTL_SERIAL_GET_CHARS</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546562">IOCTL_SERIAL_GET_COMMSTATUS</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546566">IOCTL_SERIAL_GET_DTRRTS</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546574">IOCTL_SERIAL_GET_HANDFLOW</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546620">IOCTL_SERIAL_IMMEDIATE_CHAR</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546582">IOCTL_SERIAL_GET_LINE_CONTROL</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546591">IOCTL_SERIAL_GET_MODEM_CONTROL</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546587">IOCTL_SERIAL_GET_MODEMSTATUS</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546597">IOCTL_SERIAL_GET_PROPERTIES</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546600">IOCTL_SERIAL_GET_STATS</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546649">IOCTL_SERIAL_LSRMST_INSERT</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546672">IOCTL_SERIAL_SET_BAUD_RATE</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546680">IOCTL_SERIAL_SET_BREAK_OFF</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546685">IOCTL_SERIAL_SET_BREAK_ON</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546688">IOCTL_SERIAL_SET_CHARS</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546696">IOCTL_SERIAL_SET_DTR</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546720">IOCTL_SERIAL_SET_FIFO_CONTROL</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546736">IOCTL_SERIAL_SET_HANDFLOW</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546740">IOCTL_SERIAL_SET_LINE_CONTROL</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546748">IOCTL_SERIAL_SET_MODEM_CONTROL</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546760">IOCTL_SERIAL_SET_RTS</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546784">IOCTL_SERIAL_SET_XOFF</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546793">IOCTL_SERIAL_SET_XON</a>
</dd>
<dd>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff546812">IOCTL_SERIAL_XOFF_COUNTER</a>
</dd>
</dl><p>To register an <i>EvtSerCxControl</i> callback function, the controller driver calls the <a href="https://msdn.microsoft.com/library/windows/hardware/hh406711">SerCxInitialize</a> method during the <a href="https://msdn.microsoft.com/b20db029-ee2c-4fb1-bd69-ccd2e37fdc9a">EvtDriverDeviceAdd</a> callback.</p>

<p>The function type for this callback is declared in Sercx.h, as follows.</p>

<p>To define an <i>EvtSerCxControl</i> callback function that is named <code>MyEvtSerCxControl</code>, you must first provide a function declaration that <a href="NULL">Static Driver Verifier</a> (SDV) and other verification tools require, as follows.</p>

<p>Then, implement your callback function as follows.</p>

<p>For more information about SDV requirements for function declarations, see <a href="https://msdn.microsoft.com/73a408ba-0219-4fde-8dad-ca330e4e67c3">Declaring Functions Using Function Role Types for KMDF Drivers</a>.</p>

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
<p>Version</p>
</th>
<td width="70%">
<p>Available starting with Windows 8.</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>1.0\Sercx.h</dt>
</dl>
</td>
</tr>
<tr>
<th width="30%">
<p>IRQL</p>
</th>
<td width="70%">
<p>Called at IRQL &lt;= DISPATCH_LEVEL</p>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/b20db029-ee2c-4fb1-bd69-ccd2e37fdc9a">EvtDriverDeviceAdd</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/hh406711">SerCxInitialize</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [serports\serports]:%20EVT_SERCX_CONTROL callback function%20 RELEASE:%20(10/23/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>