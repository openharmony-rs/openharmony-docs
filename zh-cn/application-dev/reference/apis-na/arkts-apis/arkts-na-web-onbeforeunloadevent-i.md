# OnBeforeUnloadEvent

Defines the triggered function when the web page wants to confirm navigation from JavaScript onbeforeunload.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface OnBeforeUnloadEvent--><!--Device-unnamed-export declare interface OnBeforeUnloadEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## isReload

```TypeScript
isReload?: boolean
```

The isReload parameter is set to true when the page is refreshed; otherwise, it remains false. Default is false.

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-OnBeforeUnloadEvent-isReload?: boolean--><!--Device-OnBeforeUnloadEvent-isReload?: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## message

```TypeScript
message: string
```

The message of confirm dialog.

**类型：** string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-OnBeforeUnloadEvent-message: string--><!--Device-OnBeforeUnloadEvent-message: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## result

```TypeScript
result: JsResult
```

Handle the user's JavaScript result.

**类型：** [JsResult](arkts-na-web-jsresult-c.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-OnBeforeUnloadEvent-result: JsResult--><!--Device-OnBeforeUnloadEvent-result: JsResult-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

The url of the page.

**类型：** string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-OnBeforeUnloadEvent-url: string--><!--Device-OnBeforeUnloadEvent-url: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

