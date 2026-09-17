# RenderMode

Enumerates the rendering modes of the **Web** component. By default, the asynchronous rendering mode is used.

The asynchronous rendering mode is recommended because it has better performance and lower power consumption.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## ASYNC_RENDER

```TypeScript
ASYNC_RENDER = 0
```

Asynchronous rendering mode of the Web component. The ArkWeb component acts as a graphics surface node and independently outputs display. The maximum height of the Web component does not exceed 7,680 px (physical pixels).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## SYNC_RENDER

```TypeScript
SYNC_RENDER = 1
```

Synchronous rendering mode of the Web component. The ArkWeb component acts as a graphics canvas node and outputs display together with system components, allowing longer Web component content to be rendered. The maximum height of the Web component does not exceed 500,000 px (physical pixels).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core
