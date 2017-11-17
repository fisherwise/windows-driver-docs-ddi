# Declarations in the hdaudio header
This header Hdaudio contains these programming interfaces:

Callback

| Title        | Description    |
| ------------- |:-------------:|
| [PREGISTER_NOTIFICATION_EVENT callback](nc-hdaudio-pregister-notification-event.md) | The RegisterNotificationEvent routine registers a kernel event so that it can receive DMA progress notifications.The function pointer type for a RegisterNotificationEvent routine is defined as follows. |
| [PGET_WALL_CLOCK_REGISTER callback](nc-hdaudio-pget-wall-clock-register.md) | The GetWallClockRegister routine retrieves a pointer to the wall clock register.The function pointer type for a GetWallClockRegister routine is defined as |
| [PGET_RESOURCE_INFORMATION callback](nc-hdaudio-pget-resource-information.md) | The GetResourceInformation routine retrieves information about hardware resources.The function pointer type for a GetResourceInformation routine is defined as |
| [PREGISTER_EVENT_CALLBACK callback](nc-hdaudio-pregister-event-callback.md) | The RegisterEventCallback routine registers a callback routine for an unsolicited response from a codec or codecs.The function pointer type for a RegisterEventCallback routine is defined as |
| [PALLOCATE_DMA_BUFFER callback](nc-hdaudio-pallocate-dma-buffer.md) | The AllocateDmaBuffer routine allocates a data buffer in system memory for a DMA engine.The function pointer type for an AllocateDmaBuffer routine is defined as |
| [PCHANGE_BANDWIDTH_ALLOCATION callback](nc-hdaudio-pchange-bandwidth-allocation.md) | The ChangeBandwidthAllocation routine changes a DMA engine's bandwidth allocation on the HD Audio Link.The function pointer type for a ChangeBandwidthAllocation routine is defined as |
| [PUNREGISTER_EVENT_CALLBACK callback](nc-hdaudio-punregister-event-callback.md) | The UnregisterEventCallback routine deletes the registration of an event callback that was previously registered by a call to RegisterEventCallback.The function pointer type for an UnregisterEventCallback routine is defined as |
| [PSET_DMA_ENGINE_STATE callback](nc-hdaudio-pset-dma-engine-state.md) | The SetDmaEngineState routine sets the state of one or more DMA engines to the Running, Stopped, Paused, or Reset state.The function pointer type for a SetDmaEngineState routine is defined as |
| [PTRANSFER_CODEC_VERBS callback](nc-hdaudio-ptransfer-codec-verbs.md) | The TransferCodecVerbs routine transfers one or more commands to a codec or codecs and retrieves the responses to those commands.The function pointer type for a TransferCodecVerbs routine is defined as |
| [PALLOCATE_RENDER_DMA_ENGINE callback](nc-hdaudio-pallocate-render-dma-engine.md) | The AllocateRenderDmaEngine routine allocates a DMA engine for a render stream.The function pointer type for an AllocateRenderDmaEngine routine is defined as |
| [PGET_DEVICE_INFORMATION callback](nc-hdaudio-pget-device-information.md) | The GetDeviceInformation routine retrieves information about the HD Audio controller device.The function pointer type for a GetDeviceInformation routine is defined as |
| [PFREE_DMA_BUFFER_WITH_NOTIFICATION callback](nc-hdaudio-pfree-dma-buffer-with-notification.md) | The FreeDmaBufferWithNotification routine frees a DMA buffer that was previously allocated by a call to AllocateDmaBufferWithNotification.The function pointer type for a FreeDmaBufferWithNotification routine is defined as follows. |
| [PHDAUDIO_TRANSFER_COMPLETE_CALLBACK callback](nc-hdaudio-phdaudio-transfer-complete-callback.md) | HDAudio codec transfer complete callback function. PHDAUDIO_TRANSFER_COMPLETE_CALLBACK is used by the PTRANSFER_CODEC_VERBS callback function. |
| [PSETUP_DMA_ENGINE_WITH_BDL callback](nc-hdaudio-psetup-dma-engine-with-bdl.md) | The SetupDmaEngineWithBdl routine sets up a DMA engine to use a caller-allocated DMA buffer.The function pointer type for a SetupDmaEngineWithBdl routine is defined as |
| [PALLOCATE_CAPTURE_DMA_ENGINE callback](nc-hdaudio-pallocate-capture-dma-engine.md) | The AllocateCaptureDmaEngine routine allocates a DMA engine for a capture stream.The function pointer type for an AllocateCaptureDmaEngine routine is defined as |
| [PHDAUDIO_BDL_ISR callback](nc-hdaudio-phdaudio-bdl-isr.md) | The HDAudioBdlIsr routine is the ISR that the HD Audio bus driver calls each time an IOC interrupt occurs on the stream. It is a function pointer of type PHDAUDIO_BDL_ISR, which is defined as |
| [PALLOCATE_DMA_BUFFER_WITH_NOTIFICATION callback](nc-hdaudio-pallocate-dma-buffer-with-notification.md) | The AllocateDmaBufferWithNotification routine allocates a data buffer in system memory for a DMA engine.The function pointer type for an AllocateDmaBufferWithNotification routine is defined as follows. |
| [PFREE_CONTIGUOUS_DMA_BUFFER callback](nc-hdaudio-pfree-contiguous-dma-buffer.md) | The FreeContiguousDmaBuffer routine frees a DMA buffer and buffer descriptor list (BDL) that were allocated by a call to AllocateContiguousDmaBuffer.The function pointer type for a FreeContiguousDmaBuffer routine is defined as |
| [PHDAUDIO_UNSOLICITED_RESPONSE_CALLBACK callback](nc-hdaudio-phdaudio-unsolicited-response-callback.md) | HDAudio codec unsolicited response callback function. PHDAUDIO_UNSOLICITED_RESPONSE_CALLBACK is used by the PREGISTER_EVENT_CALLBACK callback function. |
| [PALLOCATE_CONTIGUOUS_DMA_BUFFER callback](nc-hdaudio-pallocate-contiguous-dma-buffer.md) | The AllocateContiguousDmaBuffer routine allocates a DMA buffer that consists of a single, contiguous block of physical memory.The function pointer type for an AllocateContiguousDmaBuffer routine is defined as |
| [PFREE_DMA_BUFFER callback](nc-hdaudio-pfree-dma-buffer.md) | The FreeDmaBuffer routine frees a DMA buffer that was previously allocated by a call to AllocateDmaBuffer.The function pointer type for a FreeDmaBuffer routine is defined as |
| [PUNREGISTER_NOTIFICATION_EVENT callback](nc-hdaudio-punregister-notification-event.md) | The UnregisterNotificationEvent routine deletes the registration of an event that was previously registered by a call to RegisterNotificationEvent.The function pointer type for an UnregisterNotificationEvent routine is defined as follows. |
| [PGET_LINK_POSITION_REGISTER callback](nc-hdaudio-pget-link-position-register.md) | The GetLinkPositionRegister routine retrieves a pointer to a DMA engine's link position register.The function pointer type for a GetLinkPositionRegister routine is defined as |
| [PFREE_DMA_ENGINE callback](nc-hdaudio-pfree-dma-engine.md) | The FreeDmaEngine routine frees a DMA engine that was previously allocated by a call to AllocateCaptureDmaEngine or AllocateRenderDmaEngine.The function pointer type for a FreeDmaEngine routine is defined as |
Struct

