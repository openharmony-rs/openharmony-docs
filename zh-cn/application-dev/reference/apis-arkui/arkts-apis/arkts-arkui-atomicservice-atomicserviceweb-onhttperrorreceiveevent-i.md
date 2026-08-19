# OnHttpErrorReceiveEvent

定义网页加载资源遇到HTTP错误时触发该回调。

**起始版本：** 12

<!--Device-unnamed-export declare interface OnHttpErrorReceiveEvent--><!--Device-unnamed-export declare interface OnHttpErrorReceiveEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AtomicServiceWeb, OnMessageEvent, OnErrorReceiveEvent, OnHttpErrorReceiveEvent, OnPageBeginEvent, OnPageEndEvent, AtomicServiceWebController, OnLoadInterceptEvent, OnProgressChangeEvent, OnLoadInterceptCallback, WebHeader } from '@kit.ArkUI';
```

## request

```TypeScript
request: WebResourceRequest
```

网页请求的封装信息。

**类型：** WebResourceRequest

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnHttpErrorReceiveEvent-request: WebResourceRequest--><!--Device-OnHttpErrorReceiveEvent-request: WebResourceRequest-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## response

```TypeScript
response: WebResourceResponse
```

资源响应的封装信息。

**类型：** WebResourceResponse

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnHttpErrorReceiveEvent-response: WebResourceResponse--><!--Device-OnHttpErrorReceiveEvent-response: WebResourceResponse-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

