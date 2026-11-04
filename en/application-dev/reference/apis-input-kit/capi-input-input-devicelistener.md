# Input_DeviceListener

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=ed6f722d00b0124905c9d1808869056f41b1ffa1 translatedAt=2026-11-04T01:00:00.003Z pushedAt=2026-11-04T03:24:28.422Z nl=1 -->

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
| [Input_DeviceAddedCallback](capi-oh-input-manager-h.md#input_deviceaddedcallback) deviceAddedCallback | Defines a callback used to receive the device hot-plug event. |
| [Input_DeviceRemovedCallback](capi-oh-input-manager-h.md#input_deviceremovedcallback) deviceRemovedCallback | Defines a callback used to receive the device hot-unplug event. |
