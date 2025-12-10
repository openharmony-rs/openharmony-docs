# MediaKeySession_Callback
<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qin_wei_jie-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct MediaKeySession_Callback {...} MediaKeySession_Callback
```

## Overview

The MediaKeySession_Callback struct describes the callbacks for media key session events such as key expiration and key changes. It does not provide a MediaKeySession instance, making it suitable for single-session decryption scenarios.

**Since**: 11

**Related module**: [Drm](capi-drm.md)

**Header file**: [native_mediakeysession.h](capi-native-mediakeysession-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [MediaKeySession_EventCallback](capi-native-mediakeysession-h.md#mediakeysession_eventcallback) eventCallback | Callback for standard events, such as key expiration.|
| [MediaKeySession_KeyChangeCallback](capi-native-mediakeysession-h.md#mediakeysession_keychangecallback) keyChangeCallback | Callback for media key change events.|
