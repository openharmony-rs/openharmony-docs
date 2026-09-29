# OnSearchResultReceiveEvent

```TypeScript
declare interface OnSearchResultReceiveEvent
```

Defines the callback information for the search result on the web page, including the match ordinal and total count. It is suitable for scenarios where monitoring in-page search behavior is required, improving search interaction visibility and user experience.

**Since:** 12

<!--Device-unnamed-declare interface OnSearchResultReceiveEvent--><!--Device-unnamed-declare interface OnSearchResultReceiveEvent-End-->

**System capability:** SystemCapability.Web.Webview.Core

## activeMatchOrdinal

```TypeScript
activeMatchOrdinal: number
```

Sequence number of the current match, which starts from 0.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-OnSearchResultReceiveEvent-activeMatchOrdinal: number--><!--Device-OnSearchResultReceiveEvent-activeMatchOrdinal: number-End-->

**System capability:** SystemCapability.Web.Webview.Core

## isDoneCounting

```TypeScript
isDoneCounting: boolean
```

Whether the current in-page search operation is complete.

The value **true** indicates that the current in-page search operation is complete, and **false** indicates the opposite.

This method may be called back multiple times until isDoneCounting is **true**.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-OnSearchResultReceiveEvent-isDoneCounting: boolean--><!--Device-OnSearchResultReceiveEvent-isDoneCounting: boolean-End-->

**System capability:** SystemCapability.Web.Webview.Core

## numberOfMatches

```TypeScript
numberOfMatches: number
```

Total number of matches.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-OnSearchResultReceiveEvent-numberOfMatches: number--><!--Device-OnSearchResultReceiveEvent-numberOfMatches: number-End-->

**System capability:** SystemCapability.Web.Webview.Core
