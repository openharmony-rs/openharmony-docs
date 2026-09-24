# Input_DeviceListener

```c
typedef struct Input_DeviceListener {...} Input_DeviceListener
```

## Overview

Defines the struct for listening for device hot swapping. It is applicable to applications that need to respond to input device connection and disconnection in real time, such as games and music players. By listening for device hot swapping events, applications can update the input status in a timely manner, improving user experience and avoiding exceptions caused by device disconnection.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**Since**: 13

**Related module**: [input](capi-input.md)

**Header file**: [oh_input_manager.h](capi-oh-input-manager-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [Input_DeviceAddedCallback](capi-oh-input-manager-h.md#input_deviceaddedcallback) deviceAddedCallback | Defines a callback used to receive device hot-plug events. |
| [Input_DeviceRemovedCallback](capi-oh-input-manager-h.md#input_deviceremovedcallback) deviceRemovedCallback | Defines a callback used to receive device hot-unplug events. |


