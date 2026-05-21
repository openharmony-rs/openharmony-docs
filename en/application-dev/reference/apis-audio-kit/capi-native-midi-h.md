# native_midi.h
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @owen_creeper-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

## Overview

This file declares MIDI-related APIs. MIDI is a technical standard for communication between electronic musical instruments, computers, and other devices.<br> The APIs in this file are used for managing MIDI devices, sending and receiving MIDI messages, and monitoring device status.<br>
The typical process for connecting a MIDI device using OHMIDI is as follows:
1. **Create a client**: Initialize the MIDI client context, and register the device hot swap callback and service exception callback. 
2. **Discover devices and ports**: Obtain the list of currently connected devices and query the port capabilities of the devices. 
3. **Open a device**: Establish a device connection session. 
4. **Enable ports**: Enable the ports based on the port direction (input/output). 
5. **Perform data exchange**: 
   - **Receiving**: Use the callback function to receive MIDI data in the Universal MIDI Packet (UMP) format. 
   - **Sending**: Construct a UMP data packet and send it through the output port. 
6. **Release resources**: Close the port and device and destroy the client after use. 

**File to include**: <midi/native_midi.h>

**Library**: libohmidi.so

**System capability**: SystemCapability.Multimedia.Audio.MIDI

**Since**: 24

**Related module**: [OHMIDI](capi-ohmidi.md)

## Summary

### Function

