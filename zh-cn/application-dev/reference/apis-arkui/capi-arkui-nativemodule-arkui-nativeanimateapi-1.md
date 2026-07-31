# ArkUI_NativeAnimateAPI_1
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct {...} ArkUI_NativeAnimateAPI_1
```

## 概述

ArkUI提供的Native侧动画接口集合。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_animate.h](capi-native-animate-h.md)

## 汇总

### 成员函数

| 名称 | 描述 |
| -- | -- |
| [int32_t (\*animateTo)(ArkUI_ContextHandle context, ArkUI_AnimateOption* option, ArkUI_ContextCallback* update,ArkUI_AnimateCompleteCallback* complete)](#animateto) | 触发显式动画。 |
| [int32_t (\*keyframeAnimateTo)(ArkUI_ContextHandle context, ArkUI_KeyframeAnimateOption* option)](#keyframeanimateto) | 触发关键帧动画。 |
| [ArkUI_AnimatorHandle (\*createAnimator)(ArkUI_ContextHandle context, ArkUI_AnimatorOption* option)](#createanimator) | 创建animator动画对象并返回其指针（调用者获取对象所有权）。 |
| [void (\*disposeAnimator)(ArkUI_AnimatorHandle animatorHandle)](#disposeanimator) | 销毁传入指针所指向的animator动画对象，并释放其内存，销毁后不可再使用该指针。 |

## 成员函数说明

### animateTo()

```c
int32_t (*animateTo)(ArkUI_ContextHandle context, ArkUI_AnimateOption* option, ArkUI_ContextCallback* update, ArkUI_AnimateCompleteCallback* complete)
```

**描述：**

执行显式动画过渡效果。

**参数：**

| 参数项                                                                                                 | 描述 |
|-----------------------------------------------------------------------------------------------------| -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) context                           | UI上下文实例，用于指定动画所在的UI上下文环境。 |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option                       | 动画效果配置参数。 |
| [ArkUI_ContextCallback](capi-arkui-nativemodule-arkui-contextcallback.md)* update                   | 指定动效的闭包函数。在闭包函数中产生的状态变化，系统会自动插入过渡动画。<br>**说明**：在闭包函数中要设置的组件属性，必须在调用animateTo之前已在组件上设置过。 |
| [ArkUI_AnimateCompleteCallback](capi-arkui-nativemodule-arkui-animatecompletecallback.md)* complete | 动画播放完成回调函数。传参为NULL时不设置完成回调通知。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>            [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 成功。<br>            [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### keyframeAnimateTo()

```c
int32_t (*keyframeAnimateTo)(ArkUI_ContextHandle context, ArkUI_KeyframeAnimateOption* option)
```

**描述：**


关键帧动画接口。

**参数：**

| 参数项                                                                       | 描述 |
|---------------------------------------------------------------------------| -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) context | UI上下文实例，用于指定关键帧动画所在的UI上下文环境。 |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option                                   | 关键帧动画参数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>            [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 成功。<br>            [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) 函数参数异常。 |

### createAnimator()

```c
ArkUI_AnimatorHandle (*createAnimator)(ArkUI_ContextHandle context, ArkUI_AnimatorOption* option)
```

**描述：**


创建animator动画对象。

**参数：**

| 参数项                                                                       | 描述 |
|---------------------------------------------------------------------------| -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) context | UI上下文实例，用于指定动画所在的UI上下文环境。 |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option                                          | animator动画参数。 |

**返回：**

| 类型                       | 说明 |
|--------------------------| -- |
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) | animator动画对象指针，用于后续对动画对象进行控制。函数参数异常时返回NULL。 |

### disposeAnimator()

```c
void (*disposeAnimator)(ArkUI_AnimatorHandle animatorHandle)
```

**描述：**


销毁animator动画对象。

**参数：**

| 参数项 | 描述 |
|-----|----|
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) animatorHandle | animator动画对象。 |
