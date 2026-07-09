# ArkUI_PickerIndicatorBackground

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @luoying_ace_admin-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct {...} ArkUI_PickerIndicatorBackground
```

## 概述

选择器指示器背景的样式参数。用于设置选择器指示器背景样式的参数结构体；指示器背景样式以背景色和圆角高亮显示选择器的选中项，包括选中项背景颜色和圆角半径。

**使用场景：**
- 在选择器（Picker）组件中为选中项设置自定义背景样式，如音乐播放器中的歌曲列表选中背景
- 在日期选择器中突出显示当前选中的日期或时间，提升用户体验
- 在选项列表中为选中项添加圆角背景，增强视觉层次感

**起始版本：** 23

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [picker.h](capi-picker-h.md)

**相关示例：** <!--RP1-->[native_type_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeType/native_type_sample)<!--RP1End-->

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t backgroundColor | 选中项背景的颜色。<br>默认值：0（完全透明，ARGB值为0x00000000，背景不可见）。<br>格式要求：0xAARRGGBB格式，第1个字节为透明度（00表示全透明，FF表示完全不透明），第2-4个字节分别为红、绿、蓝通道，例如<b>0xFF1122FF</b>。 |
| float topLeftRadius | 左上角圆角半径。<br>默认值：0<br>单位：vp<br>取值范围：取选中项的宽和高之中较小的边长为x，最大不超过x的一半。当取值小于0时，设置选择器指示器背景的样式参数失败；当取值大于最大值时，使用最大值。 |
| float topRightRadius | 右上角圆角半径。<br>默认值：0<br>单位：vp<br>取值范围：取选中项的宽和高之中较小的边长为x，最大不超过x的一半。当取值小于0时，设置选择器指示器背景的样式参数失败；当取值大于最大值时，使用最大值。 |
| float bottomLeftRadius | 左下角圆角半径。<br>默认值：0<br>单位：vp<br>取值范围：取选中项的宽和高之中较小的边长为x，最大不超过x的一半。当取值小于0时，设置选择器指示器背景的样式参数失败；当取值大于最大值时，使用最大值。 |
| float bottomRightRadius | 右下角圆角半径。<br>默认值：0<br>单位：vp<br>取值范围：取选中项的宽和高之中较小的边长为x，最大不超过x的一半。当取值小于0时，设置选择器指示器背景的样式参数失败；当取值大于最大值时，使用最大值。 |
