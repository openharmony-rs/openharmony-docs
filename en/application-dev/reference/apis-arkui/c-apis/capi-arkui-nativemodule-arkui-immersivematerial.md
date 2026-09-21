# ArkUI_ImmersiveMaterial

```c
typedef struct ArkUI_ImmersiveMaterial ArkUI_ImmersiveMaterial
```

## Overview

Defines the immersive material object on the native side. Immersive materials have different performance levels based on the computing power of the device. The performance level is defined by {@link ArkUI_MaterialLevel}, which can be obtained<br>by {@link OH_ArkUI_NativeModule_GetGlobalMaterialLevel}. On high-end and mid-range computing power devices, they affect the filter effect of the material layer and shadow effect. On low-end computing power devices, it affects the background color, border color, border width, and shadow effect.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_material.h](capi-native-material-h.md)

