# Using OH_MIDI for MIDI Development (C/C++)

<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @owen_creeper-->
<!--Designer: @trytocalm-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=45526eba67080b876eb51af31a33be43ae26f701 translatedAt=2026-07-13T13:17:40.357Z pushedAt=2026-07-16T13:52:38.056Z -->

## When to Use

**OH_MIDI** is the native MIDI API provided by the system. Starting from API version 24, it enables MIDI application development in C/C++. Use **OH_MIDI** when your application needs to exchange MIDI data with external MIDI devices, such as USB MIDI keyboards and Bluetooth MIDI devices. Typical use cases include the following:

- **Music creation applications**: Connect to a MIDI keyboard to receive note events in real time and trigger sound playback.

- **Music learning and education applications**: Receive performance data from a MIDI keyboard to implement features such as performance evaluation and accompaniment.

- **MIDI controller applications**: Send control messages from the application to external MIDI devices, for example, to switch instrument sounds or adjust device parameters.

- **MIDI data processing tools**: Receive, parse, and forward MIDI messages for music production or device debugging.

With **OH_MIDI**, you can implement the following functions:

- Create a MIDI client and manage the connection to the MIDI service.

- Enumerate and manage MIDI devices.

- Open and manage MIDI ports.

- Send and receive MIDI messages.

- Handle MIDI events and callbacks.

- Implement low-latency MIDI data transmission.

## Checking System Capabilities

