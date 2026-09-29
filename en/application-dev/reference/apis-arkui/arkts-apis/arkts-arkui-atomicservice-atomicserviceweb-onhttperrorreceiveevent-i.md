# OnHttpErrorReceiveEvent

```TypeScript
export declare interface OnHttpErrorReceiveEvent
```

Represents the callback invoked when an HTTP error occurs during web page resource loading.

**Since:** 12

<!--Device-unnamed-export declare interface OnHttpErrorReceiveEvent--><!--Device-unnamed-export declare interface OnHttpErrorReceiveEvent-End-->

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

**Type:** [WebResourceRequest](../../apis-arkweb/arkts-components/arkts-arkweb-web-comp-webresourcerequest-c.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-OnHttpErrorReceiveEvent-request: WebResourceRequest--><!--Device-OnHttpErrorReceiveEvent-request: WebResourceRequest-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## response

```TypeScript
response: WebResourceResponse
```

Web resource response of event.

**Type:** [WebResourceResponse](../../apis-arkweb/arkts-components/arkts-arkweb-web-comp-webresourceresponse-c.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-OnHttpErrorReceiveEvent-response: WebResourceResponse--><!--Device-OnHttpErrorReceiveEvent-response: WebResourceResponse-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
