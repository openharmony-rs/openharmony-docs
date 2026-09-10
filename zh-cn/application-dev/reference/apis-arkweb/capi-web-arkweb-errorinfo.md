# ArkWeb_ErrorInfo_
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @aohui-->
<!--Designer: @yaomingliu-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

```c
typedef struct ArkWeb_ErrorInfo_ ArkWeb_ErrorInfo
```

## 概述

ArkWeb_ErrorInfo是响应错误详情结构体，用于在自定义Scheme请求拦截场景中设置响应的错误信息。开发者可以通过该结构体设置错误码、自定义错误码以及是否在未收到响应时自动生成响应。该结构体通常与ArkWeb_ResourceHandler配合使用，在请求失败时通过OH_ArkWebResourceHandler_DidFailWithErrorInfo传递错误信息。

**起始版本：** 26.1.0

**相关模块：** [Web](capi-web.md)

**所在头文件：** [arkweb_scheme_handler.h](capi-arkweb-scheme-handler-h.md)
