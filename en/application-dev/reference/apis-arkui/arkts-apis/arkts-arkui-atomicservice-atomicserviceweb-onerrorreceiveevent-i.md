# OnErrorReceiveEvent

```TypeScript
export declare interface OnErrorReceiveEvent
```

Represents the callback invoked when an error occurs during web page loading.

**Since:** 12

<!--Device-unnamed-export declare interface OnErrorReceiveEvent--><!--Device-unnamed-export declare interface OnErrorReceiveEvent-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceWeb, OnMessageEvent, OnErrorReceiveEvent, OnHttpErrorReceiveEvent, OnPageBeginEvent, OnPageEndEvent, AtomicServiceWebController, OnLoadInterceptEvent, OnProgressChangeEvent, OnLoadInterceptCallback, WebHeader } from '@kit.ArkUI';
```

## error

```TypeScript
error: WebResourceError
```

Web resource error of event.

**Type:** [WebResourceError](../../apis-arkweb/arkts-components/arkts-arkweb-web-comp-webresourceerror-c.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-OnErrorReceiveEvent-error: WebResourceError--><!--Device-OnErrorReceiveEvent-error: WebResourceError-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## request

```TypeScript
request: WebResourceRequest
```

Web resource request of event.

**Type:** [WebResourceRequest](../../apis-arkweb/arkts-components/arkts-arkweb-web-comp-webresourcerequest-c.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-OnErrorReceiveEvent-request: WebResourceRequest--><!--Device-OnErrorReceiveEvent-request: WebResourceRequest-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
