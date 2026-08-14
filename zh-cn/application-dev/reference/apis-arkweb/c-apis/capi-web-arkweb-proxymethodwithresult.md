# ArkWeb_ProxyMethodWithResult

```c
typedef struct ArkWeb_ProxyMethodWithResult {...} ArkWeb_ProxyMethodWithResult
```

## 概述

ArkWeb_ProxyMethodWithResult是带返回值的JavaScript代理方法结构体，扩展了ArkWeb_ProxyMethod的能力，支持在JavaScript调用Native方法后获取返回值。该结构体在方法名称和回调函数的基础上，增加了返回值处理能力，适用于需要向Web前端返回执行结果的调用场景。

**起始版本：** 18

**相关模块：** [Web](capi-web.md)

**所在头文件：** [arkweb_type.h](capi-arkweb-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| const char* methodName | 注入的方法名。 |
| [ArkWeb_OnJavaScriptProxyCallbackWithResult](capi-arkweb-type-h.md#arkweb_onjavascriptproxycallbackwithresult) callback | JavaScript调用Native代理方法时执行的回调函数，用于处理方法调用并返回执行结果。该参数必须为有效的函数指针，不能为NULL。 |
| void* userData | 需要在回调中携带的自定义数据。 |


