# ArkUI_AnimateCompleteCallback
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @CCFFWW-->
<!--Designer: @CCFFWW-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct {...} ArkUI_AnimateCompleteCallback
```

## 概述

动画播放结束回调类型。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_animate.h](capi-native-animate-h.md)

## 汇总

### 成员变量

| 名称                                                                              | 描述 |
|---------------------------------------------------------------------------------| -- |
| [ArkUI_FinishCallbackType](capi-native-type-h.md#arkui_finishcallbacktype) type | 在动画中定义结束回调的类型。 |
| void* userData                                                                  | 用于动画结束回调，传递用户自定义数据。 |


### 成员函数

| 名称 | 描述 |
| -- | -- |
| [void (\*callback)(void* userData)](#callback) | 动画播放结束回调。 |

## 成员函数说明

### callback()

```c
void (*callback)(void* userData)
```

**描述：**


动画播放结束回调。


