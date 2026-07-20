# DetectedBlankScreenReason

白屏的具体原因。

**起始版本：** 22

<!--Device-unnamed-declare enum DetectedBlankScreenReason--><!--Device-unnamed-declare enum DetectedBlankScreenReason-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## NO_CONTENTFUL_NODES

```TypeScript
NO_CONTENTFUL_NODES = 0
```

没有命中任何有内容的节点。

当检测策略为DETECTION_CONTENTFUL_NODES_SEVENTEEN时可能触发。

**起始版本：** 22

<!--Device-DetectedBlankScreenReason-NO_CONTENTFUL_NODES = 0--><!--Device-DetectedBlankScreenReason-NO_CONTENTFUL_NODES = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## SUB_THRESHOLD_CONTENTFUL_NODES

```TypeScript
SUB_THRESHOLD_CONTENTFUL_NODES = 1
```

命中有内容节点的数量小于等于阈值。

当检测策略为DETECTION_CONTENTFUL_NODES_SEVENTEEN，且开发者设置了节点数量阈值contentfulNodesCountThreshold时可能触发。

**起始版本：** 22

<!--Device-DetectedBlankScreenReason-SUB_THRESHOLD_CONTENTFUL_NODES = 1--><!--Device-DetectedBlankScreenReason-SUB_THRESHOLD_CONTENTFUL_NODES = 1-End-->

**系统能力：** SystemCapability.Web.Webview.Core

