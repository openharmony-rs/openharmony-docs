# Input_DeviceListener

```c
typedef struct Input_DeviceListener {...} Input_DeviceListener
```

## 概述

Defines the struct for listening for device hot swapping. It is applicable to applications that need torespond to input device connection and disconnection in real time, such as games and music players. By listening fordevice hot swapping events, applications can update the input status in a timely manner, improving user experienceand avoiding exceptions caused by device disconnection.

**起始版本：** 13

**相关模块：** [input](capi-input.md)

**所在头文件：** [oh_input_manager.h](capi-oh-input-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [Input_DeviceAddedCallback](capi-oh-input-manager-h.md#input_deviceaddedcallback) deviceAddedCallback | Callback for device addition events |
| [Input_DeviceRemovedCallback](capi-oh-input-manager-h.md#input_deviceremovedcallback) deviceRemovedCallback | Callback for device removal events |


