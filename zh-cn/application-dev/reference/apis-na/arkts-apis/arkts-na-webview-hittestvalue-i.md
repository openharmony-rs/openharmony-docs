# HitTestValue

Provides element information of the click area. related to [getLastHitTest](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-webviewcontroller-c.md#getlasthittest) method.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-webview-interface HitTestValue--><!--Device-webview-interface HitTestValue-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## extra

```TypeScript
extra: string
```

Get the hit test extra data. If the clicked area is an image or a link, the additional parameter information is it's URL address.

**类型：** string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-HitTestValue-extra: string--><!--Device-HitTestValue-extra: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## type

```TypeScript
type: WebHitTestType
```

Get the hit test type.

**类型：** [WebHitTestType](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-webhittesttype-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-HitTestValue-type: WebHitTestType--><!--Device-HitTestValue-type: WebHitTestType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

