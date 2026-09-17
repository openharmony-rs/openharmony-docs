# native_midi_base.h

## Overview

Declares the underlying data structure for MIDI module.

**Library**: libohmidi.so

**System capability**: SystemCapability.Multimedia.Audio.MIDI

**Since**: 24

**Related module**: [OHMIDI](capi-ohmidi.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_MIDIEvent](capi-ohmidi-oh-midievent.md) | OH_MIDIEvent | MIDI Event Structure (Universal). The event data is transferred in Universal MIDI Packets (UMP) format. MIDI 1.0 byte stream data should be converted to UMP format before filling this structure. |
| [OH_MIDIDeviceInformation](capi-ohmidi-oh-midideviceinformation.md) | OH_MIDIDeviceInformation | Device Information. Used for enumeration and display. |
| [OH_MIDIPortInformation](capi-ohmidi-oh-midiportinformation.md) | OH_MIDIPortInformation | Port Information (detailed). Used for enumeration (contains display names). |
| [OH_MIDIPortDescriptor](capi-ohmidi-oh-midiportdescriptor.md) | OH_MIDIPortDescriptor | Port Descriptor. |
| [OH_MIDICallbacks](capi-ohmidi-oh-midicallbacks.md) | OH_MIDICallbacks | Client callbacks structure. |
| [OH_MIDIClientStruct](capi-ohmidi-oh-midiclientstruct.md) | OH_MIDIClient | Declares a MIDI client. |
| [OH_MIDIDeviceStruct](capi-ohmidi-oh-mididevicestruct.md) | OH_MIDIDevice | Declares a MIDI device. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_MIDIStatusCode](#oh_midistatuscode) | OH_MIDIStatusCode | MIDI status code enumeration. |
| [OH_MIDIPortDirection](#oh_midiportdirection) | OH_MIDIPortDirection | Port direction enumeration. |
| [OH_MIDIProtocol](#oh_midiprotocol) | OH_MIDIProtocol | MIDI transport protocol semantics. |
| [OH_MIDIDeviceType](#oh_mididevicetype) | OH_MIDIDeviceType | MIDI Device type. |
| [OH_MIDIDeviceChangeAction](#oh_mididevicechangeaction) | OH_MIDIDeviceChangeAction | Device connection state change action. |

### Macro

| Name | Description |
| -- | -- |
| NATIVE_MIDI_BASE_H | Declares the underlying data structure for MIDI module.<br>**Since**: 24<br>**System capability**: SystemCapability.Multimedia.Audio.MIDI |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_MIDICallback_OnDeviceChange)(void *userData, OH_MIDIDeviceChangeAction action, OH_MIDIDeviceInformation deviceInfo)](#oh_midicallback_ondevicechange) | OH_MIDICallback_OnDeviceChange | Callback for monitoring device connection/disconnection. |
| [typedef void (\*OH_MIDICallback_OnError)(void *userData, OH_MIDIStatusCode code)](#oh_midicallback_onerror) | OH_MIDICallback_OnError | Callback for handling client-level errors. Invoked when a critical error occurs in the MIDI service (e.g., service crash). Applications may need to recreate the client when this occurs. |
| [typedef void (\*OH_MIDIDevice_OnReceived)(void *userData, const OH_MIDIEvent *events, size_t eventCount)](#oh_mididevice_onreceived) | OH_MIDIDevice_OnReceived | Callback for receiving MIDI data (Batch Processing). |
| [typedef void (\*OH_MIDIClient_OnDeviceOpened)(void *userData, bool opened, OH_MIDIDevice *device, OH_MIDIDeviceInformation info)](#oh_midiclient_ondeviceopened) | OH_MIDIClient_OnDeviceOpened | Callback for the result of asynchronously opening a BLE device.<br> This callback is invoked when the BLE device open attempt finishes, either successfully or with a failure. |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_MIDICallback_OnDeviceChange)( void *userData, OH_MIDIDeviceChangeAction action, OH_MIDIDeviceInformation deviceInfo) | Callback for monitoring device connection/disconnection.<br>**Since**: 24 |
| void (*OH_MIDICallback_OnError)(void *userData, OH_MIDIStatusCode code) | Callback for handling client-level errors. Invoked when a critical error occurs in the MIDI service (e.g., service crash). Applications may need to recreate the client when this occurs.<br>**Since**: 24 |
| void (*OH_MIDIDevice_OnReceived)(void *userData, const OH_MIDIEvent *events, size_t eventCount) | Callback for receiving MIDI data (Batch Processing).<br>**Since**: 24 |
| void (*OH_MIDIClient_OnDeviceOpened)(void *userData, bool opened, OH_MIDIDevice *device, OH_MIDIDeviceInformation info) | Callback for the result of asynchronously opening a BLE device.<br> This callback is invoked when the BLE device open attempt finishes, either successfully or with a failure.<br>**Since**: 24 |

## Enum type description

### OH_MIDIStatusCode

```c
enum OH_MIDIStatusCode
```

**Description**

MIDI status code enumeration.

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_MIDI_STATUS_OK = 0 |  Operation successful.<br>**Since**: 24 |
| OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT = 35500001 |  Invalid parameter (e.g., null pointer).<br>**Since**: 24 |
| OH_MIDI_STATUS_GENERIC_IPC_FAILURE = 35500002 |  IPC communication failure.<br>**Since**: 24 |
| OH_MIDI_STATUS_INVALID_CLIENT = 35500003 |  Invalid client handle.<br>**Since**: 24 |
| OH_MIDI_STATUS_INVALID_DEVICE_HANDLE = 35500004 |  Invalid device handle.<br>**Since**: 24 |
| OH_MIDI_STATUS_INVALID_PORT = 35500005 |  Invalid port index.<br>**Since**: 24 |
| OH_MIDI_STATUS_WOULD_BLOCK = 35500006 |  The send buffer is transiently full. Indicates that the shared memory buffer currently lacks space. Returned by non-blocking send when a message cannot fit in the buffer. Retry the operation with a short delay (recommended: 10ms).<br>**Since**: 24 |
| OH_MIDI_STATUS_TIMEOUT = 35500007 |  Operation can not be handled in a reasonable time.<br>**Since**: 24 |
| OH_MIDI_STATUS_TOO_MANY_OPEN_DEVICES = 35500008 |  The client has reached the maximum number of open devices allowed. To open a new device, the client must close an existing one first.<br>**Since**: 24 |
| OH_MIDI_STATUS_TOO_MANY_OPEN_PORTS = 35500009 |  The client has reached the maximum number of open ports allowed. To open a new port, the client must close an existing one first.<br>**Since**: 24 |
| OH_MIDI_STATUS_DEVICE_ALREADY_OPEN = 35500010 |  The client has already opened this device.<br>**Since**: 24 |
| OH_MIDI_STATUS_PORT_ALREADY_OPEN = 35500011 |  The client has already opened this port.<br>**Since**: 24 |
| OH_MIDI_STATUS_TOO_MANY_CLIENTS = 35500012 |  The system-wide or per-application limit for MIDI clients has been reached. The application should wait or release other resources before retrying.<br>**Since**: 24 |
| OH_MIDI_STATUS_PERMISSION_DENIED = 35500013 |  Permission denied. Returned when the application attempts to perform an operation without the required permission (e.g., Bluetooth for BLE devices).<br>**Since**: 24 |
| OH_MIDI_STATUS_SERVICE_DIED = 35500014 |  The MIDI system service has died or disconnected. The client must be destroyed and recreated.<br>**Since**: 24 |
| OH_MIDI_STATUS_SYSTEM_ERROR = 35500100 |  System-level errors such as insufficient memory or system service failure.<br>**Since**: 24 |

### OH_MIDIPortDirection

```c
enum OH_MIDIPortDirection
```

**Description**

Port direction enumeration.

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_MIDI_PORT_DIRECTION_INPUT = 0 | Input port (Device -> Host).<br>**Since**: 24 |
| OH_MIDI_PORT_DIRECTION_OUTPUT = 1 | Output port (Host -> Device).<br>**Since**: 24 |

### OH_MIDIProtocol

```c
enum OH_MIDIProtocol
```

**Description**

MIDI transport protocol semantics.

> **Note**:
>
> CRITICAL**: The SDK always uses UMP (Universal MIDI Packet) format for data transfer, regardless of the selected protocol. This enum defines the "Behavior" and "Semantics" of the connection, not the data structure.

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_MIDI_PROTOCOL_1_0 = 1 | Legacy MIDI 1.0 Semantics. Behavior: - The service expects UMP packets strictly compatible with MIDI 1.0. - **MT 0x0**: Utility Messages (e.g., Timestamps). - **MT 0x1**: System Real Time and System Common Messages. - **MT 0x2**: MIDI 1.0 Channel Voice Messages (32-bit). - **MT 0x3**: Data Messages (64-bit) used for SysEx (7-bit payload). - If the target hardware is MIDI 1.0: The service converts UMP back to byte stream (F0...F7). - If the target hardware is MIDI 2.0: The service sends these packets as-is (encapsulated MIDI 1.0).<br>**Since**: 24 |
| OH_MIDI_PROTOCOL_2_0 = 2 | MIDI 2.0 Semantics. Behavior: - The service expects UMP packets leveraging MIDI 2.0 features. - **MT 0x4**: MIDI 2.0 Channel Voice Messages (64-bit, high resolution). - **MT 0x0**: Utility Messages (Timestamps). - **MT 0xD**: Flex Data Messages (128-bit, e.g., Text, Lyrics). - **MT 0xF**: UMP Stream Messages (128-bit, Endpoint Discovery, Function Blocks). - **MT 0x3 / MT 0x5**: Data Messages (64-bit or 128-bit).<br>**Since**: 24 |

### OH_MIDIDeviceType

```c
enum OH_MIDIDeviceType
```

**Description**

MIDI Device type.

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_MIDI_DEVICE_TYPE_USB = 0 | USB MIDI device.<br>**Since**: 24 |
| OH_MIDI_DEVICE_TYPE_BLE = 1 | Bluetooth Low Energy MIDI device.<br>**Since**: 24 |

### OH_MIDIDeviceChangeAction

```c
enum OH_MIDIDeviceChangeAction
```

**Description**

Device connection state change action.

**Since**: 24

| Enum item | Description |
| -- | -- |
| OH_MIDI_DEVICE_CHANGE_ACTION_CONNECTED = 0 | Device connected.<br>**Since**: 24 |
| OH_MIDI_DEVICE_CHANGE_ACTION_DISCONNECTED = 1 | Device disconnected.<br>**Since**: 24 |


## Function description

### OH_MIDICallback_OnDeviceChange()

```c
typedef void (*OH_MIDICallback_OnDeviceChange)(void *userData, OH_MIDIDeviceChangeAction action, OH_MIDIDeviceInformation deviceInfo)
```

**Description**

Callback for monitoring device connection/disconnection.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| void \*userData | The user context pointer passed to {@link #OH_MIDIClient_Create}. |
| [OH_MIDIDeviceChangeAction](capi-native-midi-base-h.md#oh_mididevicechangeaction) action | Device change action (connected/disconnected). |
| [OH_MIDIDeviceInformation](capi-ohmidi-oh-midideviceinformation.md) deviceInfo | Information of the changed device. |

### OH_MIDICallback_OnError()

```c
typedef void (*OH_MIDICallback_OnError)(void *userData, OH_MIDIStatusCode code)
```

**Description**

Callback for handling client-level errors. Invoked when a critical error occurs in the MIDI service (e.g., service crash). Applications may need to recreate the client when this occurs.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| void \*userData | The user context pointer passed to {@link #OH_MIDIClient_Create}. |
| [OH_MIDIStatusCode](capi-native-midi-base-h.md#oh_midistatuscode) code | The error code indicating the cause. |

### OH_MIDIDevice_OnReceived()

```c
typedef void (*OH_MIDIDevice_OnReceived)(void *userData, const OH_MIDIEvent *events, size_t eventCount)
```

**Description**

Callback for receiving MIDI data (Batch Processing).

> **Warning**:
>
> This callback is invoked on a high-priority system thread. Do **not** perform blocking operations, heavy computation, or I/O.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| void \*userData | The user context pointer passed to {@link #OH_MIDIDevice_OpenInputPort}. |
| [const OH_MIDIEvent](capi-ohmidi-oh-midievent.md) \*events | Pointer to the array of MIDI events received. |
| size_t eventCount | The number of events in the array. |

### OH_MIDIClient_OnDeviceOpened()

```c
typedef void (*OH_MIDIClient_OnDeviceOpened)(void *userData, bool opened, OH_MIDIDevice *device, OH_MIDIDeviceInformation info)
```

**Description**

Callback for the result of asynchronously opening a BLE device.<br> This callback is invoked when the BLE device open attempt finishes, either successfully or with a failure.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| void \*userData | The user context pointer passed to {@link #OH_MIDIClient_OpenBLEDevice}. |
| bool opened | Indicates whether the device was successfully opened. True: Device successfully opened, device handle is valid. False: Device open failed, device handle is NULL. |
| [OH_MIDIDevice](capi-ohmidi-oh-mididevicestruct.md) \*device | The handle of the opened device. If opened is true, the application MUST close this handle using {@link #OH_MIDIClient_CloseDevice} when it is no longer needed. If opened is false, this parameter is NULL. |
| [OH_MIDIDeviceInformation](capi-ohmidi-oh-midideviceinformation.md) info | The information of the opened device. Note: This object is valid ONLY within the scope of this callback. If you need to persist specific attributes (e.g., ID or Name), copy them. |


