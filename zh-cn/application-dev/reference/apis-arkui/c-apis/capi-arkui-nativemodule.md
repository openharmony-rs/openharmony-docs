# ArkUI_NativeModule

## 概述

Provides UI capabilities of ArkUI on the native side, such as UI component creation and destruction,tree node operations, attribute setting, and event listening.

**起始版本：** 26.0.0
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [native_material.h](capi-native-material-h.md) | 提供ArkUI在Native侧的沉浸式材质类型和API声明，用于实现半透明模糊背景、光感交互反馈等沉浸式UI效果。 |
| [native_animate.h](capi-native-animate-h.md) | 提供ArkUI在Native侧的动画接口定义集合。native_animate.h中的接口需要在主线程上调用。 |
| [native_type_visual.h](capi-native-type-visual-h.md) | Defines the visual effect types for the native module. |
| [native_node.h](capi-native-node-h.md) | Provides type definitions for <b>NativeNode</b> APIs. |
| [native_node_ani.h](capi-native-node-ani-h.md) | 提供ArkTS1.2的FrameNode转换NodeHandle的方式。 |
| [native_key_event.h](capi-native-key-event-h.md) | Declares the APIs of **NativeKeyEvent**. |
| [drag_and_drop.h](capi-drag-and-drop-h.md) | Declares the APIs of **NativeDrag**. |
| [native_interface.h](capi-native-interface-h.md) | Provides a unified entry for the native module APIs. |
| [native_interface_focus.h](capi-native-interface-focus-h.md) | Declares APIs for focus management, mainly used for actively transferring focus, managing the default focustransfer behavior, and controlling the focus activation state. |
| [native_type.h](capi-native-type-h.md) | Defines the common types for the native module. |
| [native_dialog.h](capi-native-dialog-h.md) | 提供ArkUI在Native侧的自定义弹窗接口定义集合。 |
| [error_code.h](capi-error-code-h.md) | Defines the error code for the native module. |
| [common_type.h](capi-common-type-h.md) | 定义ArkUI Native API的公共类型。 |
| [drawable_descriptor.h](capi-drawable-descriptor-h.md) | 提供NativeDrawableDescriptor接口的类型定义。 |
| [native_node_napi.h](capi-native-node-napi-h.md) | 提供ArkTS侧的{@link FrameNode}转换{@link NodeHandle}的方式。 |
| [styled_string.h](capi-styled-string-h.md) | 在Native侧定义[ArkUI_NodeType](capi-native-node-h.md#arkui_nodetype)为ARKUI_NODE_TEXT的组件的文本样式和文本布局管理器。 |
| [custom_span.h](capi-custom-span-h.md) | Defines a set of CustomSpan enum and interface. |
| [node_water_flow.h](capi-node-water-flow-h.md) | 定义WaterFlow组件相关的枚举和接口。 |
| [swiper.h](capi-swiper-h.md) | 定义Swiper组件的枚举和接口。 |
| [common_attributes.h](capi-common-attributes-h.md) | Defines the common property and method types for the native module. |
| [navigation_router.h](capi-navigation-router-h.md) | 定义Navigation或Router组件的枚举和接口。 |
| [node_scroll.h](capi-node-scroll-h.md) | 提供滚动方向、边缘效果、滚动条状态、内容裁剪、嵌套滚动、滚动状态和滚动来源等枚举，用于配置和监听Scroll组件及相关可滚动组件的行为。 |
| [node_grid.h](capi-node-grid-h.md) | 定义Grid组件相关的枚举和接口。 |
| [custom_attributes.h](capi-custom-attributes-h.md) | 为NativeNode API提供自定义节点事件定义。 |
| [xcomponent.h](capi-xcomponent-h.md) | XComponent组件的枚举类型定义。 |
| [rich_editor.h](capi-rich-editor-h.md) | Defines a set of RichEditor enum and interface. |
| [image_span.h](capi-image-span-h.md) | Defines a set of ImageSpan enum and interface. |
| [progress.h](capi-progress-h.md) | Defines a set of Progress enum and interface. |
| [slider.h](capi-slider-h.md) | Provides Slider node type definitions for <b>NativeNode</b> APIs. |
| [image_animator.h](capi-image-animator-h.md) | 为NativeNode API提供ImageAnimator节点类型定义。 |
| [layout.h](capi-layout-h.md) | Defines the layout-related types for the native module. |
| [text_common.h](capi-text-common-h.md) | Defines a set of text common enum and interface. |
| [text_input.h](capi-text-input-h.md) | Defines a set of TextInput enum and interface. |
| [checkbox.h](capi-checkbox-h.md) | Provides Checkbox node type definitions for <b>NativeNode</b> APIs. |
| [node_list.h](capi-node-list-h.md) | 定义List组件相关的枚举和接口。 |
| [text.h](capi-text-h.md) | Defines a set of Text enum and interface. |
| [image.h](capi-image-h.md) | 为NativeNode API提供Image节点类型定义。 |
| [embedded_component.h](capi-embedded-component-h.md) | EmbeddedComponent组件相关的结构体和方法定义。 |
| [picker.h](capi-picker-h.md) | 为NativeNode API提供Picker节点类型定义，支持日期选择器、文本选择器等多种类型的选择器组件，适用于需要在原生层实现滚动选择功能的场景，提供了丰富的样式配置和数据联动能力，帮助开发者灵活构建各类选择交互。 |
| [button.h](capi-button-h.md) | Provides Button node type definitions for <b>NativeNode</b> APIs. |
| [text_area.h](capi-text-area-h.md) | Defines a set of TextArea enum and interface. |
