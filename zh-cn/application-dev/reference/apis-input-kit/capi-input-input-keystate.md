# Input_KeyState

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->

```c
typedef struct Input_KeyState Input_KeyState;
```

## 概述

定义按键信息，用于标识按键行为。例如，“Ctrl”按键信息包含键值和键状态。适用于快捷键处理、输入事件状态管理、按键状态检测等场景。

**起始版本：** 12

**相关模块：** [input](capi-input.md)

**所在头文件：** [oh_input_manager.h](capi-oh-input-manager-h.md)

**相关接口：**

| 名称 | 描述 |
| -- | -- |
| [OH_Input_CreateKeyState](capi-oh-input-manager-h.md#oh_input_createkeystate) | 创建按键状态的结构体对象。通过调用[OH_Input_DestroyKeyState](capi-oh-input-manager-h.md#oh_input_destroykeystate)销毁按键状态的结构体对象。 |
| [OH_Input_DestroyKeyState](capi-oh-input-manager-h.md#oh_input_destroykeystate) | 销毁按键状态的枚举对象。 |
