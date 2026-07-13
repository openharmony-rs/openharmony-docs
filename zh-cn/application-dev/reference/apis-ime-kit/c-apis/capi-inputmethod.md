# InputMethod

## 概述

InputMethod模块提供方法来使用输入法和开发输入法。

**起始版本：** 12
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [inputmethod_cursor_info_capi.h](capi-inputmethod-cursor-info-capi-h.md) | 提供光标信息对象的创建、销毁与读写方法。 |
| [inputmethod_attach_options_capi.h](capi-inputmethod-attach-options-capi-h.md) | 提供输入法绑定选项对象的创建、销毁与读写方法，用于管理应用绑定输入法时的配置参数。 |
| [inputmethod_controller_capi.h](capi-inputmethod-controller-capi-h.md) | 提供绑定、解绑输入法的方法，是应用与输入法服务交互的核心入口。 |
| [inputmethod_text_config_capi.h](capi-inputmethod-text-config-capi-h.md) | 提供输入框配置信息对象的创建、销毁与读写方法。InputMethod_TextConfig承载编辑框的配置信息，在GetTextConfigFunc回调中使用，开发者需在回调内对config参数设置各配置项。 |
| [inputmethod_text_editor_proxy_capi.h](capi-inputmethod-text-editor-proxy-capi-h.md) | 提供一套方法支持应用开发的自绘输入框获取来自输入法应用的通知和请求。该模块采用回调机制实现输入法应用与自绘输入框之间的双向通信。 |
| [inputmethod_types_capi.h](capi-inputmethod-types-capi-h.md) | 提供了输入法相关的类型定义，包含键盘状态、回车键功能类型，光标移动方向等。这些类型定义用于描述输入法应用与编辑框客户端之间的交互行为。键盘状态定义了软键盘的显示和隐藏状态；回车键功能类型定义了在不同输入场景下回车键的触发行为；光标移动方向定义了光标在编辑框中的移动操作。 |
| [inputmethod_private_command_capi.h](capi-inputmethod-private-command-capi-h.md) | 提供私有数据对象的创建、销毁与读写方法。InputMethod_PrivateCommand采用key-value机制，支持输入法应用与编辑框客户端之间传递自定义私有数据，用于扩展输入法功能、传递特定场景指令或交换自定义配置信息。 |
| [inputmethod_inputmethod_proxy_capi.h](capi-inputmethod-inputmethod-proxy-capi-h.md) | 提供使用输入法的方法，可以向输入法应用发送请求和通知，适用于需要控制输入法显示、隐藏、配置变更通知等功能的应用开发场景。 |
| [inputmethod_text_avoid_info_capi.h](capi-inputmethod-text-avoid-info-capi-h.md) | 提供输入框避让信息对象的创建、销毁与读写方法，用于在软键盘弹起时动态调整输入框的位置，避免遮挡输入内容。 |
