# ArkWeb_JavaScriptObject
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

```c
typedef struct {...} ArkWeb_JavaScriptObject
```

## 概述

**ArkWeb_JavaScriptObject** 结构体用于向Web页面注入JavaScript代码并获取执行结果。开发者可通过该结构体指定待注入的JavaScript脚本内容及长度，注册执行完成回调，并通过userData传递自定义上下文数据。该结构体通常与相关接口配合使用，实现Web与原生应用之间的数据交互。

**起始版本：** 12

**相关模块：** [Web](capi-web.md)

**所在头文件：** [arkweb_type.h](capi-arkweb-type-h.md)

## 汇总

### 成员变量

| 名称                                                                                        | 描述 |
|-------------------------------------------------------------------------------------------| -- |
| const uint8_t* buffer                                                                     | 注入的JavaScript代码。 |
| size_t size                                                                               | JavaScript代码长度。单位：字节 |
| [ArkWeb_OnJavaScriptCallback](capi-arkweb-type-h.md#arkweb_onjavascriptcallback) callback | JavaScript执行完成的回调。 |
| void* userData                                                                            | 需要在回调中携带的自定义数据。 |

