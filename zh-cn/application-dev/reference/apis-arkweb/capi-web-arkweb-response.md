# ArkWeb_Response_
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

```c
typedef struct ArkWeb_Response_ ArkWeb_Response
```

## 概述

ArkWeb_Response是用于构建自定义HTTP响应的结构体，定义了响应状态码、响应头、响应体等核心字段。该结构体配合ArkWeb_ResourceHandler使用，在Scheme请求拦截场景中为被拦截的请求提供完整的HTTP响应数据，实现自定义的资源返回能力。

**起始版本：** 12

**相关模块：** [Web](capi-web.md)

**所在头文件：** [arkweb_scheme_handler.h](capi-arkweb-scheme-handler-h.md)

