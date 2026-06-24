# Input_CursorConfig

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->

```c
typedef struct Input_CursorConfig Input_CursorConfig
```

## 概述

自定义鼠标光标配置，用于定义和管理应用程序中鼠标光标的显示样式和交互行为。支持设置不同类型的光标样式（如默认、手形、文本输入等），为用户提供更直观的操作反馈，提升用户体验。

**起始版本：** 22

**相关模块：** [input](capi-input.md)

**所在头文件：** [oh_input_manager.h](capi-oh-input-manager-h.md)

**相关接口：**

| 名称 | 描述 |
| -- | -- |
| [OH_Input_CursorConfig_Create](capi-oh-input-manager-h.md#oh_input_cursorconfig_create) | 创建自定义鼠标光标配置对象。通过调用[OH_Input_CursorConfig_Destroy](capi-oh-input-manager-h.md#oh_input_cursorconfig_destroy)销毁自定义鼠标光标配置对象。 |
| [OH_Input_CursorConfig_Destroy](capi-oh-input-manager-h.md#oh_input_cursorconfig_destroy) | 销毁自定义鼠标光标配置对象。 |
