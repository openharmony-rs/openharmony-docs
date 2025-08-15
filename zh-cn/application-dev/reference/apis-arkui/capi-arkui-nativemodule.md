# ArkUI_NativeModule
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @piggyguy; @xiang-shouxing; @yangfan229-->
<!--Designer: @piggyguy; @xiang-shouxing; @yangfan229-->
<!--Tester: @fredyuan912-->
<!--Adviser: @HelloCrease-->

## 概述

提供ArkUI在Native侧的通用拖拽及主动发起拖拽能力。更多详细介绍请参考[拖拽事件](../../ui/ndk-drag-event.md)。

提供ArkUI在Native侧的通用按键事件能力。

提供ArkUI在Native侧的注册手势回调的能力。更多详细介绍请参考[绑定手势事件](../../ui/ndk-bind-gesture-events.md)。

提供ArkUI在Native侧动画回调的能力。更多详细介绍请参考[使用动画](../../ui/ndk-use-animation.md)。

提供ArkUI在Native侧的UI能力，如UI组件创建销毁、树节点操作，属性设置，事件监听等。更多详细介绍请参考[接入ArkTS页面](../../ui/ndk-access-the-arkts-page.md)。

**起始版本：** 12

## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [drag_and_drop.h](capi-drag-and-drop-h.md) | 提供NativeDrag相关接口定义。 |
| [drawable_descriptor.h](capi-drawable-descriptor-h.md) | 提供NativeDrawableDescriptor接口的类型定义。 |
| [native_animate.h](capi-native-animate-h.md) | 提供ArkUI在Native侧的动画接口定义集合。 |
| [native_dialog.h](capi-native-dialog-h.md) | 提供ArkUI在Native侧的自定义弹窗接口定义集合。 |
| [native_gesture.h](capi-native-gesture-h.md) | 提供NativeGesture接口的类型定义。 |
| [native_interface.h](capi-native-interface-h.md) | 提供NativeModule接口的统一入口函数。 |
| [native_interface_focus.h](capi-native-interface-focus-h.md) | 定义焦点管理的相关接口，主要用于主动转移焦点或管理控制焦点转移默认行为，控制焦点激活态。 |
| [native_key_event.h](capi-native-key-event-h.md) | 提供NativeKeyEvent相关接口定义。 |
| [native_node.h](capi-native-node-h.md) | 提供NativeNode接口的类型定义。 |
| [native_node_napi.h](capi-native-node-napi-h.md) | 提供ArkTS侧的FrameNode转换NodeHandle的方式。 |
| [native_render.h](capi-native-render-h.md) | 提供Native侧的RenderNode的类型定义和操作RenderNode节点的能力。 |
| [native_type.h](capi-native-type-h.md) | 提供NativeModule公共的类型定义。 |
| [styled_string.h](capi-styled-string-h.md) | 提供ArkUI在Native侧的属性字符串能力。 |
