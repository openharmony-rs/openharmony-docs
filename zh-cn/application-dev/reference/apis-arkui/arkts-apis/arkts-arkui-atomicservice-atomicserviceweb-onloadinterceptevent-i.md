# OnLoadInterceptEvent

定义Web组件加载url之前触发的加载拦截事件。

**起始版本：** 12

<!--Device-unnamed-export declare interface OnLoadInterceptEvent--><!--Device-unnamed-export declare interface OnLoadInterceptEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AtomicServiceWeb, OnMessageEvent, OnErrorReceiveEvent, OnHttpErrorReceiveEvent, OnPageBeginEvent, OnPageEndEvent, AtomicServiceWebController, OnLoadInterceptEvent, OnProgressChangeEvent, OnLoadInterceptCallback, WebHeader } from '@kit.ArkUI';
```

## data

```TypeScript
data: WebResourceRequest
```

网页请求的封装信息。

**类型：** WebResourceRequest

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-OnLoadInterceptEvent-data: WebResourceRequest--><!--Device-OnLoadInterceptEvent-data: WebResourceRequest-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

