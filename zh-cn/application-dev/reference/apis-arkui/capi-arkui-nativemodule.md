# ArkUI_NativeModule
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @piggyguy; @wangyang2022-->
<!--Designer: @piggyguy; @wangyang2022-->
<!--Tester: @fredyuan912-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

提供ArkUI在Native侧的通用拖拽及主动发起拖拽能力。更多详细介绍请参考[绑定拖拽事件](../../ui/ndk-drag-event.md)。

提供ArkUI在Native侧的通用按键事件能力。

提供ArkUI在Native侧的注册手势回调的能力。更多详细介绍请参考[绑定手势事件](../../ui/ndk-bind-gesture-events.md)。

提供ArkUI在Native侧使用动画回调的能力。更多详细介绍请参考[使用动画](../../ui/ndk-use-animation.md)。

提供ArkUI在Native侧的UI能力，如UI组件创建销毁、树节点操作、属性设置、事件监听等。更多详细介绍请参考[接入ArkTS页面](../../ui/ndk-access-the-arkts-page.md)。

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
| [native_type.h](capi-native-type-h.md) | 提供NativeModule公共的类型定义。 |
| [text.h](capi-text-h.md) | 定义Text相关的枚举和接口，用于配置文本样式、控制跑马灯效果、实现文本实体识别以及管理文本控制器等功能。适用于需要自定义文本显示效果、实现动态文本交互、识别文本中特殊实体（如地址、电话号码）以及精确控制文本字体粗细等场景。通过这些配置接口，开发者可以灵活控制文本组件的显示效果和交互行为，提升用户体验。 |
| [text_common.h](capi-text-common-h.md) | 定义文本类组件通用的枚举和接口，涵盖文本对齐、装饰线样式、复制粘贴、溢出处理、断行策略、菜单定制等多种能力，适用于文本输入框、文本显示等场景，帮助开发者灵活控制文本样式与交互行为，降低开发复杂度。 |
| [text_input.h](capi-text-input-h.md) | 定义TextInput相关的枚举。支持多种输入类型配置（包括文本、数字、密码、邮箱、电话号码等）、清除按钮样式定制、自动填充内容类型设置和输入框风格选择，适用于登录注册、表单填写、搜索输入等需要用户交互输入的场景，帮助开发者快速实现符合业务需求的单行文本输入功能。 |
| [text_area.h](capi-text-area-h.md) | 定义TextArea相关的枚举类型。TextArea组件用于接收多行文本输入，枚举值用于指定不同的输入类型，会影响输入内容的验证规则，例如支持基本输入、纯数字、电话号码、邮箱地址、验证码等模式。开发者可根据表单类型选择合适的枚举值，系统将自动提供对应的内容验证，从而优化用户输入体验并确保数据格式的正确性。 |
| [image_span.h](capi-image-span-h.md) | 定义ImageSpan相关的枚举，用于在富文本中嵌入图片并控制图片与文本的对齐方式。支持多种对齐模式，适用于图文混排场景，可实现图片与文本的精确对齐，提升富文本的展示效果。 |
| [progress.h](capi-progress-h.md) | 定义Progress相关的枚举和接口，支持线性、环形、圆形、胶囊等多种进度条类型，并提供线性进度条样式选项的自定义能力（平滑动效、扫光效果、宽度、圆角），适用于需要展示任务进度、加载状态等场景，帮助开发者快速实现多样化的进度展示和交互反馈。 |
| [rich_editor.h](capi-rich-editor-h.md) | 定义RichEditor相关的枚举和接口。 |
| [custom_span.h](capi-custom-span-h.md) | 定义CustomSpan相关的结构体和接口，用于实现自定义绘制Span的精确尺寸测量、布局排版和绘制效果。支持开发者在富文本编辑器、聊天应用、文档应用等场景中实现图文混排、表情内嵌、自定义标记等功能，提供灵活的自定义绘制Span能力，帮助开发者提升开发效率，实现更丰富的文本排版效果。 |
| [styled_string.h](capi-styled-string-h.md) | 提供ArkUI在Native侧的属性字符串能力。 |
