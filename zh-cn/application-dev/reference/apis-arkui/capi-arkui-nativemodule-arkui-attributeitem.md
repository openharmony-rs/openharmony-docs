# ArkUI_AttributeItem
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @piggyguy; @xiang-shouxing; @yangfan229-->
<!--Designer: @piggyguy; @xiang-shouxing; @yangfan229-->
<!--Tester: @fredyuan912-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct {...} ArkUI_AttributeItem
```

## 概述

定义[setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute)函数通用入参结构。各个属性设置接口可选择使用其中的成员变量来存储特定类型的参数数据。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

## 汇总

### 成员变量

| 名称                                 | 描述 |
|------------------------------------| -- |
| const [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)* value | 数字类型数组，用于存储数字数组类型的参数。 |
| int32_t size                       | 数字类型数组大小，配合变量value使用，value数组的长度。 |
| const char* string                 | 字符串类型，用于存储字符串类型的参数。 |
| void* object                       | 对象类型，用于存储对象类型的参数。 |


