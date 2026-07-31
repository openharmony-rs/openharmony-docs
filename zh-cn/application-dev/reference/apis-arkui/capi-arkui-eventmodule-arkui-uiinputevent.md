# ArkUI_UIInputEvent
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct ArkUI_UIInputEvent ArkUI_UIInputEvent
```

## 概述

ArkUI_UIInputEvent用于表示ArkUI中的UI输入事件。ArkUI_EventModule中的事件接口通过该对象向回调传递输入事件数据，开发者可使用查询接口获取事件信息，适用于识别或响应用户输入事件的场景。

**起始版本：** 12

**相关模块：** [ArkUI_EventModule](capi-arkui-eventmodule.md)

**所在头文件：** [ui_input_event.h](capi-ui-input-event-h.md)

