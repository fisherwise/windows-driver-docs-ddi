---
UID: NS.ntddk._WHEA_PCIEXPRESS_ERROR_SECTION
title: WHEA_PCIEXPRESS_ERROR_SECTION
author: windows-driver-content
description: The WHEA_PCIEXPRESS_ERROR_SECTION structure describes PCI Express (PCIe) error data.
old-location: whea\whea_pciexpress_error_section.htm
ms.assetid: 1d96a799-6e52-49e0-b440-a8643111176f
ms.author: windowsdriverdev
ms.date: 10/23/2017
ms.topic: struct
ms.prod: windows-hardware
ms.technology: whea
req.header: ntddk.h
req.include-header: Ntddk.h
req.target-type: Windows
req.target-min-winverclnt: Supported in Windows Server 2008, Windows Vista SP1, and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.alt-api: WHEA_PCIEXPRESS_ERROR_SECTION
req.alt-loc: ntddk.h
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
ms.keywords: WHEA_PCIEXPRESS_ERROR_SECTION, WHEA_PCIEXPRESS_ERROR_SECTION, *PWHEA_PCIEXPRESS_ERROR_SECTION
req.iface: 
---

# WHEA_PCIEXPRESS_ERROR_SECTION structure



## -description
<p>The WHEA_PCIEXPRESS_ERROR_SECTION structure describes PCI Express (PCIe) error data.</p>


## -syntax

````
typedef struct _WHEA_PCIEXPRESS_ERROR_SECTION {
  WHEA_PCIEXPRESS_ERROR_SECTION_VALIDBITS ValidBits;
  WHEA_PCIEXPRESS_DEVICE_TYPE             PortType;
  WHEA_PCIEXPRESS_VERSION                 Version;
  WHEA_PCIEXPRESS_COMMAND_STATUS          CommandStatus;
  ULONG                                   Reserved;
  WHEA_PCIEXPRESS_DEVICE_ID               DeviceId;
  ULONGLONG                               DeviceSerialNumber;
  WHEA_PCIEXPRESS_BRIDGE_CONTROL_STATUS   BridgeControlStatus;
  UCHAR                                   ExpressCapability[60];
  UCHAR                                   AerInfo[96];
} WHEA_PCIEXPRESS_ERROR_SECTION, *PWHEA_PCIEXPRESS_ERROR_SECTION;
````


## -struct-fields
<dl>

### -field <b>ValidBits</b>

<dd>
<p>A <a href="https://msdn.microsoft.com/library/windows/hardware/ff560580">WHEA_PCIEXPRESS_ERROR_SECTION_VALIDBITS</a> union that specifies which members of this structure contain valid data.</p>
</dd>

### -field <b>PortType</b>

<dd>
<p>The device type or port type of the PCIe component where the error occurred. Possible values are:</p>
<p></p>
<dl>

### -field <a id="WheaPciExpressEndpoint"></a><a id="wheapciexpressendpoint"></a><a id="WHEAPCIEXPRESSENDPOINT"></a><b>WheaPciExpressEndpoint</b>

<dd>
<p>A PCIe endpoint device.</p>
</dd>

### -field <a id="WheaPciExpressLegacyEndpoint"></a><a id="wheapciexpresslegacyendpoint"></a><a id="WHEAPCIEXPRESSLEGACYENDPOINT"></a><b>WheaPciExpressLegacyEndpoint</b>

<dd>
<p>A legacy PCIe endpoint device.</p>
</dd>

### -field <a id="WheaPciExpressRootPort"></a><a id="wheapciexpressrootport"></a><a id="WHEAPCIEXPRESSROOTPORT"></a><b>WheaPciExpressRootPort</b>

<dd>
<p>A root port of a PCIe root complex.</p>
</dd>

### -field <a id="WheaPciExpressUpstreamSwitchPort"></a><a id="wheapciexpressupstreamswitchport"></a><a id="WHEAPCIEXPRESSUPSTREAMSWITCHPORT"></a><b>WheaPciExpressUpstreamSwitchPort</b>

<dd>
<p>An upstream port of a PCIe switch.</p>
</dd>

### -field <a id="WheaPciExpressDownstreamSwitchPort"></a><a id="wheapciexpressdownstreamswitchport"></a><a id="WHEAPCIEXPRESSDOWNSTREAMSWITCHPORT"></a><b>WheaPciExpressDownstreamSwitchPort</b>

<dd>
<p>A downstream port of a PCIe switch.</p>
</dd>

