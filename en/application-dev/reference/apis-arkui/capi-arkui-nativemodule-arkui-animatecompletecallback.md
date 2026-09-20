# ArkUI_AnimateCompleteCallback

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=39ca26def5c22dc659f3dc0b76ef62a29421e77a translatedAt=2026-08-19T04:16:53.493Z pushedAt=2026-08-19T06:53:02.802Z -->

```c
typedef struct {...} ArkUI_AnimateCompleteCallback
```

## Overview

Defines the callback type for when the animation playback is complete, which is used to notify you that the animation playback is complete. You can use the **type** field to specify a callback trigger mode, use the **callback** field to set a custom callback function, and use the **userData** field to pass user-defined data to the callback function.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_animate.h](capi-native-animate-h.md)

## Summary

### Member Variables

| Name                                                                             | Description|
|---------------------------------------------------------------------------------| -- |
| [ArkUI_FinishCallbackType](capi-native-type-visual-h.md#arkui_finishcallbacktype) type | Callback type for when the animation playback is complete, used to specify how the callback is triggered. The value options are as follows: **ARKUI_FINISH_CALLBACK_REMOVED(0)** indicates that the callback is triggered when the animation ends and is removed immediately, and **ARKUI_FINISH_CALLBACK_LOGICALLY(1)** indicates that the callback is triggered when the animation playback is logically complete (it may still be in the tailing state). Different callback types are triggered at different times. Select an appropriate type based on the service scenario. If **type** is not explicitly set, **ARKUI_FINISH_CALLBACK_REMOVED** is used. |
| void\* userData                                                                  | Pointer to the user-defined data passed upon animation end callback. Ensure that **userData** is still valid when the animation completion callback is triggered to avoid undefined behavior caused by a dangling pointer. If this parameter is set to **NULL**, the callback function will not receive the **userData** parameter. |

### Member Functions

| Name| Description|
| -- | -- |
| [void (\*callback)(void\* userData)](#callback) | Pointer to the callback for when the animation playback is complete. It can be used to perform custom operations after the animation playback ends, such as starting a transition animation, updating the UI element state, or clearing resources. |

## Member Function Description

### callback()

```c
void (*callback)(void* userData)
```

**Description**

Invoked when the animation playback is complete. It is used together with **type** and **userData**. The **type** parameter determines the timing type for triggering the callback, and the callback function receives **userData** as an input parameter. After this callback is set, it is automatically invoked when the animation playback ends. You can execute custom logic in the callback through the **userData** parameter, such as updating the UI state or handling subsequent operations after the animation playback is complete.