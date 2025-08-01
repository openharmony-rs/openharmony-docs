# ArkUI_NativeAnimateAPI_1

## 概述

ArkUI提供的Native侧动画接口集合。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_animate.h](capi-native-animate-h.md)

## 汇总

### 成员函数

| 名称 | 描述 |
| -- | -- |
| [int32_t (\*animateTo)(ArkUI_ContextHandle context, ArkUI_AnimateOption* option, ArkUI_ContextCallback* update,ArkUI_AnimateCompleteCallback* complete)](#animateto) | 显式动画接口。 |
| [int32_t (\*keyframeAnimateTo)(ArkUI_ContextHandle context, ArkUI_KeyframeAnimateOption* option)](#keyframeanimateto) | 关键帧动画接口。 |
| [ArkUI_AnimatorHandle (\*createAnimator)(ArkUI_ContextHandle context, ArkUI_AnimatorOption* option)](#createanimator) | 创建animator动画对象。 |
| [void (\*disposeAnimator)(ArkUI_AnimatorHandle animatorHandle)](#disposeanimator) | 销毁animator动画对象。 |

## 成员函数说明

### animateTo()

```
int32_t (*animateTo)(ArkUI_ContextHandle context, ArkUI_AnimateOption* option, ArkUI_ContextCallback* update,ArkUI_AnimateCompleteCallback* complete)
```

**描述：**


显式动画接口。

**参数：**

| 参数项                                                                                                 | 描述 |
|-----------------------------------------------------------------------------------------------------| -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) context                           | UIContext实例。 |
| [ArkUI_AnimateOption](capi-arkui-nativemodule-arkui-animateoption.md)* option                       | 设置动画效果相关参数。 |
| [ArkUI_ContextCallback](capi-arkui-nativemodule-arkui-contextcallback.md)* update                                                                   | 指定动效的闭包函数，在闭包函数中导致的状态变化系统会自动插入过渡动画。 |
| [ArkUI_AnimateCompleteCallback](capi-arkui-nativemodule-arkui-animatecompletecallback.md)* complete | 设置动画播放完成回调参数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>            [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>            [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### keyframeAnimateTo()

```
int32_t (*keyframeAnimateTo)(ArkUI_ContextHandle context, ArkUI_KeyframeAnimateOption* option)
```

**描述：**


关键帧动画接口。

**参数：**

| 参数项                                                                       | 描述 |
|---------------------------------------------------------------------------| -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) context | UIContext实例。 |
| [ArkUI_KeyframeAnimateOption](capi-arkui-nativemodule-arkui-keyframeanimateoption.md)* option                                   | 关键帧动画参数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>            [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>            [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) 函数参数异常。 |

### createAnimator()

```
ArkUI_AnimatorHandle (*createAnimator)(ArkUI_ContextHandle context, ArkUI_AnimatorOption* option)
```

**描述：**


创建animator动画对象。

**参数：**

| 参数项                                                                       | 描述 |
|---------------------------------------------------------------------------| -- |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-context8h.md) context | UIContext实例。 |
| [ArkUI_AnimatorOption](capi-arkui-nativemodule-arkui-animatoroption.md)* option                                          | animator动画参数。 |

**返回：**

| 类型                       | 说明 |
|--------------------------| -- |
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) | animator动画对象指针。函数参数异常时返回NULL。 |

### disposeAnimator()

```
void (*disposeAnimator)(ArkUI_AnimatorHandle animatorHandle)
```

**描述：**


销毁animator动画对象。

**参数：**

| 参数项 | 描述 |
|-----|----|
| [ArkUI_AnimatorHandle](capi-arkui-nativemodule-arkui-animator8h.md) animatorHandle | animator动画对象。 |
