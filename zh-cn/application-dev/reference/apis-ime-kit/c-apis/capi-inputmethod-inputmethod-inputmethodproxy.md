# InputMethod_InputMethodProxy

```c
typedef struct InputMethod_InputMethodProxy InputMethod_InputMethodProxy
```

## 概述

应用与输入法服务之间的交互代理对象，应用可通过此对象调用输入法服务的相关接口，并接收输入法服务的事件回调。该结构体为不透明类型（opaque type），调用者不可直接访问其内部成员，仅可通过本模块提供的函数接口进行操作。

**起始版本：** 12

**相关模块：** [InputMethod](capi-inputmethod.md)

**所在头文件：** [inputmethod_inputmethod_proxy_capi.h](capi-inputmethod-inputmethod-proxy-capi-h.md)

