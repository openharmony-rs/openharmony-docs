# AVSession_OutputDeviceInfo
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @ccfriend; @devil_red-->
<!--Designer: @ccfriend-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct AVSession_OutputDeviceInfo {...}
```

## Overview

Defines a struct for the target device information.

**Since:** 23

**Related module:** [OHAVSession](capi-ohavsession.md)

**Header file:** [native_deviceinfo.h](capi-native-deviceinfo-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t size | Size of the device information array.|
| [AVSession_DeviceInfo](capi-ohavsession-avsession-deviceinfo.md) **deviceInfos | Double pointer to the device information array.|
