# ArkUI_TextChangeEvent
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiaxiaguang-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct {...} ArkUI_TextChangeEvent
```

## 概述

定义文本变化事件的数据结构，用于在文本输入场景中监听和处理文本变更事件。该结构体包含文本内容、扩展信息和数值参数，支持开发者实时获取文本变更数据，适用于输入框内容监听、实时搜索、字数统计等场景。

**起始版本：** 15

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| const char* pStr | 文本变更事件中的文本内容字符串。 |
| const char* pExtendStr | 文本变更事件中的扩展字符串，用于存储额外的文本信息。 |
| int32_t number | 事件的数字参数值，用于记录文本变更事件中的数值信息。取值范围[-2147483648, 2147483647]。 |


