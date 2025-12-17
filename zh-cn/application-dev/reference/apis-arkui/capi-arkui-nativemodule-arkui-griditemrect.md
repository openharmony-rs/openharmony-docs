# ArkUI_GridItemRect

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zcdqs-->
<!--Designer: @zcdqs-->
<!--Tester: @liuzhenshuo-->
<!--Adviser: @Brilliantry_Rui-->

```
typedef struct {...} ArkUI_GridItemRect
```

## 概述

定义Grid布局选项onGetRectByIndex回调返回值结构体。

**起始版本：** 22

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_type.h](capi-native-type-h.md)

**相关示例：** <!--RP1-->[native_type_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeType/native_type_sample)<!--RP1End-->

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t rowStart | GridItem行起始位置。 |
| uint32_t columnStart | GridItem列起始位置。 |
| uint32_t rowSpan | GridItem占用的行数。 |
| uint32_t columnSpan | GridItem占用的列数。 |