| Title        | Description    |
| ------------- |:-------------:|
| [HDAUDIO_CONVERTER_FORMAT structure](ns-hdaudio--hdaudio-converter-format.md) | The HDAUDIO_CONVERTER_FORMAT structure specifies the 16-bit encoded stream format for an input or output converter, as defined in the Intel High Definition Audio Specification (see the Intel HD Audio website). |
| [HDAUDIO_CODEC_COMMAND structure](ns-hdaudio--hdaudio-codec-command.md) | The HDAUDIO_CODEC_COMMAND structure specifies a codec command. |
| [HDAUDIO_BUFFER_DESCRIPTOR structure](ns-hdaudio--hdaudio-buffer-descriptor.md) | The HDAUDIO_BUFFER_DESCRIPTOR structure specifies a buffer descriptor, which is an entry in a buffer descriptor list (BDL). |
| [HDAUDIO_CODEC_RESPONSE structure](ns-hdaudio--hdaudio-codec-response.md) | The HDAUDIO_CODEC_RESPONSE structure specifies either a response to a codec command or an unsolicited response from a codec. |
| [HDAUDIO_BUS_INTERFACE_V2 structure](ns-hdaudio--hdaudio-bus-interface-v2.md) | The HDAUDIO_BUS_INTERFACE_V2 structure specifies the information that a client requires to call the routines in the HDAUDIO_BUS_INTERFACE_V2 version of the HD Audio DDI. |
| [HDAUDIO_BUS_INTERFACE_BDL structure](ns-hdaudio--hdaudio-bus-interface-bdl.md) | The HDAUDIO_BUS_INTERFACE_BDL structure specifies the information that a client requires to call the routines in the HDAUDIO_BUS_INTERFACE_BDL version of the HD Audio DDI. Another variant of this DDI is specified by the HDAUDIO_BUS_INTERFACE structure. |
| [HDAUDIO_DEVICE_INFORMATION structure](ns-hdaudio--hdaudio-device-information.md) | The HDAUDIO_DEVICE_INFORMATION structure specifies the hardware capabilities of the HD Audio bus controller. |
| [HDAUDIO_CODEC_TRANSFER structure](ns-hdaudio--hdaudio-codec-transfer.md) | The HDAUDIO_CODEC_TRANSFER structure specifies a codec command and the response to that command. |
| [HDAUDIO_STREAM_FORMAT structure](ns-hdaudio--hdaudio-stream-format.md) | The HDAUDIO_STREAM_FORMAT structure describes the data format of a capture or render stream. |
| [HDAUDIO_BUS_INTERFACE structure](ns-hdaudio--hdaudio-bus-interface.md) | The HDAUDIO_BUS_INTERFACE structure specifies the information that a client requires to call the routines in the HDAUDIO_BUS_INTERFACE version of the HD Audio DDI. Another variant of this DDI is specified by the HDAUDIO_BUS_INTERFACE_BDL structure. |
Enum

| Title        | Description    |
| ------------- |:-------------:|
| [HDAUDIO_STREAM_STATE enumeration](ne-hdaudio--hdaudio-stream-state.md) | The HDAUDIO_STREAM_STATE enumeration defines constants that specify the different stream states supported by HDAudio. |
| [HDAUDIO_CODEC_POWER_STATE enumeration](ne-hdaudio--hdaudio-codec-power-state.md) | The HDAUDIO_CODEC_POWER_STATE enumeration defines constants that specify the different power states that HD Audio codecs can support. All states are from DEVICE_POWER_STATE except PowerCodecD3Cold. |

This header is used in these topics:

- [audio](..content/_audio)