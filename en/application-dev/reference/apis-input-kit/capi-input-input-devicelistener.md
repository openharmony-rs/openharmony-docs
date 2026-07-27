# Input_DeviceListener

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=574e1b97c419a831e3ff5b620b1254fe667a5306 translatedAt=2026-06-12T02:19:38.071Z pushedAt=2026-06-12T02:43:05.470Z -->

```c
typedef struct Input_DeviceListener {...} Input_DeviceListener
```

## Overview

Defines the struct for listening for device hot swapping. It is applicable to applications that need to respond to input device connection and disconnection in real time, such as games and music players. By listening for device hot swapping events, applications can update the input status in a timely manner, improving user experience and avoiding exceptions caused by device disconnection.

**Since**: 13

**Related module**: [input](capi-input.md)

**Header file**: [oh_input_manager.h](capi-oh-input-manager-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [Input_DeviceAddedCallback()](#input_deviceaddedcallback) deviceAddedCallback | Defines a callback used to receive device hot-plug events.|
| [Input_DeviceRemovedCallback()](#input_deviceremovedcallback) deviceRemovedCallback | Defines a callback used to receive device hot-unplug events.|

### Member Functions

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [typedef void (\*Input_DeviceAddedCallback)(int32_t deviceId)](#input_deviceaddedcallback) | Input_DeviceAddedCallback() | Callback used to receive input device hot-plug events.|
| [typedef void (\*Input_DeviceRemovedCallback)(int32_t deviceId)](#input_deviceremovedcallback) | Input_DeviceRemovedCallback() | Callback used to receive input device hot-unplug events.|

## Member Function Description

### Input_DeviceAddedCallback()

```c
typedef void (*Input_DeviceAddedCallback)(int32_t deviceId)
```

**Description**

Callback used to receive input device hot-plug events.

**Since**: 13

**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t deviceId | Unique ID of the input device. If a physical device is repeatedly plugged and unplugged or restarted, its ID may change.|

### Input_DeviceRemovedCallback()

```c
typedef void (*Input_DeviceRemovedCallback)(int32_t deviceId)
```

**Description**

Callback used to receive input device hot-unplug events.

**Since**: 13

**Parameters**

| Parameter| Description|
| -- | -- |
| int32_t deviceId | Unique ID of the input device. If a physical device is repeatedly plugged and unplugged or restarted, its ID may change.|