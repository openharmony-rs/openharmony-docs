# Input_DeviceInfo

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=574e1b97c419a831e3ff5b620b1254fe667a5306 translatedAt=2026-06-12T02:19:53.418Z pushedAt=2026-06-12T02:35:26.964Z -->

```c
typedef struct Input_DeviceInfo Input_DeviceInfo
```

## Overview

Defines input device information, which is used to describe the basic information and capability characteristics of an input device, including attributes such as the device type and device ID. You can use this struct to obtain and manage detailed information about input devices, facilitating device identification and configuration management.

**Since**: 13

**Related module**: [input](capi-input.md)

**Header file**: [oh_input_manager.h](capi-oh-input-manager-h.md)

**Related APIs**:

| Name| Description|
| -- | -- |
| [OH_Input_CreateDeviceInfo](capi-oh-input-manager-h.md#oh_input_createdeviceinfo) | Creates a **deviceInfo** object. You can call [OH_Input_DestroyDeviceInfo](capi-oh-input-manager-h.md#oh_input_destroydeviceinfo) to destroy a **deviceInfo** object.|
| [OH_Input_DestroyDeviceInfo](capi-oh-input-manager-h.md#oh_input_destroydeviceinfo) | Destroys a **deviceInfo** object.|