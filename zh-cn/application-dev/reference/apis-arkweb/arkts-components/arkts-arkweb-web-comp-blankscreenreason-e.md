# BlankScreenReason

```TypeScript
declare enum BlankScreenReason
```

白屏归因的具体原因，从网络层、资源层、渲染与JS层、内核与进程层、容器层标识白屏问题的根因，帮助开发者快速定位白屏问题来源，提升页面加载问题的排查效率和用户体验。

**起始版本：** 26.0.1

<!--Device-unnamed-declare enum BlankScreenReason--><!--Device-unnamed-declare enum BlankScreenReason-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## CERT_ERROR

```TypeScript
CERT_ERROR = 106
```

发生证书错误。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlankScreenReason-CERT_ERROR = 106--><!--Device-BlankScreenReason-CERT_ERROR = 106-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## CONNECTION_REFUSED

```TypeScript
CONNECTION_REFUSED = 103
```

连接被拒绝。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlankScreenReason-CONNECTION_REFUSED = 103--><!--Device-BlankScreenReason-CONNECTION_REFUSED = 103-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## CONNECTION_RESET

```TypeScript
CONNECTION_RESET = 104
```

连接被重置。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlankScreenReason-CONNECTION_RESET = 104--><!--Device-BlankScreenReason-CONNECTION_RESET = 104-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## CORS_BLOCKED

```TypeScript
CORS_BLOCKED = 213
```

请求被CORS拦截。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlankScreenReason-CORS_BLOCKED = 213--><!--Device-BlankScreenReason-CORS_BLOCKED = 213-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## CSP_BLOCKED

```TypeScript
CSP_BLOCKED = 214
```

请求被CSP拦截。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlankScreenReason-CSP_BLOCKED = 214--><!--Device-BlankScreenReason-CSP_BLOCKED = 214-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## CSS_LOAD_FAILED

```TypeScript
CSS_LOAD_FAILED = 211
```

CSS加载失败。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlankScreenReason-CSS_LOAD_FAILED = 211--><!--Device-BlankScreenReason-CSS_LOAD_FAILED = 211-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## DNS_RESOLVE_FAILED

```TypeScript
DNS_RESOLVE_FAILED = 101
```

DNS解析失败。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlankScreenReason-DNS_RESOLVE_FAILED = 101--><!--Device-BlankScreenReason-DNS_RESOLVE_FAILED = 101-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## GPU_PROCESS_CRASHED

```TypeScript
GPU_PROCESS_CRASHED = 403
```

GPU进程崩溃。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlankScreenReason-GPU_PROCESS_CRASHED = 403--><!--Device-BlankScreenReason-GPU_PROCESS_CRASHED = 403-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## GPU_PROCESS_WATCHDOG_TIMEOUT

```TypeScript
GPU_PROCESS_WATCHDOG_TIMEOUT = 404
```

GPU进程看门狗超时。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlankScreenReason-GPU_PROCESS_WATCHDOG_TIMEOUT = 404--><!--Device-BlankScreenReason-GPU_PROCESS_WATCHDOG_TIMEOUT = 404-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## HTTP_4XX_ERROR

```TypeScript
HTTP_4XX_ERROR = 202
```

发生HTTP 4xx错误。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlankScreenReason-HTTP_4XX_ERROR = 202--><!--Device-BlankScreenReason-HTTP_4XX_ERROR = 202-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## HTTP_5XX_ERROR

```TypeScript
HTTP_5XX_ERROR = 203
```

发生HTTP 5xx错误。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlankScreenReason-HTTP_5XX_ERROR = 203--><!--Device-BlankScreenReason-HTTP_5XX_ERROR = 203-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## INTERNET_DISCONNECTED

```TypeScript
INTERNET_DISCONNECTED = 107
```

网络已断开。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlankScreenReason-INTERNET_DISCONNECTED = 107--><!--Device-BlankScreenReason-INTERNET_DISCONNECTED = 107-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## JS_GLOBAL_BUNDLE_LOAD_FAILED

```TypeScript
JS_GLOBAL_BUNDLE_LOAD_FAILED = 210
```

