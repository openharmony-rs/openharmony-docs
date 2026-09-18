# OnFirstContentfulPaintEvent

Defines the callback information for the first content paint on the web page, including the load time and paint time. It is suitable for scenarios where monitoring page rendering performance is required, improving performance optimization accuracy and user experience.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## firstContentfulPaintMs

```TypeScript
firstContentfulPaintMs: number
```

Time between navigation and when the content is first rendered, in milliseconds.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## navigationStartTick

```TypeScript
navigationStartTick: number
```

Navigation start time, in microseconds.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core
