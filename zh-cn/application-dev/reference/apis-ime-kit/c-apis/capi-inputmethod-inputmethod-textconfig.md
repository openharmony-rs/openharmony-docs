# InputMethod_TextConfig

```c
typedef struct InputMethod_TextConfig InputMethod_TextConfig
```

## 概述

文本输入框的文本输入行为配置结构体，用于输入框向输入法框架传递核心输入规则，输入法框架根据配置执行相应输入行为。通过配置输入属性（如输入类型、文本格式等），能够满足不同场景下的输入需求，提升用户输入体验，适用于需要精细化控制输入行为的文本输入场景。该结构体为不透明类型（opaque type），调用者不可直接访问其内部成员，仅可通过本模块提供的函数接口进行操作。

**起始版本：** 12

**相关模块：** [InputMethod](capi-inputmethod.md)

**所在头文件：** [inputmethod_text_config_capi.h](capi-inputmethod-text-config-capi-h.md)

