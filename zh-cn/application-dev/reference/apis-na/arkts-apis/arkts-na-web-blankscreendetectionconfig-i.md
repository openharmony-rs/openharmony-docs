# BlankScreenDetectionConfig

The strategy of blank screen detection.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface BlankScreenDetectionConfig--><!--Device-unnamed-export declare interface BlankScreenDetectionConfig-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## contentfulNodesCountThreshold

```TypeScript
contentfulNodesCountThreshold?: int
```

When using the specific detection method of detecting contentful nodes, the threshold is used to determine how close the detection is to being blank screen page.

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-BlankScreenDetectionConfig-contentfulNodesCountThreshold?: int--><!--Device-BlankScreenDetectionConfig-contentfulNodesCountThreshold?: int-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## detectionMethods

```TypeScript
detectionMethods?: BlankScreenDetectionMethod[]
```

The combination of blank screen detection methods.

**类型：** [BlankScreenDetectionMethod](arkts-na-web-blankscreendetectionmethod-e.md)[]

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-BlankScreenDetectionConfig-detectionMethods?: BlankScreenDetectionMethod[]--><!--Device-BlankScreenDetectionConfig-detectionMethods?: BlankScreenDetectionMethod[]-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## detectionTiming

```TypeScript
detectionTiming?: double[]
```

The settings of the timing when web try to detect current page is blank or not. The timing is the duration after web navigation. <br>Length range:[0,+∞).Unit: second.Default value:[1.0,3.0,5.0].

**类型：** double[]

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-BlankScreenDetectionConfig-detectionTiming?: double[]--><!--Device-BlankScreenDetectionConfig-detectionTiming?: double[]-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## enable

```TypeScript
enable: boolean
```

Enable blank screen detection or not.

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-BlankScreenDetectionConfig-enable: boolean--><!--Device-BlankScreenDetectionConfig-enable: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