Before developing with MIDI, call the [canIUse](../../reference/common/init.md#caniuse) API to check whether the current device supports MIDI capabilities. When **canIUse("SystemCapability.Multimedia.Audio.MIDI")** returns **true**, it indicates that the MIDI capability is available.

## Available APIs

The main APIs of **OH_MIDI** include:

- Client management: [OH_MIDIClient_Create](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_midiclient_create), [OH_MIDIClient_Destroy](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_midiclient_destroy)

- Device management: [OH_MIDIClient_GetDeviceCount](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_midiclient_getdevicecount), [OH_MIDIClient_GetDeviceInfos](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_midiclient_getdeviceinfos), [OH_MIDIClient_OpenDevice](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_midiclient_opendevice), [OH_MIDIClient_CloseDevice](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_midiclient_closedevice)

- Port management: [OH_MIDIClient_GetPortCount](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_midiclient_getportcount), [OH_MIDIClient_GetPortInfos](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_midiclient_getportinfos), [OH_MIDIDevice_OpenInputPort](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_mididevice_openinputport), [OH_MIDIDevice_OpenOutputPort](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_mididevice_openoutputport), [OH_MIDIDevice_CloseInputPort](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_mididevice_closeinputport), [OH_MIDIDevice_CloseOutputPort](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_mididevice_closeoutputport)

- Data transmission: [OH_MIDIDevice_Send](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_mididevice_send), [OH_MIDIDevice_SendSysEx](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_mididevice_sendsysex)

- Callback: [OH_MIDICallback_OnDeviceChange](../../reference/apis-audio-kit/capi-native-midi-base-h.md#oh_midicallback_ondevicechange), [OH_MIDIDevice_OnReceived](../../reference/apis-audio-kit/capi-native-midi-base-h.md#oh_mididevice_onreceived)

## Preparations

Before using **OH_MIDI** APIs, you need to complete the following preparations:

- Link dynamic libraries in the CMake script.

  <!-- @[ohmidi_cmake](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/Midi/entry/src/main/cpp/CMakeLists.txt) -->

  ``` Text
  target_link_libraries(entry PUBLIC
      libace_napi.z.so
      libohmidi.so
      libhilog_ndk.z.so
  )
  ```

- Add header files.

  ``` C++
  #include "native_midi.h"
  #include "native_midi_base.h"
  #include <hilog/log.h>
  ```

## Declaring Permissions

The permission requirements for MIDI functionality vary depending on the usage scenario.

**Scenario 1: Using only USB MIDI devices**

No additional permission declaration is required.

**Scenario 2: Discovering and connecting BLE MIDI devices**

Declare the Bluetooth permission in `module.json5`:

```json
"requestPermissions": [
    {
        "name": "ohos.permission.ACCESS_BLUETOOTH",
        "reason": "$string:bluetooth_permission_reason"
    }
]
```

## How to Develop

### Creating a MIDI Client

Creating a MIDI client is the first step in using the MIDI API.

The client serves as the connection entry point between the application and the MIDI system service, responsible for managing all interactions with the MIDI service. Before creating the client, you need to prepare the callback structure:

The system has defined the [OH_MIDICallbacks](../../reference/apis-audio-kit/capi-ohmidi-oh-midicallbacks.md) structure. You need to implement the callback functions within it:

- **onDeviceChange**: Automatically called by the system when a MIDI device is connected or disconnected. You can handle device connection and removal logic in this callback.

- **onError**: Called when an error occurs in the MIDI service. You can handle error logging and exception recovery logic in this callback, such as recreating the client.

Create a MIDI client instance by calling the [OH_MIDIClient_Create](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_midiclient_create) API, passing in the callback structure and user data.

<!-- @[create_midi_client](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/Midi/entry/src/main/cpp/napi_init.cpp) -->  

``` C++
// Create the MIDI client.
static napi_value CreateMIDIClient(napi_env env, napi_callback_info info)
{
    // ...
    std::lock_guard<std::mutex> lock(g_midiMutex);
    // ...
    OH_MIDIStatusCode status = OH_MIDIClient_Create(&g_midiClient, g_midiCallbacks, nullptr);
    // ...
}
```

### Destroying the MIDI Client

When the MIDI functionality is no longer needed, the client should be destroyed to release resources. Before destroying, all opened devices must be closed first.

Destroy the MIDI client instance by calling [OH_MIDIClient_Destroy](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_midiclient_destroy) to release all associated resources.

<!-- @[cleanup_destroy_client](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/Midi/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value DestroyMIDIClient(napi_env env, napi_callback_info info)
{
    // ...
    std::lock_guard<std::mutex> lock(g_midiMutex);

    if (g_midiClient != nullptr) {
        CloseAllOpenedDevices();
        OH_MIDIClient_Destroy(g_midiClient);
        g_midiClient = nullptr;
    }
    CleanupAllPortContexts();

    // ...
}
```

### Enumerating MIDI Devices

After creating the client, you can enumerate the MIDI devices currently available in the system. Device enumeration involves two steps:

1. Obtain the device count: Call [OH_MIDIClient_GetDeviceCount](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_midiclient_getdevicecount) to obtain the number of currently connected devices.

2. Obtain device information: Allocate a sufficiently large buffer and call [OH_MIDIClient_GetDeviceInfos](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_midiclient_getdeviceinfos) to populate detailed device information.

> **NOTE**
>
> - If the application has not obtained the Bluetooth permission (**ohos.permission.ACCESS_BLUETOOTH**), Bluetooth MIDI devices will not be included in the enumeration results.
> - After the application obtains the Bluetooth permission, it needs to re-enumerate MIDI devices to obtain the connected Bluetooth MIDI devices.

Obtain the device count through [OH_MIDIClient_GetDeviceCount](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_midiclient_getdevicecount), and then obtain detailed device information through [OH_MIDIClient_GetDeviceInfos](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_midiclient_getdeviceinfos).

<!-- @[get_device_infos](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/Midi/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value GetDeviceInfos(napi_env env, napi_callback_info info)
{
    std::lock_guard<std::mutex> lock(g_midiMutex);
    // ...

    size_t count = 0;
    OH_MIDIStatusCode status = OH_MIDIClient_GetDeviceCount(g_midiClient, &count);
    // ...
    std::vector<OH_MIDIDeviceInformation> devices(count);
    size_t actualCount = 0;
    status = OH_MIDIClient_GetDeviceInfos(g_midiClient, devices.data(), count, &actualCount);
    // ...
}
```

### Opening a MIDI Device

A device must be opened before data transmission can occur. The opening method varies depending on the device type: USB MIDI devices are opened synchronously through [OH_MIDIClient_OpenDevice](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_midiclient_opendevice), while BLE MIDI devices are opened asynchronously through [OH_MIDIClient_OpenBLEDevice](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_midiclient_openbledevice).

**Opening a USB MIDI Device (Synchronous)**

Call [OH_MIDIClient_OpenDevice](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_midiclient_opendevice) to synchronously open a USB MIDI device. Pass the device ID to obtain a device handle.

<!-- @[open_device](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/Midi/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value OpenDevice(napi_env env, napi_callback_info info)
{
    size_t argc = 1;
    napi_value args[1] = {nullptr};
    napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);

    int64_t deviceId = 0;
    napi_get_value_int64(env, args[0], &deviceId);
    std::lock_guard<std::mutex> lock(g_midiMutex);
    // ...
    OH_MIDIDevice *device = nullptr;
    OH_MIDIStatusCode status = OH_MIDIClient_OpenDevice(g_midiClient, deviceId, &device);
    if (status == OH_MIDI_STATUS_OK && device != nullptr) {
        g_openedDevices[deviceId] = device;
        OH_LOG_INFO(LOG_APP, "[OpenDevice] device stored, total opened devices=%{public}zu", g_openedDevices.size());
    }
    // ...
}
```

**Opening a BLE MIDI Device (Asynchronous)**

Call [OH_MIDIClient_OpenBLEDevice](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_midiclient_openbledevice) to open a BLE MIDI device asynchronously.

The BLE device address can be obtained through the following methods:

1. BLE scan: Use the Bluetooth API to scan for MIDI BLE devices.

2. History: Load previously connected device addresses from persistent storage.

3. User input: Allow the user to manually enter a MAC address.

MIDI BLE devices can be filtered and identified by the service UUID `03B80E5A-EDE8-4B33-A751-6CE34EC4C700`.

Call [OH_MIDIClient_OpenBLEDevice](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_midiclient_openbledevice) to open a BLE MIDI device asynchronously. Pass the device MAC address and a result callback.

<!-- @[open_ble_device](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/Midi/entry/src/main/cpp/napi_init.cpp) -->  

``` C++
// Asynchronously open the BLE device.
static napi_value OpenBLEDevice(napi_env env, napi_callback_info info)
{
    size_t argc = 2;
    napi_value args[2] = {nullptr};
    napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);

    // Obtain the device address.
    size_t addrLen = 0;
    napi_get_value_string_utf8(env, args[0], nullptr, 0, &addrLen);
    std::string deviceAddr(addrLen, '\0');
    napi_get_value_string_utf8(env, args[0], &deviceAddr[0], addrLen + 1, &addrLen);

    // ...

    std::lock_guard<std::mutex> lock(g_midiMutex);

    // ...
    OH_MIDIStatusCode status = OH_MIDIClient_OpenBLEDevice(g_midiClient, deviceAddr.c_str(),
                                                           OnBLEDeviceOpened, nullptr);
    // ...
}
```

Obtain the BLE device open result through the [OH_MIDIClient_OnDeviceOpened](../../reference/apis-audio-kit/capi-native-midi-base-h.md#oh_midiclient_ondeviceopened) callback, and obtain the device handle and device information in the callback.

<!-- @[ble_device_opened_callback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/Midi/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static void OnBLEDeviceOpened(void *userData, bool opened, OH_MIDIDevice *device, OH_MIDIDeviceInformation info)
{
    std::string deviceAddr = info.deviceAddress;
    // ...
}
```

> **NOTE**
>
> - BLE device connection is asynchronous, and the result is returned through a callback.
> - The callback is executed in a non-main thread. If you need to update the UI, use a thread safety mechanism.
> - After a successful connection, subsequent port operations should be performed in the callback.
> - Use `OH_MIDIClient_CloseDevice` to close the device.

### Closing a MIDI Device

Close an opened MIDI device and release device resources through [OH_MIDIClient_CloseDevice](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_midiclient_closedevice).

<!-- @[close_device](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/Midi/entry/src/main/cpp/napi_init.cpp) -->  

``` C++
static napi_value CloseDevice(napi_env env, napi_callback_info info)
{
    // ...
    std::lock_guard<std::mutex> lock(g_midiMutex);
    // ...
    auto it = g_openedDevices.find(deviceId);
    if (it != g_openedDevices.end()) {
        // Clean up all InputPortContext instances for the device.
        CleanupInputPortContextsForDevice(deviceId);
        OH_MIDIStatusCode status = OH_MIDIClient_CloseDevice(g_midiClient, it->second);
        g_openedDevices.erase(it);
        // ...
    } else {
        // ...
    }

    // ...
    return result;
}
```

### Obtaining Port Information

After opening the device, you need to obtain its port information and open the input or output port to send or receive MIDI data.

Each MIDI device may provide multiple ports, and each port has a clear direction (input or output). You need to enumerate all ports first, find the corresponding input port and output port based on application requirements, and then open them separately.

Obtain the port count through [OH_MIDIClient_GetPortCount](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_midiclient_getportcount), and then obtain detailed port information through [OH_MIDIClient_GetPortInfos](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_midiclient_getportinfos).

<!-- @[get_port_infos](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/Midi/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value GetPortInfos(napi_env env, napi_callback_info info)
{
    size_t argc = 1;
    napi_value args[1] = {nullptr};
    napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);

    int64_t deviceId = 0;
    napi_get_value_int64(env, args[0], &deviceId);
    // ...

    std::lock_guard<std::mutex> lock(g_midiMutex);

    // ...

    size_t count = 0;
    OH_MIDIStatusCode status = OH_MIDIClient_GetPortCount(g_midiClient, deviceId, &count);
    // ...

    std::vector<OH_MIDIPortInformation> ports(count);
    size_t actualCount = 0;
    status = OH_MIDIClient_GetPortInfos(g_midiClient, deviceId, ports.data(), count, &actualCount);
    // ...
}
```

### Managing MIDI Ports

**Opening an Input Port**

To receive MIDI messages, you need to open an input port and register a receiving callback function. When the device sends MIDI data, the callback function will be invoked.

The callback runs in a separate thread. Use a mutex or another synchronization mechanism to ensure thread safety. The `events` data is valid only for the duration of the callback. To retain the data, make a copy before the callback returns.

Receive MIDI data through the [OH_MIDIDevice_OnReceived](../../reference/apis-audio-kit/capi-native-midi-base-h.md#oh_mididevice_onreceived) callback, and obtain the event array and its data within the callback.

<!-- @[midi_received_callback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/Midi/entry/src/main/cpp/napi_init.cpp) -->  

``` C++
static void OnMIDIReceived(void *userData, const OH_MIDIEvent *events, size_t eventCount)
{
    // userData points to InputPortContext.
    InputPortContext* context = static_cast<InputPortContext*>(userData);
    // ...
}
```

Open an input port through [OH_MIDIDevice_OpenInputPort](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_mididevice_openinputport). Pass the [OH_MIDIPortDescriptor](../../reference/apis-audio-kit/capi-ohmidi-oh-midiportdescriptor.md) structure to configure port parameters and register the data reception callback.

<!-- @[open_input_port](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/Midi/entry/src/main/cpp/napi_init.cpp) -->  

``` C++
static napi_value OpenInputPort(napi_env env, napi_callback_info info)
{
    InputPortArgs args = ParseInputPortArgs(env, info);

    std::lock_guard<std::mutex> lock(g_midiMutex);

    napi_value result;
    auto it = g_openedDevices.find(args.deviceId);
    if (g_midiClient == nullptr || it == g_openedDevices.end()) {
        OH_LOG_ERROR(LOG_APP, "[OpenInputPort] client is null or device not opened");
        napi_create_int32(env, static_cast<int32_t>(OH_MIDI_STATUS_INVALID_DEVICE_HANDLE), &result);
        return result;
    }

    // Construct the port descriptor.
    OH_MIDIPortDescriptor descriptor;
    descriptor.portIndex = args.portIndex;
    descriptor.protocol = static_cast<OH_MIDIProtocol>(args.protocol);

    // Create an input port context for thread-safe callback handling.
    auto context = std::make_shared<InputPortContext>(args.deviceId, args.portIndex);

    OH_MIDIStatusCode status = OH_MIDIDevice_OpenInputPort(it->second, descriptor, OnMIDIReceived, context.get());
    // ...
}
```

**Closing an Input Port**

Call [OH_MIDIDevice_CloseInputPort](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_mididevice_closeinputport) to close an opened input port. After the port is closed, it will no longer receive MIDI messages, and the registered callback function will no longer be called.

<!-- @[close_input_port](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/Midi/entry/src/main/cpp/napi_init.cpp) -->  

``` C++
// Close the input port.
static napi_value CloseInputPort(napi_env env, napi_callback_info info)
{
    size_t argc = 2;
    napi_value args[2] = {nullptr};
    napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);

    int64_t deviceId = 0;
    napi_get_value_int64(env, args[0], &deviceId);

    uint32_t portIndex = 0;
    napi_get_value_uint32(env, args[1], &portIndex);

    OH_LOG_INFO(LOG_APP, "[CloseInputPort] ++enter, deviceId=%{public}lld, portIndex=%{public}u",
                (long long)deviceId, portIndex);

    std::lock_guard<std::mutex> lock(g_midiMutex);

    napi_value result;
    auto it = g_openedDevices.find(deviceId);
    if (g_midiClient == nullptr || it == g_openedDevices.end()) {
        OH_LOG_ERROR(LOG_APP, "[CloseInputPort] client is null or device not opened");
        napi_create_int32(env, static_cast<int32_t>(OH_MIDI_STATUS_INVALID_DEVICE_HANDLE), &result);
        return result;
    }

    OH_MIDIStatusCode status = OH_MIDIDevice_CloseInputPort(it->second, portIndex);

    // Clean up the input port context.
    auto key = std::make_pair(deviceId, portIndex);
    auto contextIt = g_inputPortContexts.find(key);
    if (contextIt != g_inputPortContexts.end()) {
        if (contextIt->second != nullptr) {
            contextIt->second->Stop();
        }
        g_inputPortContexts.erase(contextIt);
    }
    // ...
}
```

**Opening an Output Port**

Call [OH_MIDIDevice_OpenOutputPort](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_mididevice_openoutputport) to open an output port. Pass the [OH_MIDIPortDescriptor](../../reference/apis-audio-kit/capi-ohmidi-oh-midiportdescriptor.md) structure to configure port parameters and protocols.

<!-- @[open_output_port](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/Midi/entry/src/main/cpp/napi_init.cpp) -->  

``` C++
static napi_value OpenOutputPort(napi_env env, napi_callback_info info)
{
    size_t argc = 3;
    napi_value args[3] = {nullptr};
    napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);

    int64_t deviceId = 0;
    napi_get_value_int64(env, args[0], &deviceId);

    uint32_t portIndex = 0;
    napi_get_value_uint32(env, args[1], &portIndex);

    int32_t protocol = static_cast<int32_t>(MIDI_PROTOCOL_1_0); // Use the MIDI 1.0 protocol by default.
    napi_get_value_int32(env, args[MIDI_ARG_INDEX_2], &protocol);

    OH_LOG_INFO(LOG_APP, "[OpenOutputPort] ++enter, deviceId=%{public}lld, portIndex=%{public}u, protocol=%{public}d",
                (long long)deviceId, portIndex, protocol);

    std::lock_guard<std::mutex> lock(g_midiMutex);

    napi_value result;
    auto it = g_openedDevices.find(deviceId);
    if (g_midiClient == nullptr || it == g_openedDevices.end()) {
        OH_LOG_ERROR(LOG_APP, "[OpenOutputPort] client is null or device not opened");
        napi_create_int32(env, static_cast<int32_t>(OH_MIDI_STATUS_INVALID_DEVICE_HANDLE), &result);
        return result;
    }

    OH_MIDIPortDescriptor descriptor;
    descriptor.portIndex = portIndex;
    descriptor.protocol = static_cast<OH_MIDIProtocol>(protocol);
    
    OH_MIDIStatusCode status = OH_MIDIDevice_OpenOutputPort(it->second, descriptor);
    // ...
}
```

**Closing an Output Port**

Call [OH_MIDIDevice_CloseOutputPort](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_mididevice_closeoutputport) to close an opened output port. After the port is closed, MIDI messages can no longer be sent through this port.

<!-- @[close_output_port](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/Midi/entry/src/main/cpp/napi_init.cpp) -->  

``` C++
// Close the output port.
static napi_value CloseOutputPort(napi_env env, napi_callback_info info)
{
    size_t argc = 2;
    napi_value args[2] = {nullptr};
    napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);

    int64_t deviceId = 0;
    napi_get_value_int64(env, args[0], &deviceId);

    uint32_t portIndex = 0;
    napi_get_value_uint32(env, args[1], &portIndex);

    OH_LOG_INFO(LOG_APP, "[CloseOutputPort] ++enter, deviceId=%{public}lld, portIndex=%{public}u",
                (long long)deviceId, portIndex);

    std::lock_guard<std::mutex> lock(g_midiMutex);

    napi_value result;
    auto it = g_openedDevices.find(deviceId);
    if (g_midiClient == nullptr || it == g_openedDevices.end()) {
        OH_LOG_ERROR(LOG_APP, "[CloseOutputPort] client is null or device not opened");
        napi_create_int32(env, static_cast<int32_t>(OH_MIDI_STATUS_INVALID_DEVICE_HANDLE), &result);
        return result;
    }
    OH_MIDIStatusCode status = OH_MIDIDevice_CloseOutputPort(it->second, portIndex);
    // Remove the protocol information of this output port.
    if (status == OH_MIDI_STATUS_OK) {
        auto key = std::make_pair(deviceId, portIndex);
        g_outputPortProtocols.erase(key);
    }
    // ...
}
```

### Sending MIDI Messages

To send MIDI messages, you need to first construct data in the Universal MIDI Packet (UMP) format, and then send it through [OH_MIDIDevice_Send](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_mididevice_send). UMP is the unified packet format used by the MIDI 2.0.

**Sending Custom MIDI Messages**

Construct an array of [OH_MIDIEvent](../../reference/apis-audio-kit/capi-ohmidi-oh-midievent.md) events, and send MIDI messages through [OH_MIDIDevice_Send](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_mididevice_send).

<!-- @[send_midi](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/Midi/entry/src/main/cpp/napi_init.cpp) -->  

``` C++
static napi_value SendMIDI(napi_env env, napi_callback_info info)
{
    size_t argc = 3;
    napi_value args[3] = {nullptr};
    napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);

    int64_t deviceId = 0;
    napi_get_value_int64(env, args[0], &deviceId);
    uint32_t portIndex = 0;
    napi_get_value_uint32(env, args[1], &portIndex);

    OH_LOG_DEBUG(LOG_APP, "[SendMIDI] deviceId=%{public}lld, portIndex=%{public}u", (long long)deviceId, portIndex);

    bool isArray = false;
    napi_is_array(env, args[MIDI_ARG_INDEX_2], &isArray);
    if (!isArray) {
        napi_value result;
        napi_create_int32(env, static_cast<int32_t>(OH_MIDI_STATUS_GENERIC_INVALID_ARGUMENT), &result);
        return result;
    }

    std::vector<OH_MIDIEvent> events;
    std::vector<std::vector<uint32_t>> eventDataBuffers;
    ParseMIDIEventsFromArray(env, args[MIDI_ARG_INDEX_2], events, eventDataBuffers);
    uint32_t eventCount = static_cast<uint32_t>(events.size());

    std::lock_guard<std::mutex> lock(g_midiMutex);
    napi_value result;
    auto it = g_openedDevices.find(deviceId);
    if (g_midiClient == nullptr || it == g_openedDevices.end()) {
        napi_create_int32(env, static_cast<int32_t>(OH_MIDI_STATUS_INVALID_DEVICE_HANDLE), &result);
        return result;
    }

    uint32_t eventsWritten = 0;
    OH_MIDIStatusCode status = OH_MIDIDevice_Send(it->second, portIndex, events.data(), eventCount, &eventsWritten);
    napi_create_object(env, &result);
    napi_value statusValue;
    napi_create_int32(env, static_cast<int32_t>(status), &statusValue);
    napi_set_named_property(env, result, "status", statusValue);
    napi_value writtenValue;
    napi_create_uint32(env, eventsWritten, &writtenValue);
    napi_set_named_property(env, result, "eventsWritten", writtenValue);
    return result;
