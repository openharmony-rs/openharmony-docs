# OH_MediaKeySession_Callback

<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @qin_wei_jie-->
<!-- md-trans-meta sourceCommit=21259e195bf1b8fc84db30d7d959f8dc56433790 translatedAt=2026-11-03T06:47:04.704Z pushedAt=2026-11-04T03:11:19.914Z nl=1 -->

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
| [OH_MediaKeySession_EventCallback](capi-native-mediakeysession-h.md#oh_mediakeysession_eventcallback) eventCallback | Pointer to the callback invoked when the MediaKeySession state changes normally, used to handle regular events such as key expiration. |
| [OH_MediaKeySession_KeyChangeCallback](capi-native-mediakeysession-h.md#oh_mediakeysession_keychangecallback) keyChangeCallback | Pointer to the callback invoked when the key state changes, such as key availability or key expiration. The callback parameters contain the information about the changed key. |