### -field <a id="WheaPciExpressToPciXBridge"></a><a id="wheapciexpresstopcixbridge"></a><a id="WHEAPCIEXPRESSTOPCIXBRIDGE"></a><b>WheaPciExpressToPciXBridge</b>

<dd>
<p>A PCIe-to-PCI or PCI-X bridge.</p>
</dd>

### -field <a id="WheaPciXToExpressBridge"></a><a id="wheapcixtoexpressbridge"></a><a id="WHEAPCIXTOEXPRESSBRIDGE"></a><b>WheaPciXToExpressBridge</b>

<dd>
<p>A PCI or PCI-X-to-PCIe bridge.</p>
</dd>

### -field <a id="WheaPciExpressRootComplexIntegratedEndpoint"></a><a id="wheapciexpressrootcomplexintegratedendpoint"></a><a id="WHEAPCIEXPRESSROOTCOMPLEXINTEGRATEDENDPOINT"></a><b>WheaPciExpressRootComplexIntegratedEndpoint</b>

<dd>
<p>A PCIe endpoint device that is integrated into the root complex.</p>
</dd>

### -field <a id="WheaPciExpressRootComplexEventCollector"></a><a id="wheapciexpressrootcomplexeventcollector"></a><a id="WHEAPCIEXPRESSROOTCOMPLEXEVENTCOLLECTOR"></a><b>WheaPciExpressRootComplexEventCollector</b>

<dd>
<p>A PCIe root complex event collector.</p>
</dd>
</dl>
<p>This member contains valid data only if the <b>ValidBits.PortType</b> bit is set.</p>
</dd>

### -field <b>Version</b>

<dd>
<p>A WHEA_PCIEXPRESS_VERSION union that contains the version of the PCIe specification that is supported by the hardware platform. The WHEA_PCIEXPRESS_VERSION union is defined as follows:</p>
<div class="code"><span codelanguage=""><table>
<tr>
<th></th>
</tr>
<tr>
<td>
<pre>typedef union _WHEA_PCIEXPRESS_VERSION {
  struct {
    UCHAR  MinorVersion;
    UCHAR  MajorVersion;
    USHORT  Reserved;
  };
  ULONG  AsULONG;
} WHEA_PCIEXPRESS_VERSION, *PWHEA_PCIEXPRESS_VERSION;</pre>
</td>
</tr>
</table></span></div>
<p></p>
<dl>

### -field <a id="MinorVersion"></a><a id="minorversion"></a><a id="MINORVERSION"></a><b>MinorVersion</b>

<dd>
<p>The minor version number.</p>
</dd>

### -field <a id="MajorVersion"></a><a id="majorversion"></a><a id="MAJORVERSION"></a><b>MajorVersion</b>

<dd>
<p>The major version number.</p>
</dd>

### -field <a id="Reserved"></a><a id="reserved"></a><a id="RESERVED"></a><b>Reserved</b>

<dd>
<p>Reserved for system use.</p>
</dd>

### -field <a id="AsULONG"></a><a id="asulong"></a><a id="ASULONG"></a><b>AsULONG</b>

<dd>
<p>A ULONG representation of the contents of the WHEA_PCIEXPRESS_VERSION union.</p>
</dd>
</dl>
<p>This member contains valid data only if the <b>ValidBits.Version</b> bit is set.</p>
</dd>

### -field <b>CommandStatus</b>

<dd>
<p>A WHEA_PCIEXPRESS_COMMAND_STATUS union that contains the contents of the PCI command and status registers of the PCIe device where the error occurred. The WHEA_PCIEXPRESS_COMMAND_STATUS union is defined as follows:</p>
<div class="code"><span codelanguage=""><table>
<tr>
<th></th>
</tr>
<tr>
<td>
<pre>typedef union _WHEA_PCIEXPRESS_COMMAND_STATUS {
  struct {
    USHORT  Command;
    USHORT  Status;
  };
  ULONG  AsULONG;
} WHEA_PCIEXPRESS_COMMAND_STATUS, *PWHEA_PCIEXPRESS_COMMAND_STATUS;</pre>
</td>
</tr>
</table></span></div>
<p></p>
<dl>

### -field <a id="Command"></a><a id="command"></a><a id="COMMAND"></a><b>Command</b>

<dd>
<p>The contents of the PCI command register.</p>
</dd>

### -field <a id="Status"></a><a id="status"></a><a id="STATUS"></a><b>Status</b>

<dd>
<p>The contents of the PCI status register.</p>
</dd>

### -field <a id="AsULONG"></a><a id="asulong"></a><a id="ASULONG"></a><b>AsULONG</b>

