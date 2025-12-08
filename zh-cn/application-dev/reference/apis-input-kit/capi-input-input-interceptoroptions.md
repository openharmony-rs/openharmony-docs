# Input_InterceptorOptions

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct Input_InterceptorOptions Input_InterceptorOptions
```

## 概述

事件拦截选项。

**起始版本：** 12

**相关模块：** [input](capi-input.md)

**所在头文件：** [oh_input_manager.h](capi-oh-input-manager-h.md)

**相关接口：**

| 名称 | 描述 |
| -- | -- |
| [OH_Input_AddKeyEventInterceptor](capi-oh-input-manager-h.md#oh_input_addkeyeventinterceptor) | 添加按键事件的拦截，重复添加只有第一次生效。仅在应用获焦时拦截按键事件。 |
| [OH_Input_RemoveKeyEventInterceptor](capi-oh-input-manager-h.md#oh_input_removekeyeventinterceptor) | 移除按键事件拦截。 |
| [OH_Input_AddInputEventInterceptor](capi-oh-input-manager-h.md#oh_input_addinputeventinterceptor) | 添加输入事件拦截，包括鼠标、触屏和轴事件，重复添加只有第一次生效。仅命中应用窗口时拦截输入事件。 |
| [OH_Input_RemoveInputEventInterceptor](capi-oh-input-manager-h.md#oh_input_removeinputeventinterceptor) | 移除输入事件拦截，包括鼠标、触屏和轴事件。 |
