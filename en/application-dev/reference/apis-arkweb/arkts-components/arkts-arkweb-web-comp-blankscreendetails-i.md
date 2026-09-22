# BlankScreenDetails

```TypeScript
declare interface BlankScreenDetails
```

Provides the result details when a blank screen is detected, including the number of nodes with content. It is suitable for scenarios where analyzing blank screen causes is required, improving blank screen diagnosis detail and accuracy.

**Since:** 22

**System capability:** SystemCapability.Web.Webview.Core

## detectedContentfulNodesCount

```TypeScript
detectedContentfulNodesCount?: number
```

This attribute may exist when the contentful node detection policy is used and the threshold for the number of detected nodes is set. Otherwise, this attribute does not exist.

Number of contentful nodes that are detected.

**Type:** number

**Since:** 22

**System capability:** SystemCapability.Web.Webview.Core
