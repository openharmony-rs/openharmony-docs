# native_midi_base.h
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @owen_creeper-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

## Overview

This file declares the basic data structure of the MIDI module. It defines the basic types, enumerations, structs, and callback functions of the MIDI APIs.

**File to include**: <midi/native_midi_base.h>

**Library**: libohmidi.so

**System capability**: SystemCapability.Multimedia.Audio.MIDI

**Since:** 24

**Related module**: [OHMIDI](capi-ohmidi.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_MIDIEvent](capi-ohmidi-oh-midievent.md) | OH_MIDIEvent | Describes a generic MIDI event structure, which is applicable to both raw byte stream (MIDI 1.0) and Universal MIDI Packet (UMP) data formats.|
| [OH_MIDIDeviceInformation](capi-ohmidi-oh-midideviceinformation.md) | OH_MIDIDeviceInformation | Describes the device information struct, such as the storage device ID.|
| [OH_MIDIPortInformation](capi-ohmidi-oh-midiportinformation.md) | OH_MIDIPortInformation | Describes the port information struct, which is used to enumerate ports, including port names.|
| [OH_MIDIPortDescriptor](capi-ohmidi-oh-midiportdescriptor.md) | OH_MIDIPortDescriptor | Describes the port descriptor struct, which is used to specify the port index and protocol behavior for opening a port.|
| [OH_MIDICallbacks](capi-ohmidi-oh-midicallbacks.md) | OH_MIDICallbacks | Describes the client callback struct. Client callbacks include the device change callback and error handling callback.|
| [OH_MIDIClientStruct](capi-ohmidi-oh-midiclientstruct.md) | OH_MIDIClient | Declares a MIDI client.|
| [OH_MIDIDeviceStruct](capi-ohmidi-oh-mididevicestruct.md) | OH_MIDIDevice | Declares a MIDI device.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_MIDIStatusCode](#oh_midistatuscode) | OH_MIDIStatusCode | Enumerates MIDI status codes. It defines MIDI operation status codes, which are used to indicate operation success or failure causes.|
| [OH_MIDIPortDirection](#oh_midiportdirection) | OH_MIDIPortDirection | Enumerates the port directions, which indicate MIDI ports' data transmission directions.|
| [OH_MIDIProtocol](#oh_midiprotocol) | OH_MIDIProtocol | Enumerates the MIDI protocol versions, which are used to specify the MIDI protocols used by ports.|
| [OH_MIDIDeviceType](#oh_mididevicetype) | OH_MIDIDeviceType | Enumerates MIDI device types, which define MIDI devices' connection types.|
| [OH_MIDIDeviceChangeAction](#oh_mididevicechangeaction) | OH_MIDIDeviceChangeAction | Enumerates the operations that cause device connection status changes, which are used to identify device connection and disconnection events.|

### Function

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [typedef void (\*OH_MIDICallback_OnDeviceChange)(void *userData, OH_MIDIDeviceChangeAction action, OH_MIDIDeviceInformation deviceInfo)](#oh_midicallback_ondevicechange) | OH_MIDICallback_OnDeviceChange | Callback for monitoring device connection and disconnection.|
| [typedef void (\*OH_MIDICallback_OnError)(void *userData, OH_MIDIStatusCode code)](#oh_midicallback_onerror) | OH_MIDICallback_OnError | Callback for handling client-level errors. It is called when a critical error (such as service crash) occurs in the MIDI service. In this case, an application may need to re-create the client.|
| [typedef void (\*OH_MIDIDevice_OnReceived)(void *userData, const OH_MIDIEvent *events, size_t eventCount)](#oh_mididevice_onreceived) | OH_MIDIDevice_OnReceived | Callback for receiving MIDI data (batch processing).|
| [typedef void (\*OH_MIDIClient_OnDeviceOpened)(void *userData, bool opened, OH_MIDIDevice *device, OH_MIDIDeviceInformation info)](#oh_midiclient_ondeviceopened) | OH_MIDIClient_OnDeviceOpened | Callback for the result of asynchronously opening a BLE device.|

## Enum Description

### OH_MIDIStatusCode

```c
enum OH_MIDIStatusCode
```

**Description**

Enumerates MIDI status codes. It defines MIDI operation status codes, which are used to indicate operation success or failure causes.

**Since:** 24

| Enum Item| Description|
| -- | -- |
| OH_MIDI_STATUS_OK = 0 |  The operation succeeded.<br>**Since**: 24|
| OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT = 35500001 |  Invalid parameter (for example, a null pointer).<br>**Since**: 24|
| OH_MIDI_STATUS_GENERIC_IPC_FAILURE = 35500002 |  IPC fails.<br>**Since**: 24|
| OH_MIDI_STATUS_INVALID_CLIENT = 35500003 |  Invalid client handle.<br>**Since**: 24|
| OH_MIDI_STATUS_INVALID_DEVICE_HANDLE = 35500004 |  Invalid device handle.<br>**Since**: 24|
| OH_MIDI_STATUS_INVALID_PORT = 35500005 |  Invalid port index.<br>**Since**: 24|
| OH_MIDI_STATUS_WOULD_BLOCK = 35500006 |  The send buffer is temporarily full, indicating that the shared memory buffer is currently out of space.<br> This code is returned by a non-blocking send operation if messages cannot be placed into the buffer. In this case, you are advised to wait for about 10 ms and try again.<br>**Since**: 24|
| OH_MIDI_STATUS_TIMEOUT = 35500007 |  The operation times out.<br>**Since**: 24|
| OH_MIDI_STATUS_TOO_MANY_OPEN_DEVICES = 35500008 |  The number of devices that can be opened on the client has reached the maximum (16).<br> To open a new device, you must first close an existing one.<br>**Since**: 24|
| OH_MIDI_STATUS_TOO_MANY_OPEN_PORTS = 35500009 |  The number of ports opened on the client has reached the maximum (64).<br> To open a new port, you must first close an existing one.<br>**Since**: 24|
| OH_MIDI_STATUS_DEVICE_ALREADY_OPEN = 35500010 |  The device has already been opened on the client. A device cannot be opened repeatedly on the same client.<br>**Since**: 24|
| OH_MIDI_STATUS_PORT_ALREADY_OPEN = 35500011 |  The port has already been opened on the client. A port cannot be opened repeatedly on the same client.<br>**Since**: 24|
| OH_MIDI_STATUS_TOO_MANY_CLIENTS = 35500012 |  The maximum number of clients (8 system-level, or 2 application-level per UID) has been reached. The application should wait or release other resources and then try again.<br>**Since**: 24|
| OH_MIDI_STATUS_PERMISSION_DENIED = 35500013 |  Permission denied. This code is returned when an application attempts to perform an operation without the required permission (for example, the Bluetooth permission for BLE devices).<br>**Since**: 24|
| OH_MIDI_STATUS_SERVICE_DIED = 35500014 |  The MIDI system service has crashed or been disconnected. The client must be destroyed and re-created.<br>**Since**: 24|
| OH_MIDI_STATUS_SYSTEM_ERROR = 35500100 |  Internal system error. An unexpected system-level error occurs.<br>**Since**: 24|

### OH_MIDIPortDirection

```c
enum OH_MIDIPortDirection
```

**Description**

Enumerates the port directions, which indicate MIDI ports' data transmission directions.

**Since:** 24

| Enum Item| Description|
| -- | -- |
| OH_MIDI_PORT_DIRECTION_INPUT = 0 | Input (device -> host).<br>**Since**: 24|
| OH_MIDI_PORT_DIRECTION_OUTPUT = 1 | Output (host -> device).<br>**Since**: 24|

### OH_MIDIProtocol

```c
enum OH_MIDIProtocol
```

**Description**

Enumerates the MIDI protocol versions, which are used to specify the MIDI protocols used by ports.

> **NOTE**
> 
> The SDK always uses the UMP format for data transmission, regardless of which protocol is selected. This enum defines the data behavior and semantics of the connection, not the data structure. MT is the identifier for the message type within a UMP packet; different MT values correspond to different types of MIDI messages.

**Since:** 24

| Enum Item| Description|
| -- | -- |
| OH_MIDI_PROTOCOL_1_0 = 1 | Traditional MIDI 1.0 semantics.<br> Under this protocol, the MIDI system service expects to receive the following types of UMP messages:<br> - UMP packets that strictly comply with the MIDI 1.0 protocol specifications.<br> - **MT 0x0**: utility messages (such as timestamps).<br> - **MT 0x1**: system real-time and system common messages.<br> - **MT 0x2**: MIDI 1.0 channel voice messages (32-bit).<br> - **MT 0x3**: data messages (64-bit), used for SysEx (7-bit payload).<br> - If the target hardware uses MIDI 1.0, the service converts UMP packets back to byte streams (F0...F7).<br> - If the target hardware uses MIDI 2.0, the service directly sends the unconverted UMP packets (encapsulated based on MIDI 1.0).<br>**Since**: 24|
| OH_MIDI_PROTOCOL_2_0 = 2 | MIDI 2.0 semantics.<br> Under this protocol, the MIDI system service expects to receive the following types of UMP messages:<br> - UMP packets that utilize the features of MIDI 2.0.<br> - **MT 0x4**: MIDI 2.0 channel voice messages (64-bit, high resolution).<br> - **MT 0x0**: utility messages (timestamp).<br> - **MT 0xD**: Flex data messages (128-bit, such as text and lyrics).<br> - **MT 0xF**: UMP stream messages (128-bit, endpoint discovery and functional blocks).<br> - **MT 0x3/MT 0x5**: data messages (64-bit or 128-bit).<br>**Since**: 24|

### OH_MIDIDeviceType

```c
enum OH_MIDIDeviceType
```

**Description**

Enumerates MIDI device types, which define MIDI devices' connection types.

**Since:** 24

| Enum Item| Description|
| -- | -- |
| OH_MIDI_DEVICE_TYPE_USB = 0 | USB MIDI device.|
| OH_MIDI_DEVICE_TYPE_BLE = 1 | Bluetooth Low Energy (BLE) MIDI device.|

### OH_MIDIDeviceChangeAction

```c
enum OH_MIDIDeviceChangeAction
```

**Description**

Enumerates the operations that cause device connection status changes, which are used to identify device connection and disconnection events.

**Since:** 24

| Enum Item| Description|
| -- | -- |
| OH_MIDI_DEVICE_CHANGE_ACTION_CONNECTED = 0 | The device is connected.<br>**Since**: 24|
| OH_MIDI_DEVICE_CHANGE_ACTION_DISCONNECTED = 1 | The device is disconnected.<br>**Since**: 24|


## Function Description

### OH_MIDICallback_OnDeviceChange()

```c
typedef void (*OH_MIDICallback_OnDeviceChange)(void *userData, OH_MIDIDeviceChangeAction action, OH_MIDIDeviceInformation deviceInfo)
```

**Description**

Callback for monitoring device connection and disconnection.

**Since:** 24

**Parameters**

| Name| Description                                                                                  |
| -- |--------------------------------------------------------------------------------------|
| void \*userData | Pointer to the custom data passed when [OH_MIDIClient_Create](./capi-native-midi-h.md#oh_midiclient_create) is called.|
| [OH_MIDIDeviceChangeAction](capi-native-midi-base-h.md#oh_mididevicechangeaction) action | Device change operation (connected/disconnected).                                                                    |
| [OH_MIDIDeviceInformation](capi-ohmidi-oh-midideviceinformation.md) deviceInfo | Information about the device change.                                                                            |

### OH_MIDICallback_OnError()

```c
typedef void (*OH_MIDICallback_OnError)(void *userData, OH_MIDIStatusCode code)
```

**Description**

Callback for handling client-level errors. It is called when a critical error (such as service crash) occurs in the MIDI service. In this case, an application may need to re-create the client.

**Since:** 24

**Parameters**

| Name| Description|
| -- | -- |
| void \*userData | Pointer to the custom data passed when [OH_MIDIClient_Create](./capi-native-midi-h.md#oh_midiclient_create) is called.|
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) code | Status code, indicating the cause of the error.|

### OH_MIDIDevice_OnReceived()

```c
typedef void (*OH_MIDIDevice_OnReceived)(void *userData, const OH_MIDIEvent *events, size_t eventCount)
```

**Description**

Callback for receiving MIDI data (batch processing).

> **NOTE**
> 
> Memory safety and thread safety precautions:
> - Memory safety: The **events** array and all data pointers within it are temporary and valid only during this callback. Accessing these pointers after the callback returns results in undefined behavior (crashes or memory corruption). Callers must copy any data that needs to be retained.
> - Thread safety: This callback is called on a high-priority system thread. Avoid blocking operations, heavy computation, or I/O operations in the callback.

**Since:** 24

**Parameters**

| Name| Description|
| -- | -- |
| void \*userData | Pointer to the custom data passed when [OH_MIDIClient_Create](./capi-native-midi-h.md#oh_midiclient_create) is called.|
| [const OH_MIDIEvent](capi-ohmidi-oh-midievent.md) \*events | Pointer to the array of received MIDI events.|
| size_t eventCount | Number of events in the array.|

### OH_MIDIClient_OnDeviceOpened()

```c
typedef void (*OH_MIDIClient_OnDeviceOpened)(void *userData, bool opened, OH_MIDIDevice *device, OH_MIDIDeviceInformation info)
```

**Description**

Callback for the result of asynchronously opening a BLE device.

**Since:** 24

**Parameters**

| Name| Description                                                                                                                                                       |
| -- |-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| void \*userData | Pointer to the custom data passed when [OH_MIDIClient_OpenBLEDevice](./capi-native-midi-h.md#oh_midiclient_openbledevice) is called.                                                       |
| bool opened | Whether the device is successfully opened.<br> The value **true** indicates that the device is successfully opened and the device handle is valid. The value **false** indicates that the device fails to be opened and the device handle is **NULL**.                                                                                               |
| [OH_MIDIDevice](capi-ohmidi-oh-mididevicestruct.md) \*device | Handle to the opened device.<br> If the value of **opened** is **true**, the application must call [OH_MIDIClient_CloseDevice](./capi-native-midi-h.md#oh_midiclient_closedevice) to close the handle when it is no longer needed.<br> If the value of **opened** is **false**, the value of this parameter is **NULL**.|
| [OH_MIDIDeviceInformation](capi-ohmidi-oh-midideviceinformation.md) info | Information about the opened device.<br> **Note**: This object is valid only within this callback. To persist specific properties (such as the ID or name), make a copy of the device information.                                                                                       |
