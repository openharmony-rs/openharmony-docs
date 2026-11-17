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

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_ArkUI_LinearGradientBlurOptions](capi-arkui-nativemodule-oh-arkui-lineargradientbluroptions.md) | OH_ArkUI_LinearGradientBlurOptions | 定义线性渐变模糊效果的选项。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_ArkUI_AnimationPropertyType](#oh_arkui_animationpropertytype)   | OH_ArkUI_AnimationPropertyType  | 枚举属性动画、关键帧动画和路径动画的可动画属性类型。             |
| [OH_ArkUI_AnimationGroupState](#oh_arkui_animationgroupstate)       | OH_ArkUI_AnimationGroupState    | 枚举动画组的播放状态。                          |
| [OH_ArkUI_AnimationFinishMode](#oh_arkui_animationfinishmode)       | OH_ArkUI_AnimationFinishMode    | 枚举动画组的结束模式。                          |
| [OH_ArkUI_LinearGradientBlurDirection](#oh_arkui_lineargradientblurdirection) | OH_ArkUI_LinearGradientBlurDirection | 枚举线性渐变模糊的渐变方向。 |

### 函数

| 名称 | 返回值 | 描述 |
| -- | -- | -- |
| [void OH_ArkUI_NativeModule_LinearGradientBlurOptions_Destroy(OH_ArkUI_LinearGradientBlurOptions *options)](#oh_arkui_nativemodule_lineargradientbluroptions_destroy) | - | 销毁线性渐变模糊选项对象。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_LinearGradientBlurOptions_SetBlurRadius(OH_ArkUI_LinearGradientBlurOptions *options, float blurRadius)](#oh_arkui_nativemodule_lineargradientbluroptions_setblurradius) | - | 设置线性渐变模糊选项的模糊半径。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_LinearGradientBlurOptions_GetBlurRadius(const OH_ArkUI_LinearGradientBlurOptions *options, float *blurRadius)](#oh_arkui_nativemodule_lineargradientbluroptions_getblurradius) | - | 获取线性渐变模糊选项的模糊半径。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_LinearGradientBlurOptions_SetFractionStops(OH_ArkUI_LinearGradientBlurOptions *options, const float *fractionStops, int32_t stopsLength)](#oh_arkui_nativemodule_lineargradientbluroptions_setfractionstops) | - | 设置线性渐变模糊选项的渐变模糊分段。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_LinearGradientBlurOptions_GetFractionStops(const OH_ArkUI_LinearGradientBlurOptions *options, float *fractionStops, int32_t stopsSize, int32_t *writeLength)](#oh_arkui_nativemodule_lineargradientbluroptions_getfractionstops) | - | 获取线性渐变模糊选项的渐变模糊分段。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_LinearGradientBlurOptions_SetDirection(OH_ArkUI_LinearGradientBlurOptions *options, OH_ArkUI_LinearGradientBlurDirection direction)](#oh_arkui_nativemodule_lineargradientbluroptions_setdirection) | - | 设置线性渐变模糊选项的渐变方向。 |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_LinearGradientBlurOptions_GetDirection(const OH_ArkUI_LinearGradientBlurOptions *options, OH_ArkUI_LinearGradientBlurDirection *direction)](#oh_arkui_nativemodule_lineargradientbluroptions_getdirection) | - | 获取线性渐变模糊选项的渐变方向。 |

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

### OH_ArkUI_LinearGradientBlurDirection

```c
enum OH_ArkUI_LinearGradientBlurDirection
```

**描述：**


枚举线性渐变模糊的渐变方向。

**起始版本：** 26.1.0

| 枚举项 | 描述 |
| -- | -- |
| OH_ARKUI_LINEAR_GRADIENT_BLUR_DIRECTION_LEFT = 0 | 线性渐变模糊从右到左。 |
| OH_ARKUI_LINEAR_GRADIENT_BLUR_DIRECTION_TOP = 1 | 线性渐变模糊从下到上。 |
| OH_ARKUI_LINEAR_GRADIENT_BLUR_DIRECTION_RIGHT = 2 | 线性渐变模糊从左到右。 |
| OH_ARKUI_LINEAR_GRADIENT_BLUR_DIRECTION_BOTTOM = 3 | 线性渐变模糊从上到下。 |
| OH_ARKUI_LINEAR_GRADIENT_BLUR_DIRECTION_LEFT_TOP = 4 | 线性渐变模糊从右下到左上。 |
| OH_ARKUI_LINEAR_GRADIENT_BLUR_DIRECTION_LEFT_BOTTOM = 5 | 线性渐变模糊从右上到左下。 |
| OH_ARKUI_LINEAR_GRADIENT_BLUR_DIRECTION_RIGHT_TOP = 6 | 线性渐变模糊从左下到右上。 |
| OH_ARKUI_LINEAR_GRADIENT_BLUR_DIRECTION_RIGHT_BOTTOM = 7 | 线性渐变模糊从左上到右下。 |

## 函数说明

### OH_ArkUI_NativeModule_LinearGradientBlurOptions_Create()

```c
OH_ArkUI_LinearGradientBlurOptions* OH_ArkUI_NativeModule_LinearGradientBlurOptions_Create(void)
```

**描述：**

创建线性渐变模糊选项对象。

**起始版本：** 26.1.0

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_ArkUI_LinearGradientBlurOptions](capi-arkui-nativemodule-oh-arkui-lineargradientbluroptions.md)* | 返回指向[OH_ArkUI_LinearGradientBlurOptions](capi-arkui-nativemodule-oh-arkui-lineargradientbluroptions.md)对象的指针。调用者拥有返回的对象，不再使用时需要调用[OH_ArkUI_NativeModule_LinearGradientBlurOptions_Destroy](#oh_arkui_nativemodule_lineargradientbluroptions_destroy)销毁该对象。 |

### OH_ArkUI_NativeModule_LinearGradientBlurOptions_Destroy()

```c
void OH_ArkUI_NativeModule_LinearGradientBlurOptions_Destroy(OH_ArkUI_LinearGradientBlurOptions *options)
```

**描述：**

销毁线性渐变模糊选项对象。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_LinearGradientBlurOptions](capi-arkui-nativemodule-oh-arkui-lineargradientbluroptions.md) *options | [入参] 表示由[OH_ArkUI_NativeModule_LinearGradientBlurOptions_Create](#oh_arkui_nativemodule_lineargradientbluroptions_create)返回的[OH_ArkUI_LinearGradientBlurOptions](capi-arkui-nativemodule-oh-arkui-lineargradientbluroptions.md)对象指针。传入NULL无效果。对非NULL参数调用该函数后，对象指针即失效，不得再次使用或销毁。 |

### OH_ArkUI_NativeModule_LinearGradientBlurOptions_SetBlurRadius()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_LinearGradientBlurOptions_SetBlurRadius(OH_ArkUI_LinearGradientBlurOptions *options, float blurRadius)
```

**描述：**

设置线性渐变模糊选项的模糊半径。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_LinearGradientBlurOptions](capi-arkui-nativemodule-oh-arkui-lineargradientbluroptions.md) *options | [入参] 表示指向[OH_ArkUI_LinearGradientBlurOptions](capi-arkui-nativemodule-oh-arkui-lineargradientbluroptions.md)对象的指针。 |
| float blurRadius | [入参] 表示模糊半径，取值范围[0, +∞)，不能为NaN，单位为px。值越大模糊程度越高，值为0时表示不模糊。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) options为空指针、blurRadius为负数或blurRadius为NaN。 |

### OH_ArkUI_NativeModule_LinearGradientBlurOptions_GetBlurRadius()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_LinearGradientBlurOptions_GetBlurRadius(const OH_ArkUI_LinearGradientBlurOptions *options, float *blurRadius)
```

**描述：**

获取线性渐变模糊选项的模糊半径。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [OH_ArkUI_LinearGradientBlurOptions](capi-arkui-nativemodule-oh-arkui-lineargradientbluroptions.md) *options | [入参] 表示指向[OH_ArkUI_LinearGradientBlurOptions](capi-arkui-nativemodule-oh-arkui-lineargradientbluroptions.md)对象的指针。 |
| float *blurRadius | [出参] 表示用于接收模糊半径的指针，单位为px。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) options或blurRadius为空指针。 |

### OH_ArkUI_NativeModule_LinearGradientBlurOptions_SetFractionStops()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_LinearGradientBlurOptions_SetFractionStops(OH_ArkUI_LinearGradientBlurOptions *options, const float *fractionStops, int32_t stopsLength)
```

**描述：**

设置线性渐变模糊选项的渐变模糊分段。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_LinearGradientBlurOptions](capi-arkui-nativemodule-oh-arkui-lineargradientbluroptions.md) *options | [入参] 表示指向[OH_ArkUI_LinearGradientBlurOptions](capi-arkui-nativemodule-oh-arkui-lineargradientbluroptions.md)对象的指针。 |
| const float *fractionStops | [入参] 表示(模糊值, 位置)对的扁平float数组。每两个元素一组(fractionStops[i], fractionStops[i+1])表示一个分段。模糊值(fractionStops[i])表示该位置处应用的模糊半径比例，0.0表示不模糊，1.0表示按blurRadius完全模糊。位置(fractionStops[i+1])表示沿渐变方向的相对位置，0.0表示起点，1.0表示终点。位置值必须严格单调递增。每个元素不能为NaN，且必须在[0.0, 1.0]范围内。 |
| int32_t stopsLength | [入参] 表示fractionStops数组中的float元素个数。必须为偶数且不小于4。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) options或fractionStops为空指针、stopsLength为奇数、stopsLength小于4、位置未严格单调递增、或fractionStops中存在NaN或超出[0.0, 1.0]范围的元素。 |

### OH_ArkUI_NativeModule_LinearGradientBlurOptions_GetFractionStops()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_LinearGradientBlurOptions_GetFractionStops(const OH_ArkUI_LinearGradientBlurOptions *options, float *fractionStops, int32_t stopsSize, int32_t *writeLength)
```

**描述：**

获取线性渐变模糊选项的渐变模糊分段。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [OH_ArkUI_LinearGradientBlurOptions](capi-arkui-nativemodule-oh-arkui-lineargradientbluroptions.md) *options | [入参] 表示指向[OH_ArkUI_LinearGradientBlurOptions](capi-arkui-nativemodule-oh-arkui-lineargradientbluroptions.md)对象的指针。 |
| float *fractionStops | [出参] 表示用于接收(模糊值, 位置)对的扁平float数组的缓冲区指针。 |
| int32_t stopsSize | [入参] 表示调用者为fractionStops数组分配的缓冲区大小（float元素个数）。若缓冲区不足以容纳所有渐变模糊分段数据，则返回[ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode)，并将writeLength设为所需大小。 |
| int32_t *writeLength | [出参] 表示返回[ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode)时实际写入fractionStops缓冲区的float元素个数；返回[ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode)时表示容纳fractionStops所需的最小缓冲区大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) options、writeLength或fractionStops为空指针。<br>         [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode) stopsSize小于实际fractionStops数量。 |

### OH_ArkUI_NativeModule_LinearGradientBlurOptions_SetDirection()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_LinearGradientBlurOptions_SetDirection(OH_ArkUI_LinearGradientBlurOptions *options, OH_ArkUI_LinearGradientBlurDirection direction)
```

**描述：**

设置线性渐变模糊选项的渐变方向。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_ArkUI_LinearGradientBlurOptions](capi-arkui-nativemodule-oh-arkui-lineargradientbluroptions.md) *options | [入参] 表示指向[OH_ArkUI_LinearGradientBlurOptions](capi-arkui-nativemodule-oh-arkui-lineargradientbluroptions.md)对象的指针。 |
| [OH_ArkUI_LinearGradientBlurDirection](#oh_arkui_lineargradientblurdirection) direction | [入参] 表示线性渐变模糊的方向。参数类型为[OH_ArkUI_LinearGradientBlurDirection](#oh_arkui_lineargradientblurdirection)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) options为空指针或direction不是有效的枚举值。 |

### OH_ArkUI_NativeModule_LinearGradientBlurOptions_GetDirection()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_LinearGradientBlurOptions_GetDirection(const OH_ArkUI_LinearGradientBlurOptions *options, OH_ArkUI_LinearGradientBlurDirection *direction)
```

**描述：**

获取线性渐变模糊选项的渐变方向。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [OH_ArkUI_LinearGradientBlurOptions](capi-arkui-nativemodule-oh-arkui-lineargradientbluroptions.md) *options | [入参] 表示指向[OH_ArkUI_LinearGradientBlurOptions](capi-arkui-nativemodule-oh-arkui-lineargradientbluroptions.md)对象的指针。 |
| [OH_ArkUI_LinearGradientBlurDirection](#oh_arkui_lineargradientblurdirection) *direction | [出参] 表示用于接收线性渐变模糊方向的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ErrorCode](capi-native-type-h.md#arkui_errorcode) | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) options或direction为空指针。 |
