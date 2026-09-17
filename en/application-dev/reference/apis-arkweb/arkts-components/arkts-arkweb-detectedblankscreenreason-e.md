# DetectedBlankScreenReason

Defines the specific reasons for the blank screen, which identify the underlying causes of page blank screen phenomena and help developers quickly locate the source of issues, improving the efficiency of troubleshooting page loading problems and user experience.

**Since:** 22

**System capability:** SystemCapability.Web.Webview.Core

## NO_CONTENTFUL_NODES

```TypeScript
NO_CONTENTFUL_NODES = 0
```

No contentful node is detected.

This may be triggered when the detection policy is **DETECTION_CONTENTFUL_NODES_SEVENTEEN**.

**Since:** 22

**System capability:** SystemCapability.Web.Webview.Core

## SUB_THRESHOLD_CONTENTFUL_NODES

```TypeScript
SUB_THRESHOLD_CONTENTFUL_NODES = 1
```

The number of contentful nodes detected is less than or equal to the threshold.

This may be triggered when the detection policy is **DETECTION_CONTENTFUL_NODES_SEVENTEEN** and **contentfulNodesCountThreshold** is set.

**Since:** 22

**System capability:** SystemCapability.Web.Webview.Core
