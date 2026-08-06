# OH_MIDICallbacks

```c
typedef struct OH_MIDICallbacks {...} OH_MIDICallbacks
```

## 概述

客户端回调结构体，包含设备变化和错误处理的回调函数指针。

**起始版本：** 24

**相关模块：** [OHMIDI](capi-ohmidi.md)

**所在头文件：** [native_midi_base.h](capi-native-midi-base-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [OH_MIDICallback_OnDeviceChange](capi-native-midi-base-h.md#oh_midicallback_ondevicechange) onDeviceChange | Handler for device hotplug events.<br>**起始版本：** 24 |
| [OH_MIDICallback_OnError](capi-native-midi-base-h.md#oh_midicallback_onerror) onError | Handler for critical service errors.<br>**起始版本：** 24 |


