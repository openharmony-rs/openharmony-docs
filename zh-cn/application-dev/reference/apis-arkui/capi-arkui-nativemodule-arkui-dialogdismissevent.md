# ArkUI_DialogDismissEvent
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @houguobiao-->
<!--Designer: @houguobiao-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct ArkUI_DialogDismissEvent ArkUI_DialogDismissEvent
```

## 概述

定义弹窗关闭事件对象，用于在弹窗被关闭时通知开发者，适用于需要监听弹窗关闭事件的场景。该事件对象采用回调机制，当弹窗触发关闭操作时，系统会创建并传递此事件对象到开发者注册的回调函数中，开发者可通过该对象获取关闭原因、设置是否拦截关闭或传递自定义数据。该事件对象不暴露内部成员，需通过对应的接口（如 OH_ArkUI_DialogDismissEvent_SetShouldBlockDismiss、OH_ArkUI_DialogDismissEvent_GetUserData、OH_ArkUI_DialogDismissEvent_GetDismissReason）获取或设置相关信息。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_dialog.h](capi-native-dialog-h.md)

