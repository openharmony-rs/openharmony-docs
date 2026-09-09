# ArkUI_AccessibilityEventInfo
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyinhua-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct ArkUI_AccessibilityEventInfo ArkUI_AccessibilityEventInfo
```

## 概述

无障碍事件信息。用于承载应用向无障碍服务上报的无障碍事件内容，可通过[OH_ArkUI_SendAccessibilityAsyncEvent](capi-native-interface-accessibility-h.md#oh_arkui_sendaccessibilityasyncevent)接口上报：既适用于无障碍服务或辅助应用要求控件执行操作后，发送执行结果事件以通知操作结果，也适用于组件状态变化（如点击、选中、文本更新、页面切换、焦点变化等）、主动播报、请求聚焦等需要向无障碍服务上报事件的场景。

**起始版本：** 13

**相关模块：** [ArkUI_Accessibility](capi-arkui-accessibility.md)

**所在头文件：** [native_interface_accessibility.h](capi-native-interface-accessibility-h.md)

