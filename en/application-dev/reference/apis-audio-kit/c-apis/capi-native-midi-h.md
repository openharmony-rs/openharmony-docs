# native_midi.h

## Overview

Declares MIDI related interfaces.<br> MIDI is a technical standard that enables communication between electronic musical instruments, computers, and other devices. The interfaces in this file are used for MIDI device management, MIDI events sending and receiving, and device status monitoring.<br> A common case of using OHMIDI to connect with MIDI device works as follows:<br> <pre> OH_MIDIClient_Create(&client, callbacks, userData);<br> OH_MIDIClient_GetDeviceCount(client, &deviceCount); // The developer should allocate a buffer for 'deviceInfos' based on 'deviceCount'. OH_MIDIClient_GetDeviceInfos(client, deviceInfos, deviceCount, &actualDeviceCount);<br> // Iterate through 'deviceInfos' to get the 'midiDeviceId' and query its ports. OH_MIDIClient_GetPortCount(client, midiDeviceId, &portCount); // The developer should allocate a buffer for 'portInfos' based on 'portCount'. OH_MIDIClient_GetPortInfos(client, midiDeviceId, portInfos, portCount, &actualPortCount);<br> OH_MIDIClient_OpenDevice(client, midiDeviceId, &device); // Or use OH_MIDIClient_OpenBLEDevice to open a BLE device, // waiting for the OH_MIDIClient_OnDeviceOpened callback.<br> // Get the port descriptor from the 'portInfos' array to open the ports. OH_MIDIDevice_OpenInputPort(device, inputportDesc, onMidiReceivedCallback, userData); // The 'onMidiReceivedCallback' is triggered upon receiving MIDI messages.<br> OH_MIDIDevice_OpenOutputPort(device, outputportDesc); OH_MIDIDevice_Send(device, outputportIndex, events, eventCount, &writtenEventCount);<br> ...<br> OH_MIDIClient_CloseDevice(client, device); // Use OH_MIDIDevice_CloseInputPort and OH_MIDIDevice_CloseOutputPort to close specific ports. OH_MIDIClient_Destroy(client); </pre>

**Library**: libohmidi.so

**System capability**: SystemCapability.Multimedia.Audio.MIDI

**Since**: 24

