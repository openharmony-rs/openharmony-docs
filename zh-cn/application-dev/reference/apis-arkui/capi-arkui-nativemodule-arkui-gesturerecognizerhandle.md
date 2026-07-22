# ArkUI_GestureRecognizerHandle
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef ArkUI_GestureRecognizer* ArkUI_GestureRecognizerHandle
```

## 概述

定义手势识别器句柄类型，是ArkUI_GestureRecognizer指针类型的别名封装，用于在ArkUI原生手势接口中表示手势识别器对象。该句柄可在手势识别器创建、属性配置和事件回调监听等场景中作为对象引用，便于在Native层统一传递、管理和操作手势识别器；获取和使用方式请参见[native_gesture.h](capi-native-gesture-h.md)。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_gesture.h](capi-native-gesture-h.md)
