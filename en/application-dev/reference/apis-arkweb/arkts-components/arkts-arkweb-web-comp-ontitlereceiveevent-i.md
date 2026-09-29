# OnTitleReceiveEvent

```TypeScript
declare interface OnTitleReceiveEvent
```

Defines the callback information triggered when the document title of the web page is changed, including the title content and source. It is suitable for scenarios where monitoring page title changes is required, improving page information real-time performance and user experience.

**Since:** 12

<!--Device-unnamed-declare interface OnTitleReceiveEvent--><!--Device-unnamed-declare interface OnTitleReceiveEvent-End-->

**System capability:** SystemCapability.Web.Webview.Core

## isRealTitle

```TypeScript
isRealTitle?: boolean
```

Whether the document title is a real title. The value true indicates that the title is from the **title** tag of the web page, and **false** indicates that the title is automatically generated based on the URL.

Default value: **false**.

**Type:** boolean

**Since:** 20

<!--Device-OnTitleReceiveEvent-isRealTitle?: boolean--><!--Device-OnTitleReceiveEvent-isRealTitle?: boolean-End-->

**System capability:** SystemCapability.Web.Webview.Core

## title

```TypeScript
title: string
```

Document title.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-OnTitleReceiveEvent-title: string--><!--Device-OnTitleReceiveEvent-title: string-End-->

**System capability:** SystemCapability.Web.Webview.Core
