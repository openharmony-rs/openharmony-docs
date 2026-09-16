# ArkUI_Context*

```c
typedef struct ArkUI_Context* ArkUI_ContextHandle
```

## 概述

ArkUI在Native侧的上下文实例对象指针，用于表示组件所在页面的UIContext。开发者可通过{@link OH_ArkUI_GetContextByNode}或{@link OH_ArkUI_GetContextFromNapiValue}获取该指针，并将其作为 UI 任务调度、动画、焦点控制等接口的上下文入参。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [common_type.h](capi-common-type-h.md)

