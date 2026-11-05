# MediaKeySession_Callback

<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @qin_wei_jie-->
<!-- md-trans-meta sourceCommit=21259e195bf1b8fc84db30d7d959f8dc56433790 translatedAt=2026-11-03T06:46:25.716Z pushedAt=2026-11-04T03:11:19.909Z nl=1 -->

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
| [MediaKeySession_EventCallback](capi-native-mediakeysession-h.md#mediakeysession_eventcallback) eventCallback | Pointer to the callback for normal events, used to handle routine events such as key expiration. When the state of the MediaKeySession changes normally, the system invokes this callback to notify the application. |
| [MediaKeySession_KeyChangeCallback](capi-native-mediakeysession-h.md#mediakeysession_keychangecallback) keyChangeCallback | Pointer to the callback for key change events, used to handle key state change events. When the key state changes (for example, the key becomes available or expires), the system invokes this callback to notify the application, and the callback parameters contain the information about the changed key. |


