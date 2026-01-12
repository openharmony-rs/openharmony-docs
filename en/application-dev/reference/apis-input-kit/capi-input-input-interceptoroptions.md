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

## **Overview**

Defines event interception options.

**Since**: 12

**Related module**: [input](capi-input.md)

**Header file**: [oh_input_manager.h](capi-oh-input-manager-h.md)

**Related APIs**:

| Name| Description|
| -- | -- |
| [OH_Input_AddKeyEventInterceptor](capi-oh-input-manager-h.md#oh_input_addkeyeventinterceptor) | Adds an interceptor for key events. If multiple interceptors are added, only the first one takes effect. Key events are intercepted only when the application gains focus.|
| [OH_Input_RemoveKeyEventInterceptor](capi-oh-input-manager-h.md#oh_input_removekeyeventinterceptor) | Removes the interceptor for key events.|
| [OH_Input_AddInputEventInterceptor](capi-oh-input-manager-h.md#oh_input_addinputeventinterceptor) | Adds an interceptor for input events, including mouse, touch, and axis events. If multiple interceptors are added, only the first one takes effect. Key events are intercepted only when the application window is hit.|
| [OH_Input_RemoveInputEventInterceptor](capi-oh-input-manager-h.md#oh_input_removeinputeventinterceptor) | Removes the interceptor for input events, including mouse, touch, and axis events.|