**Related module**: [OHMIDI](capi-ohmidi.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [OH_MIDIStatusCode OH_MIDIClient_Create(OH_MIDIClient **client, OH_MIDICallbacks callbacks, void *userData)](#oh_midiclient_create) | Creates a MIDI client instance. |
| [OH_MIDIStatusCode OH_MIDIClient_Destroy(OH_MIDIClient *client)](#oh_midiclient_destroy) | Destroys the MIDI client and releases resources. |
| [OH_MIDIStatusCode OH_MIDIClient_GetDeviceCount(const OH_MIDIClient *client, size_t *count)](#oh_midiclient_getdevicecount) | Gets the number of connected MIDI devices.<br> This function is used to determine the size of the array needed to get devices information. |
| [OH_MIDIStatusCode OH_MIDIClient_GetDeviceInfos(const OH_MIDIClient *client, OH_MIDIDeviceInformation *infos, size_t capacity, size_t *actualDeviceCount)](#oh_midiclient_getdeviceinfos) | Gets the information of connected MIDI devices.<br> Fills the user-allocated array with devices information. |
| [OH_MIDIStatusCode OH_MIDIClient_OpenDevice(OH_MIDIClient *client, int64_t deviceId, OH_MIDIDevice **device)](#oh_midiclient_opendevice) | Opens a MIDI device. |
| [OH_MIDIStatusCode OH_MIDIClient_OpenBLEDevice(OH_MIDIClient *client, const char *deviceAddr, OH_MIDIClient_OnDeviceOpened callback, void *userData)](#oh_midiclient_openbledevice) | Opens MIDI BLE device asynchronously.<br> Initiates the opening of a Bluetooth LE MIDI device. This function returns immediately, and the result is delivered via the provided callback. |
| [OH_MIDIStatusCode OH_MIDIClient_CloseDevice(OH_MIDIClient *client, OH_MIDIDevice *device)](#oh_midiclient_closedevice) | Closes the MIDI device. |
| [OH_MIDIStatusCode OH_MIDIClient_GetPortCount(const OH_MIDIClient *client, int64_t deviceId, size_t *count)](#oh_midiclient_getportcount) | Gets the number of ports for a specific MIDI device.<br> This function is used to determine the size of the array needed to get ports information. |
| [OH_MIDIStatusCode OH_MIDIClient_GetPortInfos(const OH_MIDIClient *client, int64_t deviceId, OH_MIDIPortInformation *infos, size_t capacity, size_t *actualPortCount)](#oh_midiclient_getportinfos) | Get the port information of a specific MIDI device.<br> Fills the user-allocated buffer with port information. |
| [OH_MIDIStatusCode OH_MIDIDevice_OpenInputPort(OH_MIDIDevice *device, OH_MIDIPortDescriptor descriptor, OH_MIDIDevice_OnReceived callback, void *userData)](#oh_mididevice_openinputport) | Opens a MIDI input port (Receive data).<br> Registers a callback to receive MIDI data in batches. |
| [OH_MIDIStatusCode OH_MIDIDevice_OpenOutputPort(OH_MIDIDevice *device, OH_MIDIPortDescriptor descriptor)](#oh_mididevice_openoutputport) | Opens a MIDI output port (Send data). |
| [OH_MIDIStatusCode OH_MIDIDevice_CloseInputPort(OH_MIDIDevice *device, uint32_t portIndex)](#oh_mididevice_closeinputport) | Closes the MIDI input port. |
| [OH_MIDIStatusCode OH_MIDIDevice_CloseOutputPort(OH_MIDIDevice *device, uint32_t portIndex)](#oh_mididevice_closeoutputport) | Closes the MIDI output port. |
| [OH_MIDIStatusCode OH_MIDIDevice_Send(OH_MIDIDevice *device, uint32_t portIndex, const OH_MIDIEvent *events, uint32_t eventCount, uint32_t *eventsWritten)](#oh_mididevice_send) | Sends MIDI events (Batch, Non-blocking & Atomic).<br> Attempts to write an array of events to the shared memory buffer.<br> - Atomicity: Each event in the array is treated atomically. It is either fully written or not written at all. - Partial Success: If the buffer becomes full midway, the function returns [OH_MIDI_STATUS_WOULD_BLOCK](capi-native-midi-base-h.md#oh_midistatuscode) and sets eventsWritten to the number of events successfully enqueued. |
| [OH_MIDIStatusCode OH_MIDIDevice_SendSysEx(OH_MIDIDevice *device, uint32_t portIndex, const uint8_t *data, uint32_t byteSize)](#oh_mididevice_sendsysex) | Sends a large SysEx message (Byte-Stream to UMP Helper).<br> This is a utility function for applications that handle SysEx as raw byte streams(MIDI 1.0 style, F0...F7). This works for both OH_MIDI_PROTOCOL_1_0 and OH_MIDI_PROTOCOL_2_0 sessions. The underlying service handles the final conversion based on the device's actual capabilities.<br> How it works: 1. It automatically fragments the raw bytes into a sequence of UMP Type 3(64-bit Data Message) packets. 2. It sends these packets sequentially using OH_MIDIDevice_Send. |
| [OH_MIDIStatusCode OH_MIDIDevice_FlushOutputPort(OH_MIDIDevice *device, uint32_t portIndex)](#oh_mididevice_flushoutputport) | Flushes pending events in output buffer.<br> Immediately discards all MIDI events currently waiting in the output buffer for the specified port. This includes events scheduled for future timestamps that haven't been processed by the service yet. |

## Function description

### OH_MIDIClient_Create()

```c
OH_MIDIStatusCode OH_MIDIClient_Create(OH_MIDIClient **client, OH_MIDICallbacks callbacks, void *userData)
```

**Description**

Creates a MIDI client instance.

> **Note**:
>
> Resource Management & Best Practices**: MIDI is a delay-sensitive system service. To ensure real-time performance (QoS) and system stability, the service enforces the following limits: 1. **System-wide limit**: A global maximum number of active MIDI clients that are allowed. 2. **Per-Application limit**: A maximum number of MIDI clients that are allowed per app uid. Applications are **strongly recommended** to maintain a single `OH_MIDIClient` instance throughout their lifecycle and use it to manage multiple devices/ports. Use [OH_MIDIClient_Destroy](capi-native-midi-h.md#oh_midiclient_destroy) to release the client and all associated resources.

**System capability**: SystemCapability.Multimedia.Audio.MIDI

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_MIDIClient **client | Pointer to receive the new client handle. |
| OH_MIDICallbacks callbacks | Callback structure for system events. |
| void *userData | User context to be passed to callbacks. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_MIDIStatusCode | [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode) if execution succeeds,      or [OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT](capi-native-midi-base-h.md#oh_midistatuscode) if client is null.      or [OH_MIDI_STATUS_GENERIC_IPC_FAILURE](capi-native-midi-base-h.md#oh_midistatuscode) if connection to system service fails.      or [OH_MIDI_STATUS_TOO_MANY_CLIENTS](capi-native-midi-base-h.md#oh_midistatuscode) if creation failed due to resource limits.          This occurs if the calling application exceeded its per-uid quota or the system is busy. |

### OH_MIDIClient_Destroy()

```c
OH_MIDIStatusCode OH_MIDIClient_Destroy(OH_MIDIClient *client)
```

**Description**

Destroys the MIDI client and releases resources.

> **Note**:
>
> Destroying the client will close all devices and ports (fail-safe mechanism) automatically. It is recommended to close resources in reverse order (ports->devices->client) for code clarity, but this is not a mandatory requirement.

**System capability**: SystemCapability.Multimedia.Audio.MIDI

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_MIDIClient *client | The MIDI client handle, generated by [OH_MIDIClient_Create](capi-native-midi-h.md#oh_midiclient_create). |

**Returns**:

| Type | Description |
| -- | -- |
| OH_MIDIStatusCode | [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode) if execution succeeds.      or [OH_MIDI_STATUS_INVALID_CLIENT](capi-native-midi-base-h.md#oh_midistatuscode) if client is null or invalid.      or [OH_MIDI_STATUS_GENERIC_IPC_FAILURE](capi-native-midi-base-h.md#oh_midistatuscode) if connection to system service fails. |

### OH_MIDIClient_GetDeviceCount()

```c
OH_MIDIStatusCode OH_MIDIClient_GetDeviceCount(const OH_MIDIClient *client, size_t *count)
```

**Description**

Gets the number of connected MIDI devices.<br> This function is used to determine the size of the array needed to get devices information.

**System capability**: SystemCapability.Multimedia.Audio.MIDI

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_MIDIClient *client | The MIDI client handle, generated by [OH_MIDIClient_Create](capi-native-midi-h.md#oh_midiclient_create). |
| size_t *count | Pointer to receive the number of devices. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_MIDIStatusCode | [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode) on success.      or [OH_MIDI_STATUS_INVALID_CLIENT](capi-native-midi-base-h.md#oh_midistatuscode) if client is invalid.      or [OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT](capi-native-midi-base-h.md#oh_midistatuscode) if count is null.      or [OH_MIDI_STATUS_GENERIC_IPC_FAILURE](capi-native-midi-base-h.md#oh_midistatuscode) if connection to system service fails. |

### OH_MIDIClient_GetDeviceInfos()

```c
OH_MIDIStatusCode OH_MIDIClient_GetDeviceInfos(const OH_MIDIClient *client, OH_MIDIDeviceInformation *infos, size_t capacity, size_t *actualDeviceCount)
```

**Description**

Gets the information of connected MIDI devices.<br> Fills the user-allocated array with devices information.

> **Note**:
>
> The actual number of connected devices may be larger than the capacity of the input parameter 'infos' array. If this happens, the output 'infos' array will only contain partial devices information, the output 'actualDeviceCount' will be equal to 'capacity', and the function returns [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode). If the actual number is less than or equal to 'capacity', all available devices information will be filled into 'infos', and the output 'actualDeviceCount' reflects the actual devices number.

**System capability**: SystemCapability.Multimedia.Audio.MIDI

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_MIDIClient *client | The MIDI client handle, generated by [OH_MIDIClient_Create](capi-native-midi-h.md#oh_midiclient_create). |
| OH_MIDIDeviceInformation *infos | A user-allocated array to get devices information. |
| size_t capacity | The allocated size of 'infos' array. |
| size_t *actualDeviceCount | Pointer to receive the actual number of devices filled into the 'infos' array. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_MIDIStatusCode | [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode) on success.      or [OH_MIDI_STATUS_INVALID_CLIENT](capi-native-midi-base-h.md#oh_midistatuscode) if client is invalid.      or [OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT](capi-native-midi-base-h.md#oh_midistatuscode) if infos or actualDeviceCount is null.      or [OH_MIDI_STATUS_GENERIC_IPC_FAILURE](capi-native-midi-base-h.md#oh_midistatuscode) if connection to system service fails. |

### OH_MIDIClient_OpenDevice()

```c
OH_MIDIStatusCode OH_MIDIClient_OpenDevice(OH_MIDIClient *client, int64_t deviceId, OH_MIDIDevice **device)
```

**Description**

Opens a MIDI device.

> **Note**:
>
> Use [OH_MIDIClient_CloseDevice](capi-native-midi-h.md#oh_midiclient_closedevice) to release the device resource.

**System capability**: SystemCapability.Multimedia.Audio.MIDI

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_MIDIClient *client | The MIDI client handle, generated by [OH_MIDIClient_Create](capi-native-midi-h.md#oh_midiclient_create). |
| int64_t deviceId | Device ID. |
| OH_MIDIDevice **device | Pointer to receive the device handle, allocated by the system. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_MIDIStatusCode | [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode) if execution succeeds.      or [OH_MIDI_STATUS_INVALID_CLIENT](capi-native-midi-base-h.md#oh_midistatuscode) if client is invalid.      or [OH_MIDI_STATUS_DEVICE_ALREADY_OPEN](capi-native-midi-base-h.md#oh_midistatuscode) if device is already opened by this client.      or [OH_MIDI_STATUS_TOO_MANY_OPEN_DEVICES](capi-native-midi-base-h.md#oh_midistatuscode) if the client has reached the maximum number of open devices.      or [OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT](capi-native-midi-base-h.md#oh_midistatuscode) if device is null or the deviceId does not exist.      or [OH_MIDI_STATUS_GENERIC_IPC_FAILURE](capi-native-midi-base-h.md#oh_midistatuscode) if connection to system service fails. |

### OH_MIDIClient_OpenBLEDevice()

```c
OH_MIDIStatusCode OH_MIDIClient_OpenBLEDevice(OH_MIDIClient *client, const char *deviceAddr, OH_MIDIClient_OnDeviceOpened callback, void *userData)
```

**Description**

Opens MIDI BLE device asynchronously.<br> Initiates the opening of a Bluetooth LE MIDI device. This function returns immediately, and the result is delivered via the provided callback.

> **Note**:
>
> This function triggers a BLE scan so the opening process may take time. Use [OH_MIDIClient_CloseDevice](capi-native-midi-h.md#oh_midiclient_closedevice) to release the device resource.

**System capability**: SystemCapability.Multimedia.Audio.MIDI

**Required permission**: ohos.permission.ACCESS_BLUETOOTH

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_MIDIClient *client | The MIDI client handle, generated by [OH_MIDIClient_Create](capi-native-midi-h.md#oh_midiclient_create). |
| const char *deviceAddr | The MAC address of the BLE device (e.g., "AA:BB:CC:DD:EE:FF"). |
| OH_MIDIClient_OnDeviceOpened callback | The callback function to be invoked when the open process completes. |
| void *userData | User context pointer to be passed to the callback. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_MIDIStatusCode | [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode) if the open request was successfully dispatched.      or [OH_MIDI_STATUS_INVALID_CLIENT](capi-native-midi-base-h.md#oh_midistatuscode) if client is invalid.      or [OH_MIDI_STATUS_DEVICE_ALREADY_OPEN](capi-native-midi-base-h.md#oh_midistatuscode) if device is already opened by this client.      or [OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT](capi-native-midi-base-h.md#oh_midistatuscode) if deviceAddr or callback is null.      or [OH_MIDI_STATUS_PERMISSION_DENIED](capi-native-midi-base-h.md#oh_midistatuscode) if Bluetooth permission is missing.      or [OH_MIDI_STATUS_TOO_MANY_OPEN_DEVICES](capi-native-midi-base-h.md#oh_midistatuscode) if the client has reached the maximum number of open devices.      or [OH_MIDI_STATUS_GENERIC_IPC_FAILURE](capi-native-midi-base-h.md#oh_midistatuscode) if the service is unreachable. |

### OH_MIDIClient_CloseDevice()

```c
OH_MIDIStatusCode OH_MIDIClient_CloseDevice(OH_MIDIClient *client, OH_MIDIDevice *device)
```

**Description**

Closes the MIDI device.

> **Note**:
>
> Closing a device automatically closes all opened ports on that device. Paired with [OH_MIDIClient_OpenDevice](capi-native-midi-h.md#oh_midiclient_opendevice) or [OH_MIDIClient_OpenBLEDevice](capi-native-midi-h.md#oh_midiclient_openbledevice).

**System capability**: SystemCapability.Multimedia.Audio.MIDI

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_MIDIClient *client | The MIDI client handle, generated by [OH_MIDIClient_Create](capi-native-midi-h.md#oh_midiclient_create). |
| OH_MIDIDevice *device | Target device handle, generated by [OH_MIDIClient_OpenDevice](capi-native-midi-h.md#oh_midiclient_opendevice) or [OH_MIDIClient_OpenBLEDevice](capi-native-midi-h.md#oh_midiclient_openbledevice). |

**Returns**:

| Type | Description |
| -- | -- |
| OH_MIDIStatusCode | [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode) if execution succeeds.      or [OH_MIDI_STATUS_INVALID_CLIENT](capi-native-midi-base-h.md#oh_midistatuscode) if client is invalid.      or [OH_MIDI_STATUS_INVALID_DEVICE_HANDLE](capi-native-midi-base-h.md#oh_midistatuscode) if device is invalid. |

### OH_MIDIClient_GetPortCount()

```c
OH_MIDIStatusCode OH_MIDIClient_GetPortCount(const OH_MIDIClient *client, int64_t deviceId, size_t *count)
```

**Description**

Gets the number of ports for a specific MIDI device.<br> This function is used to determine the size of the array needed to get ports information.

**System capability**: SystemCapability.Multimedia.Audio.MIDI

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_MIDIClient *client | The MIDI client handle, generated by [OH_MIDIClient_Create](capi-native-midi-h.md#oh_midiclient_create). |
| int64_t deviceId | The target device ID. |
| size_t *count | Pointer to receive the number of ports. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_MIDIStatusCode | [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode) on success.      or [OH_MIDI_STATUS_INVALID_CLIENT](capi-native-midi-base-h.md#oh_midistatuscode) if client is invalid.      or [OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT](capi-native-midi-base-h.md#oh_midistatuscode) if count is null.      or [OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT](capi-native-midi-base-h.md#oh_midistatuscode) if deviceId is invalid.      or [OH_MIDI_STATUS_GENERIC_IPC_FAILURE](capi-native-midi-base-h.md#oh_midistatuscode) if connection to system service fails. |

### OH_MIDIClient_GetPortInfos()

```c
OH_MIDIStatusCode OH_MIDIClient_GetPortInfos(const OH_MIDIClient *client, int64_t deviceId, OH_MIDIPortInformation *infos, size_t capacity, size_t *actualPortCount)
```

**Description**

Get the port information of a specific MIDI device.<br> Fills the user-allocated buffer with port information.

> **Note**:
>
> The actual number of connected devices may be larger than the capacity of the input parameter 'infos' array. If this happens, the output 'infos' array will only contain partial devices information, the output 'actualPortCount' will be equal to 'capacity', and the function returns [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode). If the actual number is less than or equal to 'capacity', all available ports information will be filled into 'infos', and the output 'actualPortCount' reflects the actual ports number.

**System capability**: SystemCapability.Multimedia.Audio.MIDI

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_MIDIClient *client | The MIDI client handle, generated by [OH_MIDIClient_Create](capi-native-midi-h.md#oh_midiclient_create). |
| int64_t deviceId | The target device ID. |
| OH_MIDIPortInformation *infos | A user-allocated array to get ports information. |
| size_t capacity | The allocated size of 'infos' array. |
| size_t *actualPortCount | Pointer to receive the actual number of ports filled into the 'infos' array. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_MIDIStatusCode | [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode) on success.      or [OH_MIDI_STATUS_INVALID_CLIENT](capi-native-midi-base-h.md#oh_midistatuscode) if client is invalid.      or [OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT](capi-native-midi-base-h.md#oh_midistatuscode) if infos or actualPortCount is null.      or [OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT](capi-native-midi-base-h.md#oh_midistatuscode) if deviceId is invalid.      or [OH_MIDI_STATUS_GENERIC_IPC_FAILURE](capi-native-midi-base-h.md#oh_midistatuscode) if connection to system service fails. |

### OH_MIDIDevice_OpenInputPort()

```c
OH_MIDIStatusCode OH_MIDIDevice_OpenInputPort(OH_MIDIDevice *device, OH_MIDIPortDescriptor descriptor, OH_MIDIDevice_OnReceived callback, void *userData)
```

**Description**

Opens a MIDI input port (Receive data).<br> Registers a callback to receive MIDI data in batches.

> **Note**:
>
> Use [OH_MIDIDevice_CloseInputPort](capi-native-midi-h.md#oh_mididevice_closeinputport) to close the input port.

**System capability**: SystemCapability.Multimedia.Audio.MIDI

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_MIDIDevice *device | Target device handle, generated by [OH_MIDIClient_OpenDevice](capi-native-midi-h.md#oh_midiclient_opendevice) or [OH_MIDIClient_OpenBLEDevice](capi-native-midi-h.md#oh_midiclient_openbledevice). |
| OH_MIDIPortDescriptor descriptor | Port index and protocol configuration. |
| OH_MIDIDevice_OnReceived callback | Callback function invoked when data is available. |
| void *userData | User context to be passed to callbacks. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_MIDIStatusCode | [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode) if execution succeeds.      or [OH_MIDI_STATUS_INVALID_DEVICE_HANDLE](capi-native-midi-base-h.md#oh_midistatuscode) if device is invalid.      or [OH_MIDI_STATUS_INVALID_PORT](capi-native-midi-base-h.md#oh_midistatuscode) if the port is invalid or not an input port.      or [OH_MIDI_STATUS_PORT_ALREADY_OPEN](capi-native-midi-base-h.md#oh_midistatuscode) if the port is already opened by this client.      or [OH_MIDI_STATUS_TOO_MANY_OPEN_PORTS](capi-native-midi-base-h.md#oh_midistatuscode) if the maximum number of open ports has been reached.      or [OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT](capi-native-midi-base-h.md#oh_midistatuscode) if callback is null.      or [OH_MIDI_STATUS_GENERIC_IPC_FAILURE](capi-native-midi-base-h.md#oh_midistatuscode) if connection to system service fails. |

### OH_MIDIDevice_OpenOutputPort()

```c
OH_MIDIStatusCode OH_MIDIDevice_OpenOutputPort(OH_MIDIDevice *device, OH_MIDIPortDescriptor descriptor)
```

**Description**

Opens a MIDI output port (Send data).

> **Note**:
>
> Use [OH_MIDIDevice_CloseOutputPort](capi-native-midi-h.md#oh_mididevice_closeoutputport) to close the output port.

**System capability**: SystemCapability.Multimedia.Audio.MIDI

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_MIDIDevice *device | Target device handle, generated by [OH_MIDIClient_OpenDevice](capi-native-midi-h.md#oh_midiclient_opendevice) or [OH_MIDIClient_OpenBLEDevice](capi-native-midi-h.md#oh_midiclient_openbledevice). |
| OH_MIDIPortDescriptor descriptor | Port index and protocol configuration. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_MIDIStatusCode | [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode) if execution succeeds.      or [OH_MIDI_STATUS_INVALID_DEVICE_HANDLE](capi-native-midi-base-h.md#oh_midistatuscode) if device is invalid.      or [OH_MIDI_STATUS_INVALID_PORT](capi-native-midi-base-h.md#oh_midistatuscode) if the port is invalid or not an output port.      or [OH_MIDI_STATUS_PORT_ALREADY_OPEN](capi-native-midi-base-h.md#oh_midistatuscode) if the port is already opened by this client.      or [OH_MIDI_STATUS_TOO_MANY_OPEN_PORTS](capi-native-midi-base-h.md#oh_midistatuscode) if the maximum number of open ports has been reached.      or [OH_MIDI_STATUS_GENERIC_IPC_FAILURE](capi-native-midi-base-h.md#oh_midistatuscode) if connection to system service fails. |

### OH_MIDIDevice_CloseInputPort()

```c
OH_MIDIStatusCode OH_MIDIDevice_CloseInputPort(OH_MIDIDevice *device, uint32_t portIndex)
```

**Description**

Closes the MIDI input port.

> **Note**:
>
> Paired with [OH_MIDIDevice_OpenInputPort](capi-native-midi-h.md#oh_mididevice_openinputport).

**System capability**: SystemCapability.Multimedia.Audio.MIDI

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_MIDIDevice *device | Target device handle, generated by [OH_MIDIClient_OpenDevice](capi-native-midi-h.md#oh_midiclient_opendevice) or [OH_MIDIClient_OpenBLEDevice](capi-native-midi-h.md#oh_midiclient_openbledevice). |
| uint32_t portIndex | Input port index to close. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_MIDIStatusCode | [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode) if execution succeeds.      or [OH_MIDI_STATUS_INVALID_DEVICE_HANDLE](capi-native-midi-base-h.md#oh_midistatuscode) if device is invalid.      or [OH_MIDI_STATUS_INVALID_PORT](capi-native-midi-base-h.md#oh_midistatuscode) if portIndex is invalid or not an open input port.      or [OH_MIDI_STATUS_GENERIC_IPC_FAILURE](capi-native-midi-base-h.md#oh_midistatuscode) if connection to system service fails. |

### OH_MIDIDevice_CloseOutputPort()

```c
OH_MIDIStatusCode OH_MIDIDevice_CloseOutputPort(OH_MIDIDevice *device, uint32_t portIndex)
```

**Description**

Closes the MIDI output port.

> **Note**:
>
> Paired with [OH_MIDIDevice_OpenOutputPort](capi-native-midi-h.md#oh_mididevice_openoutputport).

**System capability**: SystemCapability.Multimedia.Audio.MIDI

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_MIDIDevice *device | Target device handle, generated by [OH_MIDIClient_OpenDevice](capi-native-midi-h.md#oh_midiclient_opendevice) or [OH_MIDIClient_OpenBLEDevice](capi-native-midi-h.md#oh_midiclient_openbledevice). |
| uint32_t portIndex | Output port index to close. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_MIDIStatusCode | [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode) if execution succeeds.      or [OH_MIDI_STATUS_INVALID_DEVICE_HANDLE](capi-native-midi-base-h.md#oh_midistatuscode) if device is invalid.      or [OH_MIDI_STATUS_INVALID_PORT](capi-native-midi-base-h.md#oh_midistatuscode) if portIndex is invalid or not an open output port.      or [OH_MIDI_STATUS_GENERIC_IPC_FAILURE](capi-native-midi-base-h.md#oh_midistatuscode) if connection to system service fails. |

### OH_MIDIDevice_Send()

```c
OH_MIDIStatusCode OH_MIDIDevice_Send(OH_MIDIDevice *device, uint32_t portIndex, const OH_MIDIEvent *events, uint32_t eventCount, uint32_t *eventsWritten)
```

**Description**

Sends MIDI events (Batch, Non-blocking & Atomic).<br> Attempts to write an array of events to the shared memory buffer.<br> - Atomicity: Each event in the array is treated atomically. It is either fully written or not written at all. - Partial Success: If the buffer becomes full midway, the function returns [OH_MIDI_STATUS_WOULD_BLOCK](capi-native-midi-base-h.md#oh_midistatuscode) and sets eventsWritten to the number of events successfully enqueued.

**System capability**: SystemCapability.Multimedia.Audio.MIDI

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_MIDIDevice *device | Target device handle, generated by [OH_MIDIClient_OpenDevice](capi-native-midi-h.md#oh_midiclient_opendevice) or [OH_MIDIClient_OpenBLEDevice](capi-native-midi-h.md#oh_midiclient_openbledevice). |
| uint32_t portIndex | Target port index. |
| const OH_MIDIEvent *events | Pointer to the array of events to send, the memory space needs to be allocated by developer. |
| uint32_t eventCount | Number of events in the array. |
| uint32_t *eventsWritten | Returns the number of events successfully consumed. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_MIDIStatusCode | [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode) if all events were written.      or [OH_MIDI_STATUS_INVALID_DEVICE_HANDLE](capi-native-midi-base-h.md#oh_midistatuscode) if device is invalid.      or [OH_MIDI_STATUS_INVALID_PORT](capi-native-midi-base-h.md#oh_midistatuscode) if portIndex is invalid, or not open.      or [OH_MIDI_STATUS_WOULD_BLOCK](capi-native-midi-base-h.md#oh_midistatuscode) if buffer is full (check eventsWritten).      or [OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT](capi-native-midi-base-h.md#oh_midistatuscode) if arguments are invalid.      or [OH_MIDI_STATUS_GENERIC_IPC_FAILURE](capi-native-midi-base-h.md#oh_midistatuscode) if connection to system service fails. |

### OH_MIDIDevice_SendSysEx()

```c
OH_MIDIStatusCode OH_MIDIDevice_SendSysEx(OH_MIDIDevice *device, uint32_t portIndex, const uint8_t *data, uint32_t byteSize)
```

**Description**

Sends a large SysEx message (Byte-Stream to UMP Helper).<br> This is a utility function for applications that handle SysEx as raw byte streams(MIDI 1.0 style, F0...F7). This works for both OH_MIDI_PROTOCOL_1_0 and OH_MIDI_PROTOCOL_2_0 sessions. The underlying service handles the final conversion based on the device's actual capabilities.<br> How it works: 1. It automatically fragments the raw bytes into a sequence of UMP Type 3(64-bit Data Message) packets. 2. It sends these packets sequentially using OH_MIDIDevice_Send.

> **Warning**:
>
> BLOCKING CALL**: This function executes a loop and may block if the buffer fills up.

**System capability**: SystemCapability.Multimedia.Audio.MIDI

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_MIDIDevice *device | Target device handle, generated by [OH_MIDIClient_OpenDevice](capi-native-midi-h.md#oh_midiclient_opendevice) or [OH_MIDIClient_OpenBLEDevice](capi-native-midi-h.md#oh_midiclient_openbledevice). |
| uint32_t portIndex | Target port index. |
| const uint8_t *data | Pointer to the byte stream to send, the memory space needs to be allocated by developer. |
| uint32_t byteSize | Byte size of data. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_MIDIStatusCode | [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode) if all events were written.      or [OH_MIDI_STATUS_INVALID_DEVICE_HANDLE](capi-native-midi-base-h.md#oh_midistatuscode) if device is invalid.      or [OH_MIDI_STATUS_INVALID_PORT](capi-native-midi-base-h.md#oh_midistatuscode) if portIndex is invalid, or not open.      or [OH_MIDI_STATUS_TIMEOUT](capi-native-midi-base-h.md#oh_midistatuscode) if the operation could not be completed within a reasonable time,                                      application may use OH_MIDIDevice_FlushOutputPort to reset.      or [OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT](capi-native-midi-base-h.md#oh_midistatuscode) if arguments are invalid. |

### OH_MIDIDevice_FlushOutputPort()

```c
OH_MIDIStatusCode OH_MIDIDevice_FlushOutputPort(OH_MIDIDevice *device, uint32_t portIndex)
```

**Description**

Flushes pending events in output buffer.<br> Immediately discards all MIDI events currently waiting in the output buffer for the specified port. This includes events scheduled for future timestamps that haven't been processed by the service yet.

> **Note**:
>
> This function does not send "All Notes Off" event. It simply clears the queue.

**System capability**: SystemCapability.Multimedia.Audio.MIDI

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_MIDIDevice *device | Target device handle, generated by [OH_MIDIClient_OpenDevice](capi-native-midi-h.md#oh_midiclient_opendevice) or [OH_MIDIClient_OpenBLEDevice](capi-native-midi-h.md#oh_midiclient_openbledevice). |
| uint32_t portIndex | Target port index. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_MIDIStatusCode | [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode) if execution succeeds,      or [OH_MIDI_STATUS_INVALID_DEVICE_HANDLE](capi-native-midi-base-h.md#oh_midistatuscode) if device is invalid.      or [OH_MIDI_STATUS_INVALID_PORT](capi-native-midi-base-h.md#oh_midistatuscode) if portIndex is invalid or not an output port.      or [OH_MIDI_STATUS_GENERIC_IPC_FAILURE](capi-native-midi-base-h.md#oh_midistatuscode) if connection to system service fails. |


