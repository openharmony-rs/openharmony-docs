# AVSession_OutputDeviceInfo
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @ccfriend; @devil_red-->
<!--Designer: @ccfriend-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=23c78283c2fbf556eb3d88353a7151aeb7aecf0d translatedAt=2026-09-01T13:07:05.895Z pushedAt=2026-09-07T10:26:21.113Z -->

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
| uint32_t size | Size of the device information array, indicating the number of elements in the **deviceInfos** array. |
| [AVSession_DeviceInfo](capi-ohavsession-avsession-deviceinfo.md) **deviceInfos | Pointer to the device information array. The array length is specified by the **size** field. |