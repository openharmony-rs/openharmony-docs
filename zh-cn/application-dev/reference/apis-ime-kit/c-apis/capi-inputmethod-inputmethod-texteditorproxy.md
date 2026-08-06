# InputMethod_TextEditorProxy

```c
typedef struct InputMethod_TextEditorProxy InputMethod_TextEditorProxy
```

## 概述

输入法文本编辑器代理类。用于处理输入法应用与文本编辑器之间的交互，提供接收输入法请求和通知的方法，适用于需要实现输入法与编辑器双向通信的场景。该结构体为不透明类型（opaque type），调用者不可直接访问其内部成员，仅可通过本模块提供的函数接口进行操作。

**起始版本：** 12

**相关模块：** [InputMethod](capi-inputmethod.md)

**所在头文件：** [inputmethod_text_editor_proxy_capi.h](capi-inputmethod-text-editor-proxy-capi-h.md)