<dd>
<p>A ULONG representation of the contents of the WHEA_PCIEXPRESS_COMMAND_STATUS union.</p>
</dd>
</dl>
<p>This member contains valid data only if the <b>ValidBits.CommandStatus</b> bit is set.</p>
</dd>

### -field <b>Reserved</b>

<dd>
<p>Reserved for system use.</p>
</dd>

### -field <b>DeviceId</b>

<dd>
<p>A WHEA_PCIEXPRESS_DEVICE_ID structure that contains data that identifies the PCIe device where the error occurred. The WHEA_PCIEXPRESS_DEVICE_ID structure is defined as follows:</p>
<div class="code"><span codelanguage=""><table>
<tr>
<th></th>
</tr>
<tr>
<td>
<pre>typedef struct _WHEA_PCIEXPRESS_DEVICE_ID {
  USHORT  VendorID;
  USHORT  DeviceID;
  ULONG  ClassCode:24;
  ULONG  FunctionNumber:8;
  ULONG  DeviceNumber:8;
  ULONG  Segment:16;
  ULONG  PrimaryBusNumber:8;
  ULONG  SecondaryBusNumber:8;
  ULONG Reserved1:3;
  ULONG SlotNumber:13;  ULONG  Reserved2:8;
} WHEA_PCIEXPRESS_DEVICE_ID, *PWHEA_PCIEXPRESS_DEVICE_ID;</pre>
</td>
</tr>
</table></span></div>
<p></p>
<dl>

### -field <a id="VendorID"></a><a id="vendorid"></a><a id="VENDORID"></a><b>VendorID</b>

<dd>
<p>The vendor ID of the device.</p>
</dd>

### -field <a id="DeviceId"></a><a id="deviceid"></a><a id="DEVICEID"></a><b>DeviceId</b>

<dd>
<p>The device ID of the device.</p>
</dd>

### -field <a id="ClassCode"></a><a id="classcode"></a><a id="CLASSCODE"></a><b>ClassCode</b>

<dd>
<p>The class code of the device.</p>
</dd>

### -field <a id="FunctionNumber"></a><a id="functionnumber"></a><a id="FUNCTIONNUMBER"></a><b>FunctionNumber</b>

<dd>
<p>The function number of the device on the bus.</p>
</dd>

### -field <a id="DeviceNumber"></a><a id="devicenumber"></a><a id="DEVICENUMBER"></a><b>DeviceNumber</b>

<dd>
<p>The device number of the device on the bus.</p>
</dd>

### -field <a id="Segment"></a><a id="segment"></a><a id="SEGMENT"></a><b>Segment</b>

<dd>
<p>The number of the bus segment that contains the device.</p>
</dd>

### -field <a id="PrimaryBusNumber"></a><a id="primarybusnumber"></a><a id="PRIMARYBUSNUMBER"></a><b>PrimaryBusNumber</b>

<dd>
<p>The root port/bridge primary bus number or the device bus number.</p>
</dd>

### -field <a id="SecondaryBusNumber"></a><a id="secondarybusnumber"></a><a id="SECONDARYBUSNUMBER"></a><b>SecondaryBusNumber</b>

<dd>
<p>The root port/bridge secondary bus number.</p>
</dd>

### -field <a id="Reserved1"></a><a id="reserved1"></a><a id="RESERVED1"></a><b>Reserved1</b>

<dd>
<p>Reserved for system use.</p>
</dd>

### -field <a id="SlotNumber"></a><a id="slotnumber"></a><a id="SLOTNUMBER"></a><b>SlotNumber</b>

<dd>
<p>The slot number where the device is located in the system.</p>
</dd>

### -field <a id="Reserved2"></a><a id="reserved2"></a><a id="RESERVED2"></a><b>Reserved2</b>

<dd>
<p>Reserved for system use.</p>
</dd>
</dl>
<p>This member contains valid data only if the <b>ValidBits.DeviceId</b> bit is set.</p>
</dd>

### -field <b>DeviceSerialNumber</b>

<dd>
<p>The serial number of the PCIe device where the error occurred.</p>
<p>This member contains valid data only if the <b>ValidBits.DeviceSerialNumber</b> bit is set.</p>
</dd>

### -field <b>BridgeControlStatus</b>

