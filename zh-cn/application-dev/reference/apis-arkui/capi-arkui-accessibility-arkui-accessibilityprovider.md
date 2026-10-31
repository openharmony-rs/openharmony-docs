# ArkUI_AccessibilityProvider
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyinhua-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct ArkUI_AccessibilityProvider ArkUI_AccessibilityProvider
```

## 概述

该结构体为无障碍第三方操作提供者，用于承载回调函数的实现。开发者可通过该结构体注册和管理无障碍操作相关的回调，实现自定义的无障碍交互逻辑，适用于需要扩展或定制ArkUI无障碍能力的场景。

**起始版本：** 13

**相关模块：** [ArkUI_Accessibility](capi-arkui-accessibility.md)

**所在头文件：** [native_interface_accessibility.h](capi-native-interface-accessibility-h.md)

