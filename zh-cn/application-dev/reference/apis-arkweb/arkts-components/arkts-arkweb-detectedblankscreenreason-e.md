# DetectedBlankScreenReason

白屏的具体原因，用于标识页面白屏现象的底层原因，帮助开发者快速定位问题来源，提升页面加载问题的排查效率和用户体验。

**起始版本：** 22

**系统能力：** SystemCapability.Web.Webview.Core

## NO_CONTENTFUL_NODES

```TypeScript
NO_CONTENTFUL_NODES = 0
```

没有命中任何有内容的节点。

当检测策略为DETECTION_CONTENTFUL_NODES_SEVENTEEN时可能触发。

**起始版本：** 22

**系统能力：** SystemCapability.Web.Webview.Core

## SUB_THRESHOLD_CONTENTFUL_NODES

```TypeScript
SUB_THRESHOLD_CONTENTFUL_NODES = 1
```

命中有内容节点的数量小于等于阈值。

当检测策略为DETECTION_CONTENTFUL_NODES_SEVENTEEN，且开发者设置了节点数量阈值contentfulNodesCountThreshold时可能触发。

**起始版本：** 22

**系统能力：** SystemCapability.Web.Webview.Core