```

**UMP Format Description**

**OH_MIDI** mandates the use of the UMP format. Common MIDI 1.0 channel messages (MT=0x2, 32-bit) are constructed as follows.

| Bit | Field | Description |
|---------|------|------|
| 31-28 | MT | Message type. The value is `0x2` for MIDI 1.0 Channel Voice messages. |
| 27-24 | Group | Reserved. Set this field to `0`. |
| 23-20 | Status | Status code, for example, `0x9` for Note On and `0x8` for Note Off. |
| 19-16 | Channel | Channel number, ranging from `0` to `15`. |
| 15-8 | Data1 | First data byte, such as the note number. |
| 7-0 | Data2 | Second data byte, such as the velocity. |

**Examples of Constructing Common MIDI UMP Messages**

<!-- @[ump_helper_functions](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/Midi/entry/src/main/cpp/napi_init.cpp) --> 

``` C++
// Build a MIDI 1.0 Note On UMP message (a 32-bit unsigned integer).
static void BuildMIDI1NoteOn(uint32_t channel, uint32_t note, uint32_t velocity, uint32_t* umpData)
{
    // UMP format (MIDI 1.0 Channel Voice - Note On): Bits 28–31 are the message type (MT=0x2), bits 24–27 are the group (Group=0x0),
    // bits 20–23 are the status code (Status=0x9), bits 16–19 are the channel number (Channel), bits 8–15 are the note number (Note), and bits 0–7 are the velocity.
    umpData[0] = (MIDI_UMP_MT_1_0 << MIDI_UMP_WORDS_28) | (0x0 << MIDI_UMP_SHIFT_24) |
                 (MIDI_UMP_STATUS_NOTE_ON << MIDI_UMP_SHIFT_20) |
                 ((channel & MIDI_CHANNEL_MASK) << MIDI_UMP_WORDS_16) |
                 ((note & MIDI_NOTE_MASK) << MIDI_UMP_SHIFT_8) | (velocity & MIDI_NOTE_MASK);
}

