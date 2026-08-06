# ARKUI_TextPickerCascadeRangeContent
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @luoying_ace_admin-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct {...} ARKUI_TextPickerCascadeRangeContent
```

## 概述

定义多列联动滑动数据选择器的结构体，用于描述多列联动选择器的层级数据结构。该结构体通过children成员形成树状结构，支持多级联动选择，适用于需要展示省市区、年月日等分级数据的场景，可简化多级联动选择器的开发。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [picker.h](capi-picker-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| const char* text | 要显示在多列联动滑动选择器中的文本内容，用于表示该选项的显示文本。默认值为NULL，可设置为空字符串表示无文本。取值原则请参见接口说明。<br>**说明：** 未设置文本时，建议将text设置为NULL。 |
| const [ARKUI_TextPickerRangeContent](capi-arkui-nativemodule-arkui-textpickerrangecontent.md)* children | 子级联动数据数组指针，指向下一级联动数据数组。当前级别选中该选项时，children对应数组内容会作为下一级显示的选项；无子级数据时设置为NULL。传入的数组指针需要在选择器使用期间保持有效，调用者负责管理数组内存。 |
| int32_t size | children数组的元素个数，即当前层级的选项数量。取值必须大于等于0，且需与实际传入的children数组元素个数一致；当children为NULL时应设置为0。传入负数或不一致时抛出参数错误异常。 |

