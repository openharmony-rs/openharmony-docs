# ArkUI_GestureRecognizer
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct ArkUI_GestureRecognizer ArkUI_GestureRecognizer
```

## 概述

提供手势组件实例对象定义，用于在ArkUI手势识别接口中表示手势识别器对象。手势识别器绑定到UI组件后监听触摸事件，并在满足对应手势类型的识别条件时通过回调通知开发者；不同类型的识别器可用于敲击、长按、拖动、捏合、旋转和快滑等手势。详细机制和使用方式请参见[native_gesture.h](capi-native-gesture-h.md)中的手势接口说明。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_gesture.h](capi-native-gesture-h.md)