JavaScript全局bundle加载失败。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlankScreenReason-JS_GLOBAL_BUNDLE_LOAD_FAILED = 210--><!--Device-BlankScreenReason-JS_GLOBAL_BUNDLE_LOAD_FAILED = 210-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## JS_RUNTIME_ERROR

```TypeScript
JS_RUNTIME_ERROR = 301
```

发生JavaScript运行时错误。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlankScreenReason-JS_RUNTIME_ERROR = 301--><!--Device-BlankScreenReason-JS_RUNTIME_ERROR = 301-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## MAIN_DOC_EMPTY

```TypeScript
MAIN_DOC_EMPTY = 201
```

主文档为空。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlankScreenReason-MAIN_DOC_EMPTY = 201--><!--Device-BlankScreenReason-MAIN_DOC_EMPTY = 201-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## MIXED_CONTENT_BLOCKED

```TypeScript
MIXED_CONTENT_BLOCKED = 215
```

混合内容被拦截。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlankScreenReason-MIXED_CONTENT_BLOCKED = 215--><!--Device-BlankScreenReason-MIXED_CONTENT_BLOCKED = 215-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## MULTI_RESOURCE_LOAD_FAILED

```TypeScript
MULTI_RESOURCE_LOAD_FAILED = 212
```

多个资源加载失败。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlankScreenReason-MULTI_RESOURCE_LOAD_FAILED = 212--><!--Device-BlankScreenReason-MULTI_RESOURCE_LOAD_FAILED = 212-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## NO_FIRST_CONTENTFUL_PAINT

```TypeScript
NO_FIRST_CONTENTFUL_PAINT = 312
```

未发生首次内容绘制。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlankScreenReason-NO_FIRST_CONTENTFUL_PAINT = 312--><!--Device-BlankScreenReason-NO_FIRST_CONTENTFUL_PAINT = 312-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## OTHER_NETWORK_ERROR

```TypeScript
OTHER_NETWORK_ERROR = 199
```

其他网络错误。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlankScreenReason-OTHER_NETWORK_ERROR = 199--><!--Device-BlankScreenReason-OTHER_NETWORK_ERROR = 199-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## PROXY_ERROR

```TypeScript
PROXY_ERROR = 109
```

发生代理错误。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlankScreenReason-PROXY_ERROR = 109--><!--Device-BlankScreenReason-PROXY_ERROR = 109-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## REDIRECT_LOOP

```TypeScript
REDIRECT_LOOP = 108
```

发生重定向循环。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlankScreenReason-REDIRECT_LOOP = 108--><!--Device-BlankScreenReason-REDIRECT_LOOP = 108-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## RENDERER_CRASHED

```TypeScript
RENDERER_CRASHED = 401
```

渲染进程崩溃。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlankScreenReason-RENDERER_CRASHED = 401--><!--Device-BlankScreenReason-RENDERER_CRASHED = 401-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## RENDERER_KILLED

```TypeScript
RENDERER_KILLED = 402
```

渲染进程被终止。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlankScreenReason-RENDERER_KILLED = 402--><!--Device-BlankScreenReason-RENDERER_KILLED = 402-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## REQUEST_TIMED_OUT

```TypeScript
REQUEST_TIMED_OUT = 102
```

主文档加载超时。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlankScreenReason-REQUEST_TIMED_OUT = 102--><!--Device-BlankScreenReason-REQUEST_TIMED_OUT = 102-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## SSL_ERROR

```TypeScript
SSL_ERROR = 105
```

发生SSL错误。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlankScreenReason-SSL_ERROR = 105--><!--Device-BlankScreenReason-SSL_ERROR = 105-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## WEB_VIEW_ZERO_SIZE

```TypeScript
WEB_VIEW_ZERO_SIZE = 501
```

Web组件尺寸为0。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlankScreenReason-WEB_VIEW_ZERO_SIZE = 501--><!--Device-BlankScreenReason-WEB_VIEW_ZERO_SIZE = 501-End-->

**系统能力：** SystemCapability.Web.Webview.Core
