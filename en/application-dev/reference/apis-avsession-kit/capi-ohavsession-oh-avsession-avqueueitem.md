# OH_AVSession_AVQueueItem
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_7KSyM10J; @devil_red-->
<!--Designer: @gcw_7KSyM10J-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_AVSession_AVQueueItem {...} OH_AVSession_AVQueueItem
```

## Overview

Defines a struct for the AVSession queue item.

**Since:** 23

**Related module:** [OHAVSession](capi-ohavsession.md)

**Header file:** [native_avqueueitem.h](capi-native-avqueueitem-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t itemId | Resource ID.|
| [OH_AVSession_AVMediaDescription](capi-ohavsession-oh-avsession-avmediadescription.md) *description | Media item information.|
