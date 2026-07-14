# ArkUI_TranslationOptions
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct {...} ArkUI_TranslationOptions
```

## 概述

定义组件转场时平移效果的配置选项，用于设置组件在转场过程中横向、纵向和深度方向的平移距离。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_type.h](capi-native-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| float x | 横向的平移距离，单位为vp。 |
| float y | 纵向的平移距离，单位为vp。 |
| float z | 深度方向的平移距离，单位为vp。 |
