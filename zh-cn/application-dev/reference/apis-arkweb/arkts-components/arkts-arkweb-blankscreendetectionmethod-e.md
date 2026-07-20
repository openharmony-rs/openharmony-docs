# BlankScreenDetectionMethod

白屏检测使用的检测策略的方法。

**起始版本：** 22

<!--Device-unnamed-declare enum BlankScreenDetectionMethod--><!--Device-unnamed-declare enum BlankScreenDetectionMethod-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## DETECTION_CONTENTFUL_NODES_SEVENTEEN

```TypeScript
DETECTION_CONTENTFUL_NODES_SEVENTEEN = 0
```

以17点检测法进行页面检测。当检测点命中已经渲染了且有意义的节点，则认为有命中。有意义的节点指的是图片，视频和文字节点。

当无命中，或少于用户设置阈值命中时，则认为是白屏或者近似白屏。

其中，检测的17个点位包括：

中心点 (1个)： 位于页面的几何中心。

内部网格交点 (16个)：在页面区域内定义一个5×5 的均匀网格，这16个点即为页面内4条垂直等分线和4条水平等分线的交点。

**起始版本：** 22

<!--Device-BlankScreenDetectionMethod-DETECTION_CONTENTFUL_NODES_SEVENTEEN = 0--><!--Device-BlankScreenDetectionMethod-DETECTION_CONTENTFUL_NODES_SEVENTEEN = 0-End-->

**系统能力：** SystemCapability.Web.Webview.Core

