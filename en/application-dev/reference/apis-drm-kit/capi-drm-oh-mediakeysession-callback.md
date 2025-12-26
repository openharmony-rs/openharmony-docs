# OH_MediaKeySession_Callback
<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qin_wei_jie-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_MediaKeySession_Callback {...} OH_MediaKeySession_Callback
```

## Overview

The OH_MediaKeySession_Callback struct describes the callbacks for media key session events such as key expiration and key changes. It provides a MediaKeySession instance, making it suitable for multi-session decryption scenarios.

**Since**: 12

**Related module**: [Drm](capi-drm.md)

**Header file**: [native_mediakeysession.h](capi-native-mediakeysession-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [OH_MediaKeySession_EventCallback](capi-native-mediakeysession-h.md#oh_mediakeysession_eventcallback) eventCallback | Callback for standard events, such as key expiration.|
| [OH_MediaKeySession_KeyChangeCallback](capi-native-mediakeysession-h.md#oh_mediakeysession_keychangecallback) keyChangeCallback | Callback for media key change events.|
