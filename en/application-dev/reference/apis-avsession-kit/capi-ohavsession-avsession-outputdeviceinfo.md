# AVSession_OutputDeviceInfo
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_7KSyM10J; @devil_red-->
<!--Designer: @gcw_7KSyM10J-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct AVSession_OutputDeviceInfo {...} AVSession_OutputDeviceInfo
```

## Overview

Defines information about the output device.

**Since:** 23

**Related module:** [OHAVSession](capi-ohavsession.md)

**Header file:** [native_deviceinfo.h](capi-native-deviceinfo-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t size | Size of the device information array, indicating the number of elements in the **deviceInfos** array.|
| [AVSession_DeviceInfo](capi-ohavsession-avsession-deviceinfo.md) **deviceInfos | Pointer to the device information array. The array length is specified by the **size** field.|
