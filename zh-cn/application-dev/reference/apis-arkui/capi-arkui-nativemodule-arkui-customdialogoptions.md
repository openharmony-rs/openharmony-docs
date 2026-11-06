# ArkUI_CustomDialogOptions
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @houguobiao-->
<!--Designer: @liyi0309-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct ArkUI_CustomDialogOptions ArkUI_CustomDialogOptions
```

## 概述

定义自定义弹窗的选项对象。该对象不暴露任何成员字段，开发者通过 [ArkUI_NativeModule](capi-arkui-nativemodule.md) 中以 `OH_ArkUI_CustomDialog_Set` 为前缀的接口（如设置背景、圆角、阴影、模糊、位置、模态等）配置弹窗属性，再调用 `OH_ArkUI_CustomDialog_OpenDialog` 打开弹窗。

**起始版本：** 19

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_dialog.h](capi-native-dialog-h.md)