// Build a MIDI 1.0 Note Off UMP (a 32-bit unsigned integer).
static void BuildMIDI1NoteOff(uint32_t channel, uint32_t note, uint32_t velocity, uint32_t* umpData)
{
    // UMP format (MIDI 1.0 Channel Voice - Note Off): Bits 28–31 are the message type (MT=0x2), bits 24–27 are the group (Group=0x0),
    // bits 20–23 are the status code (Status=0x9), bits 16–19 are the channel number (Channel), bits 8–15 are the note number (Note), and bits 0–7 are the velocity.
    umpData[0] = (MIDI_UMP_MT_1_0 << MIDI_UMP_WORDS_28) | (0x0 << MIDI_UMP_SHIFT_24) |
                 (MIDI_UMP_STATUS_NOTE_OFF << MIDI_UMP_SHIFT_20) |
                 ((channel & MIDI_CHANNEL_MASK) << MIDI_UMP_WORDS_16) |
                 ((note & MIDI_NOTE_MASK) << MIDI_UMP_SHIFT_8) | (velocity & MIDI_NOTE_MASK);
}
```

**Common CC Controller Numbers**

| Number | Name | Usage |
|------|------|------|
| 1 | Modulation Wheel | Controls vibrato depth. |
| 7 | Volume | Controls channel volume. |
| 10 | Pan | Controls the stereo pan position. |
| 11 | Expression | Controls expression. |
| 64 | Sustain Pedal | Controls the sustain pedal state. |
| 65 | Portamento | Enables or disables the portamento effect. |
| 71 | Resonance | Controls the filter resonance. |
| 74 | Filter Cutoff | Controls filter cutoff. |

**Sending System Exclusive Messages (SysEx)**

System exclusive messages are used to transmit manufacturer-specific data. Use [OH_MIDIDevice_SendSysEx](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_mididevice_sendsysex) to send SysEx messages that exceed the length of regular MIDI messages.

``` C++
// Send a large SysEx message.
void SendSysExExample(OH_MIDIDevice *device, uint32_t outputPortIndex)
{
    // Construct SysEx data.
    std::vector<uint8_t> sysexData;
    sysexData.push_back(0xF0);  // SysEx start flag.
    // Add the vendor ID and data.
    sysexData.push_back(0x43);  // Vendor ID example.
    sysexData.push_back(0x10);
    sysexData.push_back(0x4C);
    sysexData.push_back(0x00);
    sysexData.push_back(0x00);
    sysexData.push_back(0x7E);
    sysexData.push_back(0xF7);  // SysEx end flag.

    OH_MIDIStatusCode status = OH_MIDIDevice_SendSysEx(
        device, outputPortIndex, sysexData.data(), sysexData.size());

    if (status != OH_MIDI_STATUS_OK) {
        OH_LOG_ERROR(LOG_APP, "[SendSysEx] Failed: %{public}d", (int)status);
    }
}
```

### Flushing the Output Buffer

Use the [OH_MIDIDevice_FlushOutputPort](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_mididevice_flushoutputport) API to flush the output buffer of a specified port, discarding all pending messages.

<!-- @[flush_output_port](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/Midi/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value FlushOutputPort(napi_env env, napi_callback_info info)
{
    size_t argc = 2;
    napi_value args[2] = {nullptr};
    napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);

    int64_t deviceId = 0;
    napi_get_value_int64(env, args[0], &deviceId);

    uint32_t portIndex = 0;
    napi_get_value_uint32(env, args[1], &portIndex);

    std::lock_guard<std::mutex> lock(g_midiMutex);

    napi_value result;
    auto it = g_openedDevices.find(deviceId);
    if (g_midiClient == nullptr || it == g_openedDevices.end()) {
        OH_LOG_ERROR(LOG_APP, "[FlushOutputPort] client is null or device not opened");
        napi_create_int32(env, static_cast<int32_t>(OH_MIDI_STATUS_INVALID_DEVICE_HANDLE), &result);
        return result;
    }

    OH_MIDIStatusCode status = OH_MIDIDevice_FlushOutputPort(it->second, portIndex);
    // ...
}
```

