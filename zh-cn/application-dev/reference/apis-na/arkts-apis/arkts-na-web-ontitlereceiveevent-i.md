# OnTitleReceiveEvent

Defines the triggered function when the title of the main application document changes.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface OnTitleReceiveEvent--><!--Device-unnamed-export declare interface OnTitleReceiveEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## isRealTitle

```TypeScript
isRealTitle?: boolean
```

Mark the source of the title. If it is true, the title is derived from the H5 title element; If it is false, it is calculated from the URL. By default, it is calculated from the URL.

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-OnTitleReceiveEvent-isRealTitle?: boolean--><!--Device-OnTitleReceiveEvent-isRealTitle?: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## title

```TypeScript
title: string
```

The title of the page.

**类型：** string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-OnTitleReceiveEvent-title: string--><!--Device-OnTitleReceiveEvent-title: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

