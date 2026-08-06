# ArkUI_RotationOptions

```c
typedef struct ArkUI_RotationOptions {...} ArkUI_RotationOptions
```

## 概述

Defines the rotation options for component transition.

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_type.h](capi-native-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| float x | X-component of the rotation vector. |
| float y | Y-component of the rotation vector. |
| float z | Z-component of the rotation vector. |
| float angle | Rotation angle. |
| float centerX | X coordinate of the center point. |
| float centerY | Y coordinate of the center point. |
| float centerZ | Z-axis anchor, that is, the z-component of the 3D rotation center point. |
| float perspective | Distance from the user to the z=0 plane. |


