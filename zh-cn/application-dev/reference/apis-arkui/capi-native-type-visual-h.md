# native_type_visual.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

提供NativeModule视觉相关的类型定义。

**引用文件：** <arkui/native_type_visual.h>

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_ArkUI_AnimationPropertyType](#oh_arkui_animationpropertytype)   | OH_ArkUI_AnimationPropertyType  | 枚举属性动画、关键帧动画和路径动画的可动画属性类型。             |
| [OH_ArkUI_AnimationGroupState](#oh_arkui_animationgroupstate)       | OH_ArkUI_AnimationGroupState    | 枚举动画组的播放状态。                          |
| [OH_ArkUI_AnimationFinishMode](#oh_arkui_animationfinishmode)       | OH_ArkUI_AnimationFinishMode    | 枚举动画组的结束模式。                          |

## 枚举类型说明

### OH_ArkUI_AnimationPropertyType

```c
enum OH_ArkUI_AnimationPropertyType
```

**描述：**


枚举属性动画、关键帧动画和路径动画的可动画属性类型。

**起始版本：** 26.0.1

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_ANIMATION_PROPERTY_TRANSLATION = 0 | 在x和y方向上的平移。设置或获取该属性值时，需要两个f32类型的[ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)元素，依次为x、y方向的平移量，单位为px。 |
| OH_ARKUI_ANIMATION_PROPERTY_TRANSLATION_X = 1 | 在x方向上的平移。设置或获取该属性值时，需要一个f32类型的[ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)元素，单位为px。 |
| OH_ARKUI_ANIMATION_PROPERTY_TRANSLATION_Y = 2 | 在y方向上的平移。设置或获取该属性值时，需要一个f32类型的[ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)元素，单位为px。 |
| OH_ARKUI_ANIMATION_PROPERTY_TRANSLATION_Z = 3 | 在z方向上的平移。设置或获取该属性值时，需要一个f32类型的[ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)元素，单位为px。 |
| OH_ARKUI_ANIMATION_PROPERTY_SCALE = 4 | 在x和y方向上的缩放。设置或获取该属性值时，需要两个f32类型的[ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)元素，依次为x、y方向的缩放比例。 |
| OH_ARKUI_ANIMATION_PROPERTY_SCALE_X = 5 | 在x方向上的缩放。设置或获取该属性值时，需要一个f32类型的[ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)元素。 |
| OH_ARKUI_ANIMATION_PROPERTY_SCALE_Y = 6 | 在y方向上的缩放。设置或获取该属性值时，需要一个f32类型的[ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)元素。 |
| OH_ARKUI_ANIMATION_PROPERTY_ROTATION = 7 | 所有轴的旋转角度。设置或获取该属性值时，需要三个f32类型的[ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)元素，依次为x、y、z轴的旋转角度，单位为度。 |
| OH_ARKUI_ANIMATION_PROPERTY_ROTATION_X = 8 | 围绕x轴的旋转角度。设置或获取该属性值时，需要一个f32类型的[ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)元素，单位为度。 |
| OH_ARKUI_ANIMATION_PROPERTY_ROTATION_Y = 9 | 围绕y轴的旋转角度。设置或获取该属性值时，需要一个f32类型的[ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)元素，单位为度。 |
| OH_ARKUI_ANIMATION_PROPERTY_ROTATION_Z = 10 | 围绕z轴的旋转角度。设置或获取该属性值时，需要一个f32类型的[ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)元素，单位为度。 |
| OH_ARKUI_ANIMATION_PROPERTY_OPACITY = 11 | 组件的不透明度。设置或获取该属性值时，需要一个f32类型的[ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)元素。取值范围：[0, 1]。 |
| OH_ARKUI_ANIMATION_PROPERTY_BOUNDS = 12 | 边界（位置和大小）。设置或获取该属性值时，需要四个i32类型的[ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)元素，依次为x坐标、y坐标、宽度、高度，单位为px。其中宽度和高度的取值范围为大于等于0。 |
| OH_ARKUI_ANIMATION_PROPERTY_BOUNDS_X = 13 | 边界左上角的x坐标位置。设置或获取该属性值时，需要一个i32类型的[ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)元素，单位为px。 |
| OH_ARKUI_ANIMATION_PROPERTY_BOUNDS_Y = 14 | 边界左上角的y坐标位置。设置或获取该属性值时，需要一个i32类型的[ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)元素，单位为px。 |
| OH_ARKUI_ANIMATION_PROPERTY_BOUNDS_WIDTH = 15 | 边界的宽度。设置或获取该属性值时，需要一个i32类型的[ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)元素，单位为px。取值范围为大于等于0。 |
| OH_ARKUI_ANIMATION_PROPERTY_BOUNDS_HEIGHT = 16 | 边界的高度。设置或获取该属性值时，需要一个i32类型的[ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)元素，单位为px。取值范围为大于等于0。 |
| OH_ARKUI_ANIMATION_PROPERTY_BACKGROUND_COLOR = 17 | 组件的背景颜色。设置或获取该属性值时，需要一个u32类型的[ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)元素。 |

### OH_ArkUI_AnimationGroupState

```c
enum OH_ArkUI_AnimationGroupState
```

**描述：**


枚举动画组的播放状态。

**起始版本：** 26.0.1

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_ANIMATION_GROUP_STATE_RUNNING = 0 | 动画组正在运行。 |
| OH_ARKUI_ANIMATION_GROUP_STATE_PAUSED = 1 | 动画组已暂停。 |
| OH_ARKUI_ANIMATION_GROUP_STATE_INACTIVE = 2 | 动画组处于非活动状态，例如动画已结束或动画组处于无效状态。 |

### OH_ArkUI_AnimationFinishMode

```c
enum OH_ArkUI_AnimationFinishMode
```

**描述：**


枚举动画组的结束模式。

**起始版本：** 26.0.1

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_ANIMATION_FINISH_TO_START = 0 | 结束动画组并跳转到起始状态。 |
| OH_ARKUI_ANIMATION_FINISH_TO_CURRENT = 1 | 结束动画组并保持在当前值。 |
| OH_ARKUI_ANIMATION_FINISH_TO_END = 2 | 结束动画组并跳转到结束状态。 |
