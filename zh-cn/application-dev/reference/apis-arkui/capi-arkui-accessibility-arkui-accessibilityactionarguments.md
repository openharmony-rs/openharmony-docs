# ArkUI_AccessibilityActionArguments
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyinhua-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct ArkUI_AccessibilityActionArguments ArkUI_AccessibilityActionArguments
```

## 概述

表示无障碍操作的具体参数。当无障碍服务（如读屏软件、语音助手）请求在指定节点上执行无障碍操作（如选择文本、设置光标位置）时，系统通过该结构体向第三方平台传递操作所需的附加上下文信息，第三方平台可在[executeAccessibilityAction](capi-arkui-accessibility-arkui-accessibilityprovidercallbacks.md#executeaccessibilityaction)回调中调用[OH_ArkUI_FindAccessibilityActionArgumentByKey](capi-native-interface-accessibility-h.md#oh_arkui_findaccessibilityactionargumentbykey)获取指定参数的值。适用于第三方平台需要解析并响应无障碍操作参数的场景，例如读屏软件触发的文本选择、语音助手触发的无障碍交互等。

**起始版本：** 13

**相关模块：** [ArkUI_Accessibility](capi-arkui-accessibility.md)

**所在头文件：** [native_interface_accessibility.h](capi-native-interface-accessibility-h.md)

