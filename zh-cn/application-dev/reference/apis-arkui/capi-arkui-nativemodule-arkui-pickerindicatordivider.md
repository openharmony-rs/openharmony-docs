# ArkUI_PickerIndicatorDivider

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @luoying_ace_admin-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

``` c
typedef struct {...} ArkUI_PickerIndicatorDivider
```

## 概述

分割线样式指示器的样式参数。

**起始版本：** 23

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_type.h](capi-native-type-h.md)

**相关示例：** <!--RP1-->[native_type_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeType/native_type_sample)<!--RP1End-->

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| float strokeWidth | 分割线的线宽。<br/>默认值：0<br/>单位：vp<br/>取值范围：[0, 选中项高度的一半（即20vp）]。strokeWidth小于0时设置分割线样式指示器的样式参数失败，strokeWidth大于选中项高度的一半时使用2.0px。不支持“百分比”类型。 |
| uint32_t dividerColor | 分割线的颜色。<br/>默认值：0<br/>取值范围：0xARGB格式，例如<b>0xFF1122FF</b>。 |
| float startMargin | 分割线与Picker容器侧边起始端的距离。<br/>默认值：0<br/>单位：vp<br/>取值范围：startMargin与endMargin之和不得超过Picker容器的宽度。设置小于0时设置分割线样式指示器的样式参数失败，startMargin与endMargin之和超过Picker容器的宽度时，使用默认值。不支持“百分比”类型。 |
| float endMargin | 分割线与Picker容器侧边结束端的距离。<br/>默认值：0<br/>单位：vp<br/>取值范围：startMargin与endMargin之和不得超过Picker容器的宽度。设置小于0时设置分割线样式指示器的样式参数失败，startMargin与endMargin之和超过Picker容器的宽度时，使用默认值。不支持“百分比”类型。 |