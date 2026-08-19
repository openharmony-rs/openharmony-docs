# BlankScreenDetectionEventInfo

Defines the blank screen detection event info.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface BlankScreenDetectionEventInfo--><!--Device-unnamed-export declare interface BlankScreenDetectionEventInfo-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## blankScreenDetails

```TypeScript
blankScreenDetails?: BlankScreenDetails
```

The details of this detection result.

**类型：** [BlankScreenDetails](arkts-na-web-blankscreendetails-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-BlankScreenDetectionEventInfo-blankScreenDetails?: BlankScreenDetails--><!--Device-BlankScreenDetectionEventInfo-blankScreenDetails?: BlankScreenDetails-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## blankScreenReason

```TypeScript
blankScreenReason: DetectedBlankScreenReason
```

The reason why we consider this page is blank.

**类型：** [DetectedBlankScreenReason](arkts-na-web-detectedblankscreenreason-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-BlankScreenDetectionEventInfo-blankScreenReason: DetectedBlankScreenReason--><!--Device-BlankScreenDetectionEventInfo-blankScreenReason: DetectedBlankScreenReason-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

The url of detected blank screen page.

**类型：** string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-BlankScreenDetectionEventInfo-url: string--><!--Device-BlankScreenDetectionEventInfo-url: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

