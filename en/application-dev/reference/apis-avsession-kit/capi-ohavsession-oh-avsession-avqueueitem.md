# OH_AVSession_AVQueueItem
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @ccfriend; @devil_red-->
<!--Designer: @ccfriend-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct {...} OH_AVSession_AVQueueItem
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
