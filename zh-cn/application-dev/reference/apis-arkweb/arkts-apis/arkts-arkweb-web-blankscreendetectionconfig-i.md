# BlankScreenDetectionConfig

定义白屏检测的策略配置选项。

**起始版本：** 22

**系统能力：** SystemCapability.Web.Webview.Core

## contentfulNodesCountThreshold

```TypeScript
contentfulNodesCountThreshold?: number
```

在使用到检测有内容的节点检测策略时，才会生效。

可以设置0-${检测策略最大节点}，如果小于等于阈值则会触发近似白屏。

默认值：0。

**类型：** number

**起始版本：** 22

**系统能力：** SystemCapability.Web.Webview.Core

## detectionMethods

```TypeScript
detectionMethods?: BlankScreenDetectionMethod[]
```

使用检测策略的方法，是一个数组。

注：

1.重复值会忽略。

默认值：[BlankScreenDetectionMethod.DETECTION_CONTENTFUL_NODES_SEVENTEEN]。

**类型：** BlankScreenDetectionMethod[]

**起始版本：** 22

**系统能力：** SystemCapability.Web.Webview.Core

## detectionTiming

```TypeScript
detectionTiming?: number[]
```

用以设置需要在加载后多少秒的时机来检测是否白屏。

单位：秒。

注：

1.重复值会忽略。

2.需大于0，小于0的值会被忽略。

默认值：[1.0,3.0,5.0]。

**类型：** number[]

**起始版本：** 22

**系统能力：** SystemCapability.Web.Webview.Core

## enable

```TypeScript
enable: boolean
```

是否使能白屏策略功能。

**类型：** boolean

**起始版本：** 22

**系统能力：** SystemCapability.Web.Webview.Core

