# AVSession_OutputDeviceInfo
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @ccfriend; @liao_qian-->
<!--Designer: @ccfriend-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->

```c
struct AVSession_OutputDeviceInfo {...}
```

## 概述

目标设备信息的定义。

**起始版本：** 23

**相关模块：** [OHAVSession](capi-ohavsession.md)

**所在头文件：** [native_deviceinfo.h](capi-native-deviceinfo-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t size | 设备信息数组的大小。 |
| [AVSession_DeviceInfo](capi-ohavsession-avsession-deviceinfo.md) **deviceInfos | 设备信息数组。 |