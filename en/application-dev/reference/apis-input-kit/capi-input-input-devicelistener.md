# Input_DeviceListener

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=3ac9506947b9a687415be23e968a5dc9053205f5 translatedAt=2026-09-01T01:18:20.144Z pushedAt=2026-09-03T06:08:24.318Z -->

```c
typedef struct Input_DeviceListener {
    // ...
} Input_DeviceListener
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
| [Input_DeviceAddedCallback](capi-oh-input-manager-h.md#input_deviceaddedcallback) deviceAddedCallback | Defines a callback used to receive device hot-plug events. |
| [Input_DeviceRemovedCallback](capi-oh-input-manager-h.md#input_deviceremovedcallback) deviceRemovedCallback | Defines a callback used to receive device hot-unplug events. |