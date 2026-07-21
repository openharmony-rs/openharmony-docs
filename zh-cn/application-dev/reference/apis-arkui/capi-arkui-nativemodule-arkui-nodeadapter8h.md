# ArkUI_NodeAdapter*
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct ArkUI_NodeAdapter* ArkUI_NodeAdapterHandle
```

## 概述

定义组件适配器对象，用于滚动类组件的元素懒加载，适用于需要按需加载大量滚动内容的场景，可避免一次性创建全部元素，降低内存占用并提升滑动性能。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)
