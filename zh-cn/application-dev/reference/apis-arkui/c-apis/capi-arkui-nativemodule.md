# ArkUI_NativeModule

## 概述

Provides UI capabilities of ArkUI on the native side, such as UI component creation and destruction,tree node operations, attribute setting, and event listening.

**起始版本：** 26.0.0

## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [native_material.h](capi-native-material-h.md) | 提供ArkUI（方舟UI框架）在Native侧的沉浸式材质类型和API声明，用于实现半透明模糊背景、光感交互反馈等沉浸式UI效果。 |
| [native_gesture.h](capi-native-gesture-h.md) | 提供NativeGesture接口的类型定义，支持手势识别器、手势事件、手势打断、触摸识别器、手势收集干预以及手势参数查询与设置等能力，适用于应用通过Native接口处理手势识别、手势冲突和手势收集干预等场景。手势识别管线按优先级和竞争规则进行识别，可通过打断回调拦截手势；手势收集干预机制允许在手势收集阶段动态干预手势的收集流程。 |
| [native_animate.h](capi-native-animate-h.md) | 提供ArkUI（方舟UI框架）在Native侧的动画接口定义集合。native_animate.h中的接口需要在主线程上调用。 |
| [native_type_visual.h](capi-native-type-visual-h.md) | 提供NativeModule视觉相关的类型定义。 |
| [native_node.h](capi-native-node-h.md) | Provides type definitions for <b>NativeNode</b> APIs. |
| [native_node_ani.h](capi-native-node-ani-h.md) | 提供ArkTS1.2的FrameNode转换NodeHandle的方式。 |
| [native_key_event.h](capi-native-key-event-h.md) | 提供NativeKeyEvent相关接口定义。 |
| [drag_and_drop.h](capi-drag-and-drop-h.md) | 提供NativeDrag相关接口定义。 |
| [native_interface.h](capi-native-interface-h.md) | Provides a unified entry for the native module APIs. |
| [native_interface_focus.h](capi-native-interface-focus-h.md) | 定义焦点管理接口，主要用于主动转移焦点、清除焦点、管理焦点转移默认行为、控制焦点激活态，以及设置按键事件的处理模式。适用于页面切换、键盘导航等需要统一管理焦点状态和焦点转移行为的场景，有助于提升焦点控制的可预测性和交互体验。 |
| [native_type.h](capi-native-type-h.md) | Defines the common types for the native module. |
| [native_dialog.h](capi-native-dialog-h.md) | 提供ArkUI在Native侧的自定义弹窗接口定义集合。 |
| [error_code.h](capi-error-code-h.md) | Defines the error code for the native module. |
| [common_type.h](capi-common-type-h.md) | 定义ArkUI Native API的公共类型。 |
| [drawable_descriptor.h](capi-drawable-descriptor-h.md) | 提供NativeDrawableDescriptor接口的类型定义。 |
| [native_node_napi.h](capi-native-node-napi-h.md) | 提供ArkTS侧的{@link FrameNode}转换{@link NodeHandle}的方式。 |
| [styled_string.h](capi-styled-string-h.md) | 在Native侧定义{@link ArkUI_NodeType}为ARKUI_NODE_TEXT的组件的文本样式和文本布局管理器。 |
| [custom_span.h](capi-custom-span-h.md) | 定义CustomSpan相关的结构体和接口，用于实现自定义绘制Span的精确尺寸测量、布局排版和绘制效果。支持开发者在富文本编辑器、聊天应用、文档应用等场景中实现图文混排、表情内嵌、自定义标记等功能，提供灵活的自定义绘制Span能力，帮助开发者提升开发效率，实现更丰富的文本排版效果。 |
| [water_flow.h](capi-water-flow-h.md) | 定义WaterFlow组件相关的枚举和接口。 |
| [swiper.h](capi-swiper-h.md) | 定义Swiper组件的枚举和接口。 |
| [common_attributes.h](capi-common-attributes-h.md) | Defines the common property and method types for the native module. |
| [navigation_router.h](capi-navigation-router-h.md) | 定义Navigation或Router组件的枚举和接口。 |
| [scroll.h](capi-scroll-h.md) | 提供滚动方向、边缘效果、滚动条状态、内容裁剪、嵌套滚动、滚动状态和滚动来源等枚举，用于配置和监听Scroll组件及相关可滚动组件的行为。 |
| [list_item.h](capi-list-item-h.md) | Provides shared list item-related type and function definitions for <b>NativeNode</b> APIs. |
| [grid.h](capi-grid-h.md) | 定义Grid组件相关的枚举和接口。 |
| [custom_attributes.h](capi-custom-attributes-h.md) | 为NativeNode API提供自定义节点事件定义。 |
| [xcomponent.h](capi-xcomponent-h.md) | XComponent组件枚举类型定义，用于描述XComponent的渲染类型，支持EGL/OpenGLES绘制及媒体数据写入场景，可满足开发者定制内容单独或与组件合成展示的渲染需求。 |
| [rich_editor.h](capi-rich-editor-h.md) | 定义文本编辑器相关的结构体、枚举和函数。文本编辑器提供富文本编辑能力，支持自定义文本选择菜单、属性字符串控制器、段落样式和文本样式设置，以及触感反馈控制等功能，适用于需要在应用中实现富文本编辑和自定义交互菜单的场景。 |
| [image_span.h](capi-image-span-h.md) | 定义ImageSpan相关的枚举，用于在富文本中嵌入图片并控制图片与文本的对齐方式。支持多种对齐模式，适用于图文混排场景，可实现图片与文本的精确对齐，提升富文本的展示效果。 |
| [progress.h](capi-progress-h.md) | 定义Progress相关的枚举和接口，支持线性、环形、圆形、胶囊等多种进度条类型，并提供线性进度条样式选项的自定义能力（平滑动效、扫光效果、宽度、圆角），适用于需要展示任务进度、加载状态等场景，帮助开发者快速实现多样化的进度展示和交互反馈。 |
| [slider.h](capi-slider-h.md) | Provides Slider node type definitions for <b>NativeNode</b> APIs. |
| [image_animator.h](capi-image-animator-h.md) | 为NativeNode API提供ImageAnimator节点类型定义。 |
| [layout.h](capi-layout-h.md) | Defines the layout-related types for the native module. |
| [text_common.h](capi-text-common-h.md) | 定义文本类组件通用的枚举和接口，涵盖文本对齐、装饰线样式、复制粘贴、溢出处理、断行策略、菜单定制等多种能力，适用于文本输入框、文本显示等场景，帮助开发者灵活控制文本样式与交互行为，降低开发复杂度。 |
| [text_input.h](capi-text-input-h.md) | 定义TextInput相关的枚举。支持多种输入类型配置（包括文本、数字、密码、邮箱、电话号码等）、清除按钮样式定制、自动填充内容类型设置和输入框风格选择，适用于登录注册、表单填写、搜索输入等需要用户交互输入的场景，帮助开发者快速实现符合业务需求的单行文本输入功能。 |
| [checkbox.h](capi-checkbox-h.md) | Provides Checkbox node type definitions for <b>NativeNode</b> APIs. |
| [list.h](capi-list-h.md) | 定义List组件相关的枚举和接口。 |
| [text.h](capi-text-h.md) | 定义Text相关的枚举和接口，用于配置文本样式、控制跑马灯效果、实现文本实体识别以及管理文本控制器等功能。适用于需要自定义文本显示效果、实现动态文本交互、识别文本中特殊实体（如地址、电话号码）以及精确控制文本字体粗细等场景。通过这些配置接口，开发者可以灵活控制文本组件的显示效果和交互行为，提升用户体验。 |
| [image.h](capi-image-h.md) | 为NativeNode API提供Image节点类型定义。 |
| [embedded_component.h](capi-embedded-component-h.md) | 声明EmbeddedComponent组件选项（ArkUI_EmbeddedComponentOption）相关的结构体和方法。开发者可通过这些方法创建、销毁组件选项对象，并为EmbeddedComponent组件设置运行异常回调（onError）和正常退出回调（onTerminated）。适用于需要在应用中嵌入EmbeddedUIExtensionAbility组件并管理其生命周期、监听运行异常与正常退出事件的应用场景，帮助开发者灵活处理组件运行过程中的状态变化。 |
| [picker.h](capi-picker-h.md) | 为NativeNode API提供Picker节点类型定义，支持日期选择器、文本选择器等多种类型的选择器组件，适用于需要在原生层实现滚动选择功能的场景，提供了丰富的样式配置和数据联动能力，帮助开发者灵活构建各类选择交互。 |
| [button.h](capi-button-h.md) | Provides Button node type definitions for <b>NativeNode</b> APIs. |
| [text_area.h](capi-text-area-h.md) | 定义TextArea相关的枚举类型。TextArea组件用于接收多行文本输入，枚举值用于指定不同的输入类型，会影响输入内容的验证规则，例如支持基本输入、纯数字、电话号码、邮箱地址、验证码等模式。开发者可根据表单类型选择合适的枚举值，系统将自动提供对应的内容验证，从而优化用户输入体验并确保数据格式的正确性。 |
