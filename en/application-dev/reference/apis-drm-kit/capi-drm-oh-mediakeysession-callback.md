# OH_MediaKeySession_Callback

<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @qin_wei_jie-->
<!-- md-trans-meta sourceCommit=6dec6b14cb206fe02a5ddd5033caa3930c0dd80f translatedAt=2026-11-03T13:16:11.893Z pushedAt=2026-11-04T08:46:14.014Z nl=1 -->

```c
typedef struct OH_MediaKeySession_Callback {...} OH_MediaKeySession_Callback
```

## Overview

The OH_MediaKeySession_Callback struct describes the callbacks for media key session events such as key expiration and key changes and provides a MediaKeySession instance. This struct is suitable for multi-session decryption scenarios.

**Since**: 12

**Related module**: [Drm](capi-drm.md)

**Header file**: [native_mediakeysession.h](capi-native-mediakeysession-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [OH_MediaKeySession_EventCallback](capi-native-mediakeysession-h.md#oh_mediakeysession_eventcallback) eventCallback | Pointer to the callback invoked for normal events, such as key expiration. When the MediaKeySession state changes normally, the system invokes this callback to notify the application. |
| [OH_MediaKeySession_KeyChangeCallback](capi-native-mediakeysession-h.md#oh_mediakeysession_keychangecallback) keyChangeCallback | Pointer to the callback invoked for key change events, used to handle key state changes. When the key state changes (for example, the key becomes available or expires), the system invokes this callback to notify the application, and the callback parameters contain the information about the changed key. |