<dd>
<p>A WHEA_PCIEXPRESS_BRIDGE_CONTROL_STATUS union that contains the contents of the PCI control and secondary status registers of the bridge device where the error occurred. The WHEA_PCIEXPRESS_BRIDGE_CONTROL_STATUS union is defined as follows:</p>
<div class="code"><span codelanguage=""><table>
<tr>
<th></th>
</tr>
<tr>
<td>
<pre>typedef union _WHEA_PCIEXPRESS_BRIDGE_CONTROL_STATUS {
  struct {
    USHORT  BridgeSecondaryStatus;
    USHORT  BridgeControl;
  };
  ULONG  AsULONG;
} WHEA_PCIEXPRESS_BRIDGE_CONTROL_STATUS, *PWHEA_PCIEXPRESS_BRIDGE_CONTROL_STATUS;</pre>
</td>
</tr>
</table></span></div>
<p></p>
<dl>

### -field <a id="BridgeSecondaryStatus"></a><a id="bridgesecondarystatus"></a><a id="BRIDGESECONDARYSTATUS"></a><b>BridgeSecondaryStatus</b>

<dd>
<p>The contents of the secondary status register of the bridge device.</p>
</dd>

### -field <a id="BridgeControl"></a><a id="bridgecontrol"></a><a id="BRIDGECONTROL"></a><b>BridgeControl</b>

<dd>
<p>The contents of the control register of the bridge device.</p>
</dd>

### -field <a id="AsULONG"></a><a id="asulong"></a><a id="ASULONG"></a><b>AsULONG</b>

<dd>
<p>A ULONG representation of the contents of the WHEA_PCIEXPRESS_BRIDGE_CONTROL_STATUS union.</p>
</dd>
</dl>
<p>This member contains valid data only if the <b>ValidBits.BridgeControlStatus</b> bit is set.</p>
</dd>

### -field <b>ExpressCapability</b>

<dd>
<p>A buffer that contains a <a href="https://msdn.microsoft.com/library/windows/hardware/ff537460">PCI_EXPRESS_CAPABILITY</a> structure that describes the PCIe capability structure for the device where the error occurred.</p>
<p>This member contains valid data only if the <b>ValidBits.ExpressCapability</b> bit is set.</p>
</dd>

### -field <b>AerInfo</b>

<dd>
<p>A buffer that contains a <a href="https://msdn.microsoft.com/library/windows/hardware/ff537457">PCI_EXPRESS_AER_CAPABILITY</a> structure that describes the PCIe advanced error reporting (AER) extended capability structure for the device where the error occurred.</p>
<p>This member contains valid data only if the <b>ValidBits.AerInfo</b> bit is set.</p>
</dd>
</dl>

## -remarks
<p>The WHEA_PCIEXPRESS_ERROR_SECTION structure describes the error data that is contained in a PCI Express (PCIe) error section of an <a href="https://msdn.microsoft.com/080da29a-b5cb-45a5-848d-048d9612ee2a">error record</a>. An error record contains a PCIe error section only if the <b>SectionType </b>member of one of the <a href="https://msdn.microsoft.com/library/windows/hardware/ff560496">WHEA_ERROR_RECORD_SECTION_DESCRIPTOR</a> structures that describe the error record sections for that error record contains PCIEXPRESS_ERROR_SECTION_GUID.</p>

## -requirements
<table>
<tr>
<th width="30%">
<p>Version</p>
</th>
<td width="70%">
<p>Supported in Windows Server 2008, Windows Vista SP1, and later versions of Windows.
</p>
</td>
</tr>
<tr>
<th width="30%">
<p>Header</p>
</th>
<td width="70%">
<dl>
<dt>Ntddk.h (include Ntddk.h)</dt>
</dl>
</td>
</tr>
</table>

## -see-also
<dl>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff537457">PCI_EXPRESS_AER_CAPABILITY</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff537460">PCI_EXPRESS_CAPABILITY</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff560465">WHEA_ERROR_PACKET</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff560496">WHEA_ERROR_RECORD_SECTION_DESCRIPTOR</a>
</dt>
<dt>
<a href="https://msdn.microsoft.com/library/windows/hardware/ff560580">WHEA_PCIEXPRESS_ERROR_SECTION_VALIDBITS</a>
</dt>
</dl>
<p> </p>
<p> </p>
<p><a href="mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback [whea\whea]:%20WHEA_PCIEXPRESS_ERROR_SECTION structure%20 RELEASE:%20(10/23/2017)&amp;body=%0A%0APRIVACY STATEMENT%0A%0AWe use your feedback to improve the documentation. We don't use your email address for any other purpose, and we'll remove your email address from our system after the issue that you're reporting is fixed. While we're working to fix this issue, we might send you an email message to ask for more info. Later, we might also send you an email message to let you know that we've addressed your feedback.%0A%0AFor more info about Microsoft's privacy policy, see http://privacy.microsoft.com/en-us/default.aspx." title="Send comments about this topic to Microsoft">Send comments about this topic to Microsoft</a></p>