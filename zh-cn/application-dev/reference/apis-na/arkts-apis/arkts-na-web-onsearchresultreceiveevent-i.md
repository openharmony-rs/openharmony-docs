# OnSearchResultReceiveEvent

Defines function Triggered when the host application call searchAllAsync.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface OnSearchResultReceiveEvent--><!--Device-unnamed-export declare interface OnSearchResultReceiveEvent-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## activeMatchOrdinal

```TypeScript
activeMatchOrdinal: int
```

The ordinal number of the currently matched lookup item (starting from 0).

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-OnSearchResultReceiveEvent-activeMatchOrdinal: int--><!--Device-OnSearchResultReceiveEvent-activeMatchOrdinal: int-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## isDoneCounting

```TypeScript
isDoneCounting: boolean
```

Indicates whether the current in-page search operation is complete. The method may be called back multiple times until isDoneCounting is true.

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-OnSearchResultReceiveEvent-isDoneCounting: boolean--><!--Device-OnSearchResultReceiveEvent-isDoneCounting: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## numberOfMatches

```TypeScript
numberOfMatches: int
```

The number of all matched keywords.

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-OnSearchResultReceiveEvent-numberOfMatches: int--><!--Device-OnSearchResultReceiveEvent-numberOfMatches: int-End-->

**系统能力：** SystemCapability.Web.Webview.Core

