# BlankScreenDetectionConfig

Provides the policy configuration options for blank screen detection, including the detection timing, method, and threshold. It is suitable for scenarios where custom blank screen detection behavior is required, improving blank screen monitoring flexibility and accuracy.

**Since:** 22

**System capability:** SystemCapability.Web.Webview.Core

## contentfulNodesCountThreshold

```TypeScript
contentfulNodesCountThreshold?: number
```

This parameter takes effect only when the contentful node detection strategy is used.

The value ranges from 0 to &#36;{maximum nodes of the detection strategy}. If the value is less than or equal to the threshold, a near-white screen is triggered.

Default value: 0.

Note: The maximum nodes of the detection strategy depend on the selected detection strategy.

**Type:** number

**Since:** 22

**System capability:** SystemCapability.Web.Webview.Core

## detectionMethods

```TypeScript
detectionMethods?: BlankScreenDetectionMethod[]
```

Methods of the detection policy. The value is an array.

**NOTE:** 

1. Duplicate values are ignored.

Default value: **[BlankScreenDetectionMethod.DETECTION_CONTENTFUL_NODES_SEVENTEEN]**.

**Type:** [BlankScreenDetectionMethod](arkts-arkweb-blankscreendetectionmethod-e.md)[]

**Since:** 22

**System capability:** SystemCapability.Web.Webview.Core

## detectionTiming

```TypeScript
detectionTiming?: number[]
```

Sets the timing (in seconds after loading) at which to detect whether a white screen occurs.

Unit: second.

Note:

1. Duplicate values are ignored.
2. The value must be greater than 0. Values less than 0 are ignored.

Default value: [1.0, 3.0, 5.0].

**Type:** number[]

**Since:** 22

**System capability:** SystemCapability.Web.Webview.Core

## enable

```TypeScript
enable: boolean
```

Whether to enable the white screen policy feature. The value **true** indicates enabled, and **false** indicates disabled.

**Type:** boolean

**Since:** 22

**System capability:** SystemCapability.Web.Webview.Core
