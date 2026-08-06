# Input_Hotkey

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->

```c
typedef struct Input_Hotkey Input_Hotkey
```

## 概述

定义快捷键结构体，用于描述快捷键的按键组合、触发条件和回调处理等设计逻辑，支持应用注册和管理自定义快捷键。

**起始版本：** 14

**相关模块：** [input](capi-input.md)

**所在头文件：** [oh_input_manager.h](capi-oh-input-manager-h.md)

**相关接口：**

| 名称 | 描述 |
| -- | -- |
| [OH_Input_CreateHotkey](capi-oh-input-manager-h.md#oh_input_createhotkey) | 创建快捷键对象。通过调用[OH_Input_DestroyHotkey](capi-oh-input-manager-h.md#oh_input_destroyhotkey)销毁快捷键对象。 |
| [OH_Input_DestroyHotkey](capi-oh-input-manager-h.md#oh_input_destroyhotkey) | 销毁快捷键对象。 |
