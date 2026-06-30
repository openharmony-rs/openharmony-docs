# ArkWeb_ProxyObject
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

```c
typedef struct {...} ArkWeb_ProxyObject
```

## 概述

ArkWeb_ProxyObject是注入到Web页面的JavaScript代理对象结构体，用于将一组相关的ArkWeb_ProxyMethod方法组织成对象整体暴露给Web前端。该结构体指定了对象在JavaScript中的名称（objName）、包含的方法数组（methodList）和方法数量（size），使得Native应用可以向Web页面暴露结构化的API集合。

**起始版本：** 12

**相关模块：** [Web](capi-web.md)

**所在头文件：** [arkweb_type.h](capi-arkweb-type-h.md)

## 汇总

### 成员变量

| 名称                                       | 描述 |
|------------------------------------------| -- |
| const char* objName                      | 注入的对象名。 |
| const [ArkWeb_ProxyMethod](capi-web-arkweb-proxymethod.md)* methodList | 注入的对象携带的方法结构体数组。 |
| size_t size                              | 方法结构体数组的长度。 |