### Passing Context Data Using userData

The **OH_MIDI** APIs provide **userData** parameters at three levels: client, BLE connection, and port connection. Each parameter is passed to callbacks within its corresponding scope.

| API | userData Scope | Callbacks Passed To | Typical Usage |
|-----|-------------|-------------|---------|
| `OH_MIDIClient_Create` | Client | `onDeviceChange`, `onError` | Stores global application state and device management context. |
| `OH_MIDIClient_OpenBLEDevice` | BLE connection | `OnBLEDeviceOpened` | Distinguishes concurrent connection requests and carries connection-specific context. |
| `OH_MIDIDevice_OpenInputPort` | Port connection | `OnMIDIReceived` | Provides port-specific processing context. |

> **NOTE**
>
> The three **userData** parameters are independent and can pass different context objects. After a port is closed, the corresponding callback is no longer invoked, and it is safe to release the port-level **userData** at this point.

**Usage Scenarios of userData**

| Scenario | Recommended Scope | Example Data |
|------|---------|---------|
| Handling device hot-plug events | Client | Device list, connection status |
| Logging errors | Client | Log file handle, error count |
| Collecting port event statistics | Port | Event count, timestamp recording |
| Distinguishing multiple ports | Port | Port ID, port name |
| Sharing state across callbacks | Client | Application configuration, global state |

