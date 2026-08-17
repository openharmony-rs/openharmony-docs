# BlankScreenDetails

提供检测到白屏时的结果细节，包括有内容节点数量。适用于需要分析白屏原因的场景，提升白屏诊断的详细性和准确性。

**起始版本：** 22

**ArkTS模式：** 起始版本为22。

**废弃版本：** -1

<!--Device-unnamed-declare interface BlankScreenDetails--><!--Device-unnamed-declare interface BlankScreenDetails-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## detectedContentfulNodesCount

```TypeScript
detectedContentfulNodesCount?: number
```

在使用到检测有内容的节点检测策略时，且开发者自己设置了检测到节点数量阈值时，可能包含该属性。否则没有该属性。 表示当前命中了多少有内容的节点。

**类型：** number

**起始版本：** 22

**ArkTS模式：** 起始版本为22。

**废弃版本：** -1

<!--Device-BlankScreenDetails-detectedContentfulNodesCount?: number--><!--Device-BlankScreenDetails-detectedContentfulNodesCount?: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

