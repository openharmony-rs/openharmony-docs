# ArkUI_Context\*
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct ArkUI_Context* ArkUI_ContextHandle
```

## 概述

ArkUI（方舟UI框架）在 Native 侧的上下文实例对象指针，用于表示组件所在页面的 UIContext。开发者可通过[OH_ArkUI_GetContextByNode](capi-native-node-h.md#oh_arkui_getcontextbynode)或[OH_ArkUI_GetContextFromNapiValue](capi-native-node-napi-h.md#oh_arkui_getcontextfromnapivalue)获取该指针，并将其作为 UI 任务调度、动画、焦点控制等接口的上下文入参。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_type.h](capi-native-type-h.md)
