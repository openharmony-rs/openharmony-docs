# Web

## 概述

提供ArkWeb中拦截和自定义网络请求的C API。

**起始版本：** 12
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [arkweb_scheme_handler.h](capi-arkweb-scheme-handler-h.md) | arkweb_scheme_handler.h是ArkWeb中用于拦截和自定义网络请求的完整C API头文件。该模块定义了注册自定义Scheme拦截器的ArkWeb_SchemeHandler、发送自定义响应的ArkWeb_ResourceHandler、构建HTTP响应的ArkWeb_Response、检查请求详情的ArkWeb_ResourceRequest，以及用于读取上传数据的ArkWeb_HttpBodyStream和访问请求头的ArkWeb_RequestHeaderList。该API配合ArkWeb_NativeAPIVariantKind系统使用，通过OH_ArkWeb_SetSchemeHandler或OH_ArkWebServiceWorker_SetSchemeHandler注册。开发者可以实现自定义协议的资源加载和响应，适用于本地资源替换、数据加密传输、离线缓存等场景，通过拦截和自定义网络请求，帮助开发者解决标准协议无法满足的特殊业务需求，提升应用的安全性和数据控制能力，优化网络资源加载效率。 |
| [arkweb_interface.h](capi-arkweb-interface-h.md) | `arkweb_interface.h`是ArkWeb在Native侧（C/C++）的核心入口头文件：它定义了基础Native API类型[ArkWeb_AnyNativeAPI](capi-web-arkweb-anynativeapi.md)与API类型枚举[ArkWeb_NativeAPIVariantKind](capi-arkweb-interface-h.md#arkweb_nativeapivariantkind)，并提供[OH_ArkWeb_GetNativeAPI](capi-arkweb-interface-h.md#oh_arkweb_getnativeapi)接口用于按需获取Controller、Component、CookieManager等具体Native API结构体，同时提供[OH_ArkWeb_RegisterScrollCallback](capi-arkweb-interface-h.md#oh_arkweb_registerscrollcallback)用于注册Web组件滚动事件回调；当开发者需要在Native代码中控制Web组件行为（如执行JavaScript、管理Cookie、监听组件生命周期或滚动事件）时，应首先通过本头文件获取对应的Native API，而页面渲染显示等能力仍需由ArkTS侧的Web组件提供。 |
| [arkweb_error_code.h](capi-arkweb-error-code-h.md) | 声明ArkWeb NDK接口异常错误码，用于在ArkWeb相关接口调用失败时返回具体的错误信息，帮助开发者快速定位和解决问题。这些错误码覆盖了初始化、参数校验、URL处理、Cookie管理、库加载等常见异常场景。 |
| [arkweb_net_error_list.h](capi-arkweb-net-error-list-h.md) | 声明ArkWeb网络协议栈错误码。该枚举定义了ArkWeb网络协议栈中可能出现的各种错误类型，覆盖网络连接、SSL/TLS、证书验证、HTTP/2、QUIC、缓存等多个方面的错误场景。开发者可以通过这些错误码快速定位网络请求失败的原因，便于进行故障诊断和错误处理。 |
| [native_interface_arkweb.h](capi-native-interface-arkweb-h.md) | native_interface_arkweb.h是ArkWeb Native API的核心入口头文件，定义了应用与ArkWeb引擎交互所需的枚举、结构体和NDK函数接口，涵盖JavaScript执行与代理注入、Cookie管理、无白屏加载控制、内核版本选择等功能。该模块适用于需要通过Native方式与Web组件进行深度交互的场景，解决了ArkWeb组件的复杂能力（如JavaScript双向通信、Cookie持久化、内核版本切换）在ArkTS层无法直接调用的技术难题，为开发者提供了完整的底层控制能力，能够实现高性能、可定制的Web组件功能。 |
| [arkweb_type.h](capi-arkweb-type-h.md) | 提供ArkWeb在Native侧的公共类型定义。 |