| Name| Description|
| -- | -- |
| [OH_MIDIStatusCode OH_MIDIClient_Create(OH_MIDIClient **client, OH_MIDICallbacks callbacks, void *userData)](#oh_midiclient_create) | Creates a MIDI client instance. A client is the entry for using the MIDI service. You need to create a client before performing any MIDI operations.<br> MIDI is a system service with strict low-latency requirements. To ensure real-time performance and system stability, the service enforces the following restrictions:<br> 1. System-level restriction: A maximum of eight active MIDI clients are allowed globally.<br> 2. Per-application restriction: A maximum of two MIDI clients are allowed for each application UID. It is recommended that an application maintain a single MIDI client instance throughout its lifecycle for managing multiple devices/ports.<br> When the MIDI function is no longer needed, call [OH_MIDIClient_Destroy](capi-native-midi-h.md#oh_midiclient_destroy) to release the client and all associated resources.|
| [OH_MIDIStatusCode OH_MIDIClient_Destroy(OH_MIDIClient *client)](#oh_midiclient_destroy) | Destroys a MIDI client and releases resources.|
| [OH_MIDIStatusCode OH_MIDIClient_GetDeviceCount(const OH_MIDIClient *client, size_t *count)](#oh_midiclient_getdevicecount) | Obtains the number of the connected MIDI devices. This function is used to determine the size of the buffer required to store the device information.<br> If the application does not have the Bluetooth permission (ohos.permission.ACCESS_BLUETOOTH), Bluetooth MIDI devices are excluded from the device count.|
| [OH_MIDIStatusCode OH_MIDIClient_GetDeviceInfos(const OH_MIDIClient *client, OH_MIDIDeviceInformation *infos, size_t capacity, size_t *actualDeviceCount)](#oh_midiclient_getdeviceinfos) | Obtains information about the connected MIDI devices. The device information is written into the buffer specified by the **infos** parameter. The buffer size should be allocated based on the value returned by [OH_MIDIClient_GetDeviceCount](capi-native-midi-h.md#oh_midiclient_getdevicecount).<br> If the application does not have the Bluetooth permission (ohos.permission.ACCESS_BLUETOOTH), Bluetooth MIDI devices are excluded from the returned device information.|
| [OH_MIDIStatusCode OH_MIDIClient_OpenDevice(OH_MIDIClient *client, int64_t deviceId, OH_MIDIDevice **device)](#oh_midiclient_opendevice) | Opens a MIDI device with the specified ID.|
| [OH_MIDIStatusCode OH_MIDIClient_OpenBLEDevice(OH_MIDIClient *client, const char *deviceAddr, OH_MIDIClient_OnDeviceOpened callback, void *userData)](#oh_midiclient_openbledevice) | Asynchronously opens a Bluetooth Low Energy (BLE) MIDI device. This function is asynchronous. After it is called, a status code is returned immediately (indicating whether the request is successfully sent). The actual connection result (success or failure) will be asynchronously returned through the provided callback after the BLE connection process is complete.|
| [OH_MIDIStatusCode OH_MIDIClient_CloseDevice(OH_MIDIClient *client, OH_MIDIDevice *device)](#oh_midiclient_closedevice) | Closes a MIDI device.|
| [OH_MIDIStatusCode OH_MIDIClient_GetPortCount(const OH_MIDIClient *client, int64_t deviceId, size_t *count)](#oh_midiclient_getportcount) | Obtains the number of ports of a specified MIDI device. This function is used to determine the size of the buffer required to store the port information.|
| [OH_MIDIStatusCode OH_MIDIClient_GetPortInfos(const OH_MIDIClient *client, int64_t deviceId, OH_MIDIPortInformation *infos, size_t capacity, size_t *actualPortCount)](#oh_midiclient_getportinfos) | Obtains the port information of a specified MIDI device. The port information is written to the buffer allocated by the caller.|
| [OH_MIDIStatusCode OH_MIDIDevice_OpenInputPort(OH_MIDIDevice *device, OH_MIDIPortDescriptor descriptor, OH_MIDIDevice_OnReceived callback, void *userData)](#oh_mididevice_openinputport) | Opens the MIDI input port (for receiving data). This API registers a callback function to receive MIDI data streams.|
| [OH_MIDIStatusCode OH_MIDIDevice_OpenOutputPort(OH_MIDIDevice *device, OH_MIDIPortDescriptor descriptor)](#oh_mididevice_openoutputport) | Opens the MIDI output port (for sending data).|
| [OH_MIDIStatusCode OH_MIDIDevice_CloseInputPort(OH_MIDIDevice *device, uint32_t portIndex)](#oh_mididevice_closeinputport) | Closes the MIDI input port.|
| [OH_MIDIStatusCode OH_MIDIDevice_CloseOutputPort(OH_MIDIDevice *device, uint32_t portIndex)](#oh_mididevice_closeoutputport) | Closes the MIDI output port.|
| [OH_MIDIStatusCode OH_MIDIDevice_Send(OH_MIDIDevice *device, uint32_t portIndex, const OH_MIDIEvent *events, uint32_t eventCount, uint32_t *eventsWritten)](#oh_mididevice_send) | Sends MIDI messages in batches (non-blocking mode, with each message being atomic).|
| [OH_MIDIStatusCode OH_MIDIDevice_SendSysEx(OH_MIDIDevice *device, uint32_t portIndex, const uint8_t *data, uint32_t byteSize)](#oh_mididevice_sendsysex) | Sends a system exclusive (SysEx) message that exceeds the standard MIDI message length. Packet fragmentation and blocking wait are automatically performed. This is a utility function for applications that process SysEx messages as the raw byte streams (MIDI 1.0 style, F0...F7).<br> This function applies to both [OH_MIDI_PROTOCOL_1_0](capi-native-midi-base-h.md#oh_midiprotocol) and [OH_MIDI_PROTOCOL_2_0](capi-native-midi-base-h.md#oh_midiprotocol) sessions.<br> The OS MIDI service automatically converts the data into the format required by the device port.|
| [OH_MIDIStatusCode OH_MIDIDevice_FlushOutputPort(OH_MIDIDevice *device, uint32_t portIndex)](#oh_mididevice_flushoutputport) | Clears the messages to be sent in the output buffer. This API immediately discards all MIDI events waiting in the output buffer of a specified port, including events for future timestamps.|

## Function Description

### OH_MIDIClient_Create()

```c
OH_MIDIStatusCode OH_MIDIClient_Create(OH_MIDIClient **client, OH_MIDICallbacks callbacks, void *userData)
```

**Description**

Creates a MIDI client instance. A client is the entry for using the MIDI service. You need to create a client before performing any MIDI operations.<br> MIDI is a system service with strict low-latency requirements. To ensure real-time performance and system stability, the service enforces the following restrictions:<br> 1. System-level restriction: A maximum of eight active MIDI clients are allowed globally.<br> 2. Per-application restriction: A maximum of two MIDI clients are allowed for each application UID. It is recommended that an application maintain a single MIDI client instance throughout its lifecycle for managing multiple devices/ports.<br> When the MIDI function is no longer needed, call [OH_MIDIClient_Destroy](capi-native-midi-h.md#oh_midiclient_destroy) to release the client and all associated resources.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_MIDIClient](capi-ohmidi-oh-midiclientstruct.md) **client | Pointer to the new client handle.|
| [OH_MIDICallbacks](capi-ohmidi-oh-midicallbacks.md) callbacks | Callbacks for system events.|
| void *userData | Pointer to the user-defined data passed to the callback function.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) | **OH_MIDI_STATUS_OK**: The operation is successful.<br>         **OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT**: The **client** parameter is **nullptr**.<br>         **OH_MIDI_STATUS_GENERIC_IPC_FAILURE**: Failed to connect to the system service.<br>         **OH_MIDI_STATUS_TOO_MANY_CLIENTS**: Failed to create the MIDI client due to resource restrictions. This occurs when the number of clients in the application that calls this API exceeds its per-UID quota or the total number of clients in the system has reached the upper limit.|

### OH_MIDIClient_Destroy()

```c
OH_MIDIStatusCode OH_MIDIClient_Destroy(OH_MIDIClient *client)
```

**Description**

Destroys a MIDI client and releases resources.

>**NOTE**
> 
> Call this function to destroy the client when the MIDI function is no longer needed (for example, when the application exits or the MIDI module is disabled). When the client is destroyed, all devices and ports opened through this client are automatically closed (security recycling mechanism). You do not need to manually close them one by one. It is recommended that you manually close resources in reverse order (port -> device -> client) before destroying the client to ensure clear code logic. However, this is not mandatory.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_MIDIClient](capi-ohmidi-oh-midiclientstruct.md) *client | Pointer to the target client handle. The passed value must be an instance created by [OH_MIDIClient_Create](capi-native-midi-h.md#oh_midiclient_create).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) | **OH_MIDI_STATUS_OK**: The operation is successful.<br>         **OH_MIDI_STATUS_INVALID_CLIENT**: The client handle is **null** or invalid.<br>         **OH_MIDI_STATUS_GENERIC_IPC_FAILURE**: Failed to connect to the system service.|

### OH_MIDIClient_GetDeviceCount()

```c
OH_MIDIStatusCode OH_MIDIClient_GetDeviceCount(const OH_MIDIClient *client, size_t *count)
```

**Description**

Obtains the number of the connected MIDI devices. This function is used to determine the size of the buffer required to store the device information.<br> If the application does not have the Bluetooth permission (ohos.permission.ACCESS_BLUETOOTH), Bluetooth MIDI devices are excluded from the device count.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [const OH_MIDIClient](capi-ohmidi-oh-midiclientstruct.md) *client | MIDI client handle. The passed value must be an instance created by [OH_MIDIClient_Create](capi-native-midi-h.md#oh_midiclient_create).|
| size_t *count | Output parameter, which is used to receive the number of devices.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) | **OH_MIDI_STATUS_OK**: The operation is successful.<br>         **OH_MIDI_STATUS_INVALID_CLIENT**: The client handle is invalid.<br>         **OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT**: The **count** parameter is **nullptr**.<br>         **OH_MIDI_STATUS_GENERIC_IPC_FAILURE**: Failed to connect to the system service.|

### OH_MIDIClient_GetDeviceInfos()

```c
OH_MIDIStatusCode OH_MIDIClient_GetDeviceInfos(const OH_MIDIClient *client, OH_MIDIDeviceInformation *infos, size_t capacity, size_t *actualDeviceCount)
```

**Description**

Obtains information about the connected MIDI devices. The device information is written into the buffer specified by the **infos** parameter. The buffer size should be allocated based on the value returned by [OH_MIDIClient_GetDeviceCount](capi-native-midi-h.md#oh_midiclient_getdevicecount).<br> If the application does not have the Bluetooth permission (ohos.permission.ACCESS_BLUETOOTH), Bluetooth MIDI devices are excluded from the returned device information.

> **NOTE**
> 
> If the number of connected devices is greater than the capacity of the **infos** array, the array will contain only partial device information, and the value of **actualDeviceCount** will be equal to that of **capacity**. In this case, the function returns [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode). If the actual number of devices is less than or equal to the value of **capacity**, all available device information will be filled into the **infos** array, and the value of **actualDeviceCount** will be equal to the actual number of devices.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [const OH_MIDIClient](capi-ohmidi-oh-midiclientstruct.md) *client | MIDI client handle. The passed value must be an instance created by [OH_MIDIClient_Create](capi-native-midi-h.md#oh_midiclient_create).|
| [OH_MIDIDeviceInformation](capi-ohmidi-oh-midideviceinformation.md) *infos | Buffer allocated by the user, which is used to store device information.|
| size_t capacity | Maximum number of elements that the buffer can hold.|
| size_t *actualDeviceCount | Output parameter, which is used to receive the actual number of devices written.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) | **OH_MIDI_STATUS_OK**: The operation is successful.<br>         **OH_MIDI_STATUS_INVALID_CLIENT**: The client handle is invalid.<br>         **OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT**: The **infos** or **actualDeviceCount** parameter is **nullptr**.<br>         **OH_MIDI_STATUS_GENERIC_IPC_FAILURE**: Failed to connect to the system service.|

### OH_MIDIClient_OpenDevice()

```c
OH_MIDIStatusCode OH_MIDIClient_OpenDevice(OH_MIDIClient *client, int64_t deviceId, OH_MIDIDevice **device)
```

**Description**

Opens a MIDI device with the specified ID.

> **NOTE**
>  
> Use [OH_MIDIClient_CloseDevice](capi-native-midi-h.md#oh_midiclient_closedevice) to release device resources.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_MIDIClient](capi-ohmidi-oh-midiclientstruct.md) *client | Pointer to the target client handle. The passed value must be an instance created by [OH_MIDIClient_Create](capi-native-midi-h.md#oh_midiclient_create).|
| int64_t deviceId | Unique device ID, which is obtained by [OH_MIDIClient_GetDeviceInfos](capi-native-midi-h.md#oh_midiclient_getdeviceinfos).|
| [OH_MIDIDevice](capi-ohmidi-oh-mididevicestruct.md) **device | Pointer to the device handle, which is allocated by the system.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) | **OH_MIDI_STATUS_OK**: The operation is successful.<br>         **OH_MIDI_STATUS_INVALID_CLIENT**: The client handle is invalid.<br>         **OH_MIDI_STATUS_DEVICE_ALREADY_OPEN**: The device has been opened by the current client.<br>         **OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT**: The **device** parameter is **nullptr**, or the **deviceId** parameter does not exist.<br>         **OH_MIDI_STATUS_TOO_MANY_OPEN_DEVICES**: The number of devices opened by the client has reached the upper limit.<br>         **OH_MIDI_STATUS_GENERIC_IPC_FAILURE**: Failed to connect to the system service.|

### OH_MIDIClient_OpenBLEDevice()

```c
OH_MIDIStatusCode OH_MIDIClient_OpenBLEDevice(OH_MIDIClient *client, const char *deviceAddr, OH_MIDIClient_OnDeviceOpened callback, void *userData)
```

**Description**

Asynchronously opens a Bluetooth Low Energy (BLE) MIDI device. This function is asynchronous. After it is called, a status code is returned immediately (indicating whether the request is successfully sent). The actual connection result (success or failure) will be asynchronously returned through the provided callback after the BLE connection process is complete.

> **NOTE**
> 
> If the Bluetooth permission is denied, the [OH_MIDIClient_OnDeviceOpened](capi-native-midi-base-h.md#oh_midiclient_ondeviceopened) callback will be called with the **opened** parameter set to **false** and the **device** parameter set to **null**. The application should check the **opened** parameter before attempting to use the device handle.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_MIDIClient](capi-ohmidi-oh-midiclientstruct.md) *client | Pointer to the target client handle. The passed value must be an instance created by [OH_MIDIClient_Create](capi-native-midi-h.md#oh_midiclient_create).|
| const char *deviceAddr | MAC address of the BLE device, for example, **AA:BB:CC:DD:EE:FF**.|
| [OH_MIDIClient_OnDeviceOpened](capi-native-midi-base-h.md#oh_midiclient_ondeviceopened) callback | Callback function to be called when the connection process is complete.|
| void *userData | Pointer to the user-defined data passed to the callback function.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) | **OH_MIDI_STATUS_OK**: The connection request has been successfully distributed.<br>         **OH_MIDI_STATUS_INVALID_CLIENT**: The client handle is invalid.<br>         **OH_MIDI_STATUS_DEVICE_ALREADY_OPEN**: The device has been opened by the current client.<br>         **OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT**: The **deviceAddr** or **callback** parameter is **nullptr**.<br>         **OH_MIDI_STATUS_PERMISSION_DENIED**: Permission denied. The application has not declared or obtained the required permission.<br>         **OH_MIDI_STATUS_TOO_MANY_OPEN_DEVICES**: The number of devices opened by the client has reached the upper limit.<br>         **OH_MIDI_STATUS_GENERIC_IPC_FAILURE**: The service is inaccessible.|

### OH_MIDIClient_CloseDevice()

```c
OH_MIDIStatusCode OH_MIDIClient_CloseDevice(OH_MIDIClient *client, OH_MIDIDevice *device)
```

**Description**

Closes a MIDI device.

> **NOTE**
>
> When a device is closed, all opened ports on the device are also closed. This function must be used together with [OH_MIDIClient_OpenDevice](capi-native-midi-h.md#oh_midiclient_opendevice) or [OH_MIDIClient_OpenBLEDevice](capi-native-midi-h.md#oh_midiclient_openbledevice).

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_MIDIClient](capi-ohmidi-oh-midiclientstruct.md) *client | Pointer to the target client handle. The passed value must be an instance created by [OH_MIDIClient_Create](capi-native-midi-h.md#oh_midiclient_create).|
| [OH_MIDIDevice](capi-ohmidi-oh-mididevicestruct.md) *device | Handle to the target device. The passed value must be an instance returned by [OH_MIDIClient_OpenDevice](capi-native-midi-h.md#oh_midiclient_opendevice) or [OH_MIDIClient_OpenBLEDevice](capi-native-midi-h.md#oh_midiclient_openbledevice).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) | **OH_MIDI_STATUS_OK**: The operation is successful.<br>         **OH_MIDI_STATUS_INVALID_CLIENT**: The client handle is invalid.<br>         **OH_MIDI_STATUS_INVALID_DEVICE_HANDLE**: The device handle is invalid.|

### OH_MIDIClient_GetPortCount()

```c
OH_MIDIStatusCode OH_MIDIClient_GetPortCount(const OH_MIDIClient *client, int64_t deviceId, size_t *count)
```

**Description**

Obtains the number of ports of a specified MIDI device. This function is used to determine the size of the buffer required to store the port information.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [const OH_MIDIClient](capi-ohmidi-oh-midiclientstruct.md) *client | MIDI client handle. The passed value must be an instance created by [OH_MIDIClient_Create](capi-native-midi-h.md#oh_midiclient_create).|
| int64_t deviceId | Target device ID.|
| size_t *count | Output parameter, which is used to receive the number of ports.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) | **OH_MIDI_STATUS_OK**: The operation is successful.<br>         **OH_MIDI_STATUS_INVALID_CLIENT**: The client handle is invalid.<br>         **OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT**: The **count** parameter is **nullptr**, or the **deviceId** parameter is invalid.<br>         **OH_MIDI_STATUS_GENERIC_IPC_FAILURE**: Failed to connect to the system service.|

### OH_MIDIClient_GetPortInfos()

```c
OH_MIDIStatusCode OH_MIDIClient_GetPortInfos(const OH_MIDIClient *client, int64_t deviceId, OH_MIDIPortInformation *infos, size_t capacity, size_t *actualPortCount)
```

**Description**

Obtains the port information of a specified MIDI device. The port information is written to the buffer allocated by the caller.

> **NOTE**
> 
> If the actual number of ports is greater than the capacity of the **infos** array, the array will contain only partial port information, and the value of **actualPortCount** will be equal to that of **capacity**. In this case, the function returns [OH_MIDI_STATUS_OK](capi-native-midi-base-h.md#oh_midistatuscode). If the actual number of ports is less than or equal to the value of **capacity**, all available port information will be filled into the **infos** array, and the value of **actualPortCount** will be equal to the actual number of ports.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [const OH_MIDIClient](capi-ohmidi-oh-midiclientstruct.md) *client | MIDI client handle. The passed value must be an instance created by [OH_MIDIClient_Create](capi-native-midi-h.md#oh_midiclient_create).|
| int64_t deviceId | Target device ID.|
| [OH_MIDIPortInformation](capi-ohmidi-oh-midiportinformation.md) *infos | Buffer allocated by the user, which is used to store device information.|
| size_t capacity | Maximum number of elements that the **infos** buffer can hold.|
| size_t *actualPortCount | Output parameter, which is used to receive the actual number of ports written.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) | **OH_MIDI_STATUS_OK**: The operation is successful.<br>         **OH_MIDI_STATUS_INVALID_CLIENT**: The client handle is invalid.<br>         **OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT**: The **infos** or **actualPortCount** parameter is **nullptr**, or the **deviceId** parameter is invalid.<br>         **OH_MIDI_STATUS_GENERIC_IPC_FAILURE**: Failed to connect to the system service.|

### OH_MIDIDevice_OpenInputPort()

```c
OH_MIDIStatusCode OH_MIDIDevice_OpenInputPort(OH_MIDIDevice *device, OH_MIDIPortDescriptor descriptor, OH_MIDIDevice_OnReceived callback, void *userData)
```

**Description**

Opens the MIDI input port (for receiving data). This API registers a callback function to receive MIDI data streams.

> **NOTE**
> 
> Use [OH_MIDIDevice_CloseInputPort](capi-native-midi-h.md#oh_mididevice_closeinputport) to close the input port.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_MIDIDevice](capi-ohmidi-oh-mididevicestruct.md) *device | Handle to the target device. The passed value must be an instance returned by [OH_MIDIClient_OpenDevice](capi-native-midi-h.md#oh_midiclient_opendevice) or [OH_MIDIClient_OpenBLEDevice](capi-native-midi-h.md#oh_midiclient_openbledevice).|
| [OH_MIDIPortDescriptor](capi-ohmidi-oh-midiportdescriptor.md) descriptor | Port index and protocol configuration.|
| [OH_MIDIDevice_OnReceived](capi-native-midi-base-h.md#oh_mididevice_onreceived) callback | Callback function called when data is available.|
| void *userData | Pointer to the user-defined data passed to the callback function.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) | **OH_MIDI_STATUS_OK**: The operation is successful.<br>         **OH_MIDI_STATUS_INVALID_DEVICE_HANDLE**: The device handle is invalid.<br>         **OH_MIDI_STATUS_INVALID_PORT**: The port index is invalid or the port is not an input port.<br>         **OH_MIDI_STATUS_PORT_ALREADY_OPEN**: The port has already been opened by the client.<br>         **OH_MIDI_STATUS_TOO_MANY_OPEN_PORTS**: The number of opened ports has reached the upper limit.<br>         **OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT**: The **callback** parameter is **nullptr**.<br>         **OH_MIDI_STATUS_GENERIC_IPC_FAILURE**: Failed to connect to the system service.|

### OH_MIDIDevice_OpenOutputPort()

```c
OH_MIDIStatusCode OH_MIDIDevice_OpenOutputPort(OH_MIDIDevice *device, OH_MIDIPortDescriptor descriptor)
```

**Description**

Opens the MIDI output port (for sending data).

> **NOTE**
>
> Use [OH_MIDIDevice_CloseOutputPort](capi-native-midi-h.md#oh_mididevice_closeoutputport) to close the output port.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_MIDIDevice](capi-ohmidi-oh-mididevicestruct.md) *device | Handle to the target device. The passed value must be an instance returned by [OH_MIDIClient_OpenDevice](capi-native-midi-h.md#oh_midiclient_opendevice) or [OH_MIDIClient_OpenBLEDevice](capi-native-midi-h.md#oh_midiclient_openbledevice).|
| [OH_MIDIPortDescriptor](capi-ohmidi-oh-midiportdescriptor.md) descriptor | Port index and protocol configuration.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) | **OH_MIDI_STATUS_OK**: The operation is successful.<br>         **OH_MIDI_STATUS_INVALID_DEVICE_HANDLE**: The device handle is invalid.<br>         **OH_MIDI_STATUS_INVALID_PORT**: The port index is invalid or the port is not an output port.<br>         **OH_MIDI_STATUS_PORT_ALREADY_OPEN**: The port has already been opened by the client.<br>         **OH_MIDI_STATUS_TOO_MANY_OPEN_PORTS**: The number of opened ports has reached the upper limit.<br>         **OH_MIDI_STATUS_GENERIC_IPC_FAILURE**: Failed to connect to the system service.|

### OH_MIDIDevice_CloseInputPort()

```c
OH_MIDIStatusCode OH_MIDIDevice_CloseInputPort(OH_MIDIDevice *device, uint32_t portIndex)
```

**Description**

Closes the MIDI input port.

> **NOTE**
> 
> This function must be used together with [OH_MIDIDevice_OpenInputPort](capi-native-midi-h.md#oh_mididevice_openinputport).

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_MIDIDevice](capi-ohmidi-oh-mididevicestruct.md) *device | Handle to the target device. The passed value must be an instance returned by [OH_MIDIClient_OpenDevice](capi-native-midi-h.md#oh_midiclient_opendevice) or [OH_MIDIClient_OpenBLEDevice](capi-native-midi-h.md#oh_midiclient_openbledevice).|
| uint32_t portIndex | Index of the input port to be closed.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) | **OH_MIDI_STATUS_OK**: The operation is successful.<br>         **OH_MIDI_STATUS_INVALID_DEVICE_HANDLE**: The device handle is invalid.<br>         **OH_MIDI_STATUS_INVALID_PORT**: The port index is invalid or the port is not opened.<br>         **OH_MIDI_STATUS_GENERIC_IPC_FAILURE**: Failed to connect to the system service.|

### OH_MIDIDevice_CloseOutputPort()

```c
OH_MIDIStatusCode OH_MIDIDevice_CloseOutputPort(OH_MIDIDevice *device, uint32_t portIndex)
```

**Description**

Closes the MIDI output port.

> **NOTE**
> 
> This function must be used together with [OH_MIDIDevice_OpenOutputPort](capi-native-midi-h.md#oh_mididevice_openoutputport).

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_MIDIDevice](capi-ohmidi-oh-mididevicestruct.md) *device | Handle to the target device. The passed value must be an instance returned by [OH_MIDIClient_OpenDevice](capi-native-midi-h.md#oh_midiclient_opendevice) or [OH_MIDIClient_OpenBLEDevice](capi-native-midi-h.md#oh_midiclient_openbledevice).|
| uint32_t portIndex | Index of the output port to be closed.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) | **OH_MIDI_STATUS_OK**: The operation is successful.<br>         **OH_MIDI_STATUS_INVALID_DEVICE_HANDLE**: The device handle is invalid.<br>         **OH_MIDI_STATUS_INVALID_PORT**: The port index is invalid or the port is not an output port.<br>         **OH_MIDI_STATUS_GENERIC_IPC_FAILURE**: Failed to connect to the system service.|

### OH_MIDIDevice_Send()

```c
OH_MIDIStatusCode OH_MIDIDevice_Send(OH_MIDIDevice *device, uint32_t portIndex, const OH_MIDIEvent *events, uint32_t eventCount, uint32_t *eventsWritten)
```

**Description**

Sends MIDI messages in batches (non-blocking mode, with each message being atomic).

> **NOTE**
> 
> Write the MIDI event array to the shared memory buffer.
> - Single-message atomicity: Each event is processed as an indivisible unit. No message will be truncated.
> - Batch operation non-atomicity: The entire array may not be written successfully. If the buffer space is insufficient, events that have been successfully written will not be rolled back. The function returns [OH_MIDI_STATUS_WOULD_BLOCK](capi-native-midi-base-h.md#oh_midistatuscode) and provides the number of successfully written events via the **eventsWritten** parameter, allowing you to resume sending the remaining events from the breakpoint.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_MIDIDevice](capi-ohmidi-oh-mididevicestruct.md) *device | Handle to the target device. The passed value must be an instance returned by [OH_MIDIClient_OpenDevice](capi-native-midi-h.md#oh_midiclient_opendevice) or [OH_MIDIClient_OpenBLEDevice](capi-native-midi-h.md#oh_midiclient_openbledevice).|
| uint32_t portIndex | Index of the target port.|
| [const OH_MIDIEvent](capi-ohmidi-oh-midievent.md) *events | Pointer to the array of events to be sent. You need to allocate the memory space.|
| uint32_t eventCount | Number of events in the array.|
| uint32_t *eventsWritten | Output parameter, which returns the number of events that are successfully sent.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) | **OH_MIDI_STATUS_OK**: All data has been successfully processed and written.<br>         **OH_MIDI_STATUS_INVALID_DEVICE_HANDLE**: The device handle is invalid.<br>         **OH_MIDI_STATUS_INVALID_PORT**: The port index is invalid or the port is not opened.<br>         **OH_MIDI_STATUS_WOULD_BLOCK**: The buffer is full. (Check the value of **eventsWritten**.)<br>         **OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT**: Invalid parameters.<br>         **OH_MIDI_STATUS_GENERIC_IPC_FAILURE**: Failed to connect to the system service.|

### OH_MIDIDevice_SendSysEx()

```c
OH_MIDIStatusCode OH_MIDIDevice_SendSysEx(OH_MIDIDevice *device, uint32_t portIndex, const uint8_t *data, uint32_t byteSize)
```

**Description**

Sends a system exclusive (SysEx) message that exceeds the standard MIDI message length. Packet fragmentation and blocking wait are automatically performed. This is a utility function for applications that process SysEx messages as the raw byte streams (MIDI 1.0 style, F0...F7).<br> This function applies to both [OH_MIDI_PROTOCOL_1_0](capi-native-midi-base-h.md#oh_midiprotocol) and [OH_MIDI_PROTOCOL_2_0](capi-native-midi-base-h.md#oh_midiprotocol) sessions.<br> The OS MIDI service automatically converts the data into the format required by the device port.

> **NOTE**
> 
> This is a blocking function that performs a loop-write. If the buffer is full, it will block and retry until the entire data is successfully written.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_MIDIDevice](capi-ohmidi-oh-mididevicestruct.md) *device | Handle to the target device. The passed value must be an instance returned by [OH_MIDIClient_OpenDevice](capi-native-midi-h.md#oh_midiclient_opendevice) or [OH_MIDIClient_OpenBLEDevice](capi-native-midi-h.md#oh_midiclient_openbledevice).|
| uint32_t portIndex | Index of the target port.|
| const uint8_t *data | Pointer to the byte stream to be sent. You need to allocate the memory space.|
| uint32_t byteSize | Size of the data in bytes.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) | **OH_MIDI_STATUS_OK**: All data has been successfully processed and written.<br>         **OH_MIDI_STATUS_INVALID_DEVICE_HANDLE**: The device handle is invalid.<br>         **OH_MIDI_STATUS_INVALID_PORT**: The port index is invalid or the port is not opened.<br>         OH_MIDI_STATUS_TIMEOUT: The operation cannot be completed within a reasonable time. You can use [OH_MIDIDevice_FlushOutputPort](capi-native-midi-h.md#oh_mididevice_flushoutputport) to reset the operation.<br>         **OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT**: Invalid parameters.|

### OH_MIDIDevice_FlushOutputPort()

```c
OH_MIDIStatusCode OH_MIDIDevice_FlushOutputPort(OH_MIDIDevice *device, uint32_t portIndex)
```

**Description**

Clears the messages to be sent in the output buffer. This API immediately discards all MIDI events waiting in the output buffer of a specified port, including events for future timestamps.

> **NOTE**
> 
> This operation does not send the "All Notes Off" message. It only clears the queue.

**Since**: 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_MIDIDevice](capi-ohmidi-oh-mididevicestruct.md) *device | Handle to the target device. The passed value must be an instance returned by [OH_MIDIClient_OpenDevice](capi-native-midi-h.md#oh_midiclient_opendevice) or [OH_MIDIClient_OpenBLEDevice](capi-native-midi-h.md#oh_midiclient_openbledevice).|
| uint32_t portIndex | Index of the target port.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) | **OH_MIDI_STATUS_OK**: The operation is successful.<br>         **OH_MIDI_STATUS_INVALID_DEVICE_HANDLE**: The device handle is invalid.<br>         **OH_MIDI_STATUS_INVALID_PORT**: The port index is invalid or the port is not an output port.<br>         **OH_MIDI_STATUS_GENERIC_IPC_FAILURE**: Failed to connect to the system service.|