## Notes

1. Resource management order: Closing a client automatically closes all devices and ports. It is recommended that applications close resources in the order of port -> device -> client to ensure clear code logic.

2. Thread safety: MIDI callback functions (`OnMIDIReceived`, `OnDeviceChange`, `OnError`) are executed in independent threads. Ensure thread safety by using mutexes or other synchronization mechanisms when accessing shared resources.

3. Memory safety: The `events` array and all data pointers within it in the `OnMIDIReceived` callback are temporary and valid only during this callback. Any data that needs to be retained must be copied before the callback returns. Accessing expired pointers can lead to undefined behavior (crashes or memory corruption).

4. Error handling: Check the return value and handle error conditions properly for all MIDI API calls.

5. Performance optimization: Operations exceeding 1 millisecond or blocking I/O are prohibited in callback functions to ensure real-time processing of MIDI messages is not affected. Performing time-consuming operations or blocking I/O in callbacks will severely impact the real-time processing of MIDI messages, potentially causing audio latency or frame drops.

6. UMP format: The SDK always uses the UMP format for data transmission, regardless of whether the MIDI 1.0 or MIDI 2.0 protocol is selected. Understanding the UMP message format is required to correctly construct and parse MIDI messages.

7. Buffer management: The send API is non-blocking and returns `OH_MIDI_STATUS_WOULD_BLOCK` when the buffer is full. The application should check the return value and retry sending the unfinished data when the buffer becomes available.

