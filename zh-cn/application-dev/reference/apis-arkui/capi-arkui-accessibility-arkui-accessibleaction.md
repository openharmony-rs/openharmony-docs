# ArkUI_AccessibleAction
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyinhua-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct {...} ArkUI_AccessibleAction
```

## 概述

无障碍操作内容结构。该结构体用于描述无障碍节点支持的操作类型及其描述信息。支持无障碍服务向用户呈现节点可执行的操作（如点击、长按、滚动等），并提供操作的文字说明，以帮助用户理解操作含义。

**起始版本：** 13

**相关模块：** [ArkUI_Accessibility](capi-arkui-accessibility.md)

**所在头文件：** [native_interface_accessibility.h](capi-native-interface-accessibility-h.md)

## 汇总

### 成员变量

| 名称                                            | 描述 |
|-----------------------------------------------| -- |
| [ArkUI_Accessibility_ActionType](capi-native-interface-accessibility-h.md#arkui_accessibility_actiontype) actionType | 操作类型。 |
| const char* description | 操作描述信息。 |


