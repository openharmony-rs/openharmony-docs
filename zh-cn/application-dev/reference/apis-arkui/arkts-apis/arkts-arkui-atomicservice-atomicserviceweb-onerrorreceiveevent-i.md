# OnErrorReceiveEvent

定义网页加载遇到错误时触发该回调。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AtomicServiceWeb, OnMessageEvent, OnErrorReceiveEvent, OnHttpErrorReceiveEvent, OnPageBeginEvent, OnPageEndEvent, AtomicServiceWebController, OnLoadInterceptEvent, OnProgressChangeEvent, OnLoadInterceptCallback, WebHeader } from '@kit.ArkUI';
```

## error

```TypeScript
error: WebResourceError
```

网页加载资源错误的封装信息 。

**类型：** [WebResourceError](../../apis-arkweb/arkts-components/arkts-arkweb-webresourceerror-c.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## request

```TypeScript
request: WebResourceRequest
```

网页请求的封装信息。

**类型：** [WebResourceRequest](../../apis-arkweb/arkts-components/arkts-arkweb-webresourcerequest-c.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
