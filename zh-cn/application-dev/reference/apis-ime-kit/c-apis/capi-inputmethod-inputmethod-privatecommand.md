# InputMethod_PrivateCommand

```c
typedef struct InputMethod_PrivateCommand InputMethod_PrivateCommand
```

## 概述

私有命令结构体，采用key-value机制，作为输入框与输入法应用之间传递私有数据的载体。可用于传递自定义指令、扩展能力参数和特定场景数据，提升输入法功能的扩展性和兼容性。每个PrivateCommand实例包含一个key（标识符字符串）和一个value（布尔值、整数或字符串，三种类型只能选择一种），value的数据类型由InputMethod_CommandValueType标识。

**起始版本：** 12

**相关模块：** [InputMethod](capi-inputmethod.md)

**所在头文件：** [inputmethod_private_command_capi.h](capi-inputmethod-private-command-capi-h.md)

