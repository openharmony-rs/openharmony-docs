# ArkUI_AnimateCompleteCallback

```c
typedef struct ArkUI_AnimateCompleteCallback {...} ArkUI_AnimateCompleteCallback
```

## Overview

Defines the callback type for when the animation playback is complete.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_animate.h](capi-native-animate-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| ArkUI_FinishCallbackType type | Callback type for when the animation playback is complete. |
| void* userData | Custom data passed upon animation end callback. |


### Member functions

| Name | Description |
| -- | -- |
| [void (\*callback)(void* userData)](#callback) | Invoked when the animation playback is complete. |

## Member function description

### callback()

```c
void (*callback)(void* userData)
```

**Description**

Invoked when the animation playback is complete.


