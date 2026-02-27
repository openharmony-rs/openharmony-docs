# Input_DeviceListener

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct Input_DeviceListener {...} Input_DeviceListener
```

## Overview

Defines a listener for device hot swap events.

**Since**: 13

**Related module**: [input](capi-input.md)

**Header file**: [oh_input_manager.h](capi-oh-input-manager-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| Input_DeviceAddedCallback deviceAddedCallback | Defines a callback used to receive device insertion events.|
| Input_DeviceRemovedCallback deviceRemovedCallback | Defines a callback used to receive device removal events.|
