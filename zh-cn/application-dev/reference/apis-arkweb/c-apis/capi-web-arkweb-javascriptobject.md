# ArkWeb_JavaScriptObject

```c
typedef struct ArkWeb_JavaScriptObject {...} ArkWeb_JavaScriptObject
```

## 概述

Defines the javascript object.

**起始版本：** 12

**相关模块：** [Web](capi-web.md)

**所在头文件：** [arkweb_type.h](capi-arkweb-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| const uint8_t* buffer | 注入的JavaScript代码。该缓冲区长度需与size参数一致。 |
| size_t size | JavaScript代码长度。单位：字节。需与buffer的实际长度一致，否则可能导致越界或截断。 |
| [ArkWeb_OnJavaScriptCallback](capi-arkweb-type-h.md#arkweb_onjavascriptcallback) callback | JavaScript执行完成的回调。回调函数指针，传入NULL表示不需要回调。 |
| void* userData | 需要在回调中携带的自定义数据。 |