8. Protocol compatibility: If MIDI 2.0 is requested but the device supports only MIDI 1.0, the service automatically falls back to MIDI 1.0 and converts the messages accordingly. This conversion may reduce data precision or cause certain message types, such as SysEx messages, to be lost.

9. Permission request: Accessing Bluetooth MIDI devices requires the `ohos.permission.ACCESS_BLUETOOTH` permission.

10. Device hot-plugging: Applications should handle device connection and disconnection events, update internal state promptly, and release related resources.

11. Resource release order: `OH_MIDIClient_Destroy()` automatically closes all opened devices and ports. However, if an error occurs during initialization and the function needs to exit early, resources should be released manually in the following order:

    Step 1: Close opened ports ([OH_MIDIDevice_CloseInputPort](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_mididevice_closeinputport)/[OH_MIDIDevice_CloseOutputPort](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_mididevice_closeoutputport)). For details, see [Managing MIDI Ports](#managing-midi-ports).

    Step 2: Close opened devices ([OH_MIDIClient_CloseDevice](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_midiclient_closedevice)). For details, see [Closing a MIDI Device](#closing-a-midi-device).

    Step 3: Destroy the client ([OH_MIDIClient_Destroy](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_midiclient_destroy)). For details, see [Destroying the MIDI Client](#destroying-the-midi-client).

## Debugging and Verification

### Verifying Device Enumeration

Use the following methods to verify that MIDI devices are correctly enumerated:

1. Check the log output: Verify that information such as the device count, device names, and device types is displayed correctly.

2. Compare with the system device list: Compare the enumerated devices with the MIDI device list displayed in system settings.

3. Test device hot-plugging: Connect and disconnect a device, and check the debugging output or logs to verify that the `OnDeviceChange` callback is invoked once when the device is connected and once when it is disconnected.

### Debugging UMP Message Format

The UMP message format follows the MIDI 2.0 standard. Common UMP message types include:

- 0x2: MIDI 1.0 Channel Voice Message (32-bit)

- 0x3: MIDI 1.0 System Message (32-bit)

- 0x4: MIDI 2.0 Channel Voice Message (64-bit)

During debugging, you can output raw UMP data for verification:

``` C++
OH_LOG_DEBUG(LOG_APP, "UMP Data: 0x%{public}08X", umpData[0]);
```

### Common Debugging Tools

Log output: Use **OH_LOG** series macros to output detailed debugging information.

### Logging Recommendations

During the development phase, you are advised to add detailed logs containing timestamps, method names, parameter values, and return values at API calls, error handling, and key service logic state changes:

``` C++
#define MIDI_LOG_TAG "[MIDI]"

#define MIDI_LOGI(fmt, ...) OH_LOG_INFO(LOG_APP, MIDI_LOG_TAG "[INFO] " fmt, ##__VA_ARGS__)
#define MIDI_LOGE(fmt, ...) OH_LOG_ERROR(LOG_APP, MIDI_LOG_TAG "[ERROR] " fmt, ##__VA_ARGS__)
#define MIDI_LOGD(fmt, ...) OH_LOG_DEBUG(LOG_APP, MIDI_LOG_TAG "[DEBUG] " fmt, ##__VA_ARGS__)

// Usage example.
MIDI_LOGI("Device opened: ID=%{public}lld", targetDeviceId);
MIDI_LOGE("Failed to send message: %{public}d", result);
MIDI_LOGD("UMP Data: 0x%{public}08X", umpData[0]);
```

## FAQs

### OH_MIDI_STATUS_WOULD_BLOCK Is Returned When Sending a Message

This status indicates that the send buffer is full and cannot accept additional messages immediately. Possible causes and solutions are as follows:

1. The sending rate exceeds the buffer processing capacity: Reduce the sending rate. This commonly occurs when sending a large number of SysEx messages.

2. The buffer is not processed promptly: Consider calling [OH_MIDIDevice_FlushOutputPort](../../reference/apis-audio-kit/capi-native-midi-h.md#oh_mididevice_flushoutputport) to flush the output buffer.

3. Partial send: Check the `eventsWritten` parameter to determine how many events were actually sent.

Example:

``` C++
uint32_t eventsWritten = 0;
OH_MIDIStatusCode result = OH_MIDIDevice_Send(device, portIndex, events, count, &eventsWritten);
if (result == OH_MIDI_STATUS_WOULD_BLOCK) {
    OH_LOG_WARN(LOG_APP, "Buffer full, partial send: %{public}u/%{public}u", eventsWritten, count);

    // Option 1: Retry sending the remaining events later.
    OH_MIDIEvent *remaining = &events[eventsWritten];
    size_t remainingCount = count - eventsWritten;

    // Option 2: Discard unsent events.
    // OH_LOG_WARN(LOG_APP, "Dropped %{public}zu events", remainingCount);
}
```

### Handling Device Hot-Plug Events Correctly

Use the following process to handle device hot-plug events:

1. Listen for device changes: Handle device connection and disconnection events in `OnDeviceChange`.

2. Update the device list: Remove a device from the list promptly when it is disconnected, and re-enumerate devices when a new device is connected.

3. Release related resources: When a device is disconnected, close all ports and device handles associated with it.

4. Handle errors: Accessing a disconnected device returns an error. Check the error code, and log the error or notify the user as appropriate.

### Handling Bluetooth MIDI Device Connection Failures

Common issues that may cause a Bluetooth MIDI device connection to fail, and their solutions, are as follows:

1. Permission not declared: Ensure that the `ohos.permission.ACCESS_BLUETOOTH` permission is declared in `module.json5`.

2. Bluetooth not enabled: Ensure that system Bluetooth is enabled before connecting the device.

3. Invalid address: Verify that the Bluetooth device address is in the correct format, for example, `"AA:BB:CC:DD:EE:FF"`.

4. Connection timeout: Bluetooth connections are asynchronous and typically take 1–3 seconds to complete, depending on the device model and performance. If the target device is already connected to another host, it may take approximately 30 seconds for the connection failure result to be returned. Handle timeout-related logic in the callback to avoid blocking the main thread.

> **NOTE**
>
> - `OH_MIDIClient_OpenBLEDevice` is an asynchronous API and returns immediately after being called.
> - The connection result is notified asynchronously through a callback function, without blocking the main thread.
> - Perform subsequent operations, such as opening ports, in the callback instead of waiting synchronously.
> - In actual applications, the `device` handle needs to be saved (for example, via `userData` or a global variable) so that `OH_MIDIClient_CloseDevice` can be called later to clean up resources.

### Handling Program Crashes When Accessing Data in Callbacks

This is usually caused by thread safety or memory lifecycle issues.

1. Memory lifecycle issue: The `events` data in the `OnMIDIReceived` callback is only valid during the callback and its pointer cannot be saved for later use.

2. Thread safety issue: The callback is executed in an independent thread, and locking is required when accessing shared data.

3. The solutions are as follows:

   - Copy the required data within the callback.

   - Use a mutex to protect shared resources.

   - Avoid performing time-consuming operations within the callback.

Incorrect example:

``` C++
// Incorrect: Save the pointer for later use.
static const OH_MIDIEvent *g_savedEvents;

static void OnMIDIReceived(void *userData, const OH_MIDIEvent *events, size_t eventCount) {
    g_savedEvents = events; // Error! events is invalid after the callback ends.
}

// Accessing g_savedEvents elsewhere will cause a crash.
```

Correct example:

``` C++
// Correct: Copy the data.
struct MIDIMessage {
    std::vector<uint32_t> umpData;
};

// Use a thread-safe queue to store messages.
static void OnMIDIReceived(void *userData, const OH_MIDIEvent *events, size_t eventCount) {
    for (size_t i = 0; i < eventCount; i++) {
        // Allocate memory and copy the data.
        MIDIMessage msg;
        msg.umpData.assign(events[i].data, events[i].data + events[i].length);

        // Add the copied data to the queue (locking required).
        // enqueue_message(msg);
    }
}
```

## Complete Example

You can access the complete sample code in the sample project:

- Sample project: `https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/Midi`.

The sample project demonstrates:

- Creating and destroying a MIDI client

- Device enumeration and device change callbacks

- Opening/Closing devices (USB and BLE)

- Obtaining port information

- Opening/Closing input and output ports

- Sending MIDI messages (including Note On/Off and SysEx)

- Receiving MIDI message callbacks

- Using `userData` to pass context data

## References

- [OH_MIDI Overview (C/C++)](midi-overview.md)

- [OHMIDI API Reference](../../reference/apis-audio-kit/capi-ohmidi.md)

- [native_midi.h](../../reference/apis-audio-kit/capi-native-midi-h.md)

- [native_midi_base.h](../../reference/apis-audio-kit/capi-native-midi-base-h.md)

- [Universal Error Codes](../../reference/errorcode-universal.md)

- Bluetooth BLE development guide: [BLE Scanning and Advertising](../../connectivity/bluetooth/ble-development-guide.md)