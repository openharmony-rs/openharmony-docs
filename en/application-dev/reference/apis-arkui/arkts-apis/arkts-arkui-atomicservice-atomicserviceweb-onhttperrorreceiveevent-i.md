# OnHttpErrorReceiveEvent

Represents the callback invoked when an HTTP error occurs during web page resource loading.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceWeb, OnMessageEvent, OnErrorReceiveEvent, OnHttpErrorReceiveEvent, OnPageBeginEvent, OnPageEndEvent, AtomicServiceWebController, OnLoadInterceptEvent, OnProgressChangeEvent, OnLoadInterceptCallback, WebHeader } from '@kit.ArkUI';
```

## request

```TypeScript
request: WebResourceRequest
```

Web resource request of event.

**Type:** [WebResourceRequest](../../apis-arkweb/arkts-components/arkts-arkweb-webresourcerequest-c.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## response

```TypeScript
response: WebResourceResponse
```

Web resource response of event.

**Type:** [WebResourceResponse](../../apis-arkweb/arkts-components/arkts-arkweb-webresourceresponse-c.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
