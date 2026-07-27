# ArkUI_AnimateCompleteCallback

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e98b791a1f57fab5012a75ce7d9ff0a0466dd410 translatedAt=2026-07-17T02:51:04.450Z pushedAt=2026-07-17T03:20:22.882Z -->

```c
typedef struct {...} ArkUI_AnimateCompleteCallback
```

## Overview

Defines the callback type for when the animation playback is complete.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_animate.h](capi-native-animate-h.md)

## Summary

### Member Variables

| Name                                                                             | Description|
|---------------------------------------------------------------------------------| -- |
| [ArkUI_FinishCallbackType](capi-native-type-visual-h.md#arkui_finishcallbacktype) type | Callback type for when the animation playback is complete, used to specify how the callback is triggered. |
| void* userData                                                                  | Pointer to the custom data passed upon animation end callback.|

### Member Functions

| Name| Description|
| -- | -- |
| [void (\*callback)(void* userData)](#callback) | Callback for when the animation playback is complete.|

## Member Function Description

### callback()

```c
void (*callback)(void* userData)
```

**Description**

Invoked when the animation playback is complete.