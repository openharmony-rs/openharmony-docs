# OH_ArkUI_NativeModule_UIJsonWrapper
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lushi871202-->
<!--Designer: @lushi871202 -->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct OH_ArkUI_NativeModule_UIJsonWrapper OH_ArkUI_NativeModule_UIJsonWrapper
```

## 概述

定义内部结构不对外公开的不可变JSON数据对象。<br>该对象保存一个JSON字符串，既用于承载框架传递的数据（UI感知），也用于承载应用注入的命令（UI控制）。JSON对象顶层必须包含schemaVersion字段，用于版本控制和后续兼容性维护。应用传入的JSON，以及框架通过接口返回或回调传递的JSON，均必须满足此要求；即使没有采集内容，返回的JSON也必须携带该字段。<br>该对象不使用引用计数。复制对象指针仅产生借用别名，不会创建独立对象或增加所有权。对象的所有者必须且只能销毁该对象一次。销毁后，所有别名及数据指针均失效，不得再次使用或销毁。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 26.1.0

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [ui_json_wrapper.h](capi-ui-json-wrapper-h.md)
