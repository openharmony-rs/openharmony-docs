# MediaInfo

```TypeScript
interface MediaInfo
```

Represents a **MediaInfo** object used as a parameter of the [CreateNativeMediaPlayerCallback](arkts-arkweb-webview-createnativemediaplayercallback-t.md) callback. The object contains information about media on the web page. The application may create, based on the information, a player that takes over media playback of the web page.

**Since:** 12

<!--Device-webview-interface MediaInfo--><!--Device-webview-interface MediaInfo-End-->

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## attributes

```TypeScript
attributes: Record<string, string>
```

Attributes in **&lt;video&gt;** or **&lt;audio&gt;**.

**Type:** Record&lt;string, string&gt;

**Since:** 12

<!--Device-MediaInfo-attributes: Record<string, string>--><!--Device-MediaInfo-attributes: Record<string, string>-End-->

**System capability:** SystemCapability.Web.Webview.Core

## controlList

```TypeScript
controlList: string[]
```

Value of the **controlslist** attribute in **&lt;video&gt;** or **&lt;audio&gt;**.

**Type:** string[]

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MediaInfo-controlList: string[]--><!--Device-MediaInfo-controlList: string[]-End-->

**System capability:** SystemCapability.Web.Webview.Core

## controlsShown

```TypeScript
controlsShown: boolean
```

Whether the `&lt;video&gt;` or `&lt;audio&gt;` element has the `controls` attribute.

The value **true** indicates that it has, and **false** indicates that it does not.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MediaInfo-controlsShown: boolean--><!--Device-MediaInfo-controlsShown: boolean-End-->

**System capability:** SystemCapability.Web.Webview.Core

## embedID

```TypeScript
embedID: string
```

ID of the `&lt;video&gt;` or `&lt;audio&gt;` element in the web page.

**Type:** string

**Since:** 12

<!--Device-MediaInfo-embedID: string--><!--Device-MediaInfo-embedID: string-End-->

**System capability:** SystemCapability.Web.Webview.Core

## headers

```TypeScript
headers: Record<string, string>
```

HTTP headers that need to be included in the player's request for media resources.

**Type:** Record&lt;string, string&gt;

**Since:** 12

<!--Device-MediaInfo-headers: Record<string, string>--><!--Device-MediaInfo-headers: Record<string, string>-End-->

**System capability:** SystemCapability.Web.Webview.Core

## mediaSrcList

```TypeScript
mediaSrcList: MediaSourceInfo[]
```

Source of the media. There may be multiple sources. The application needs to select a supported source to play.

**Type:** [MediaSourceInfo](arkts-arkweb-webview-mediasourceinfo-c.md)[]

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MediaInfo-mediaSrcList: MediaSourceInfo[]--><!--Device-MediaInfo-mediaSrcList: MediaSourceInfo[]-End-->

**System capability:** SystemCapability.Web.Webview.Core

## mediaType

```TypeScript
mediaType: MediaType
```

Type of the media.

**Type:** [MediaType](arkts-arkweb-webview-mediatype-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MediaInfo-mediaType: MediaType--><!--Device-MediaInfo-mediaType: MediaType-End-->

**System capability:** SystemCapability.Web.Webview.Core

## muted

```TypeScript
muted: boolean
```

Whether muted playback is required.

The value **true** indicates muted playback, and **false** indicates non-muted playback.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MediaInfo-muted: boolean--><!--Device-MediaInfo-muted: boolean-End-->

**System capability:** SystemCapability.Web.Webview.Core

## posterUrl

```TypeScript
posterUrl: string
```

URL of a poster.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MediaInfo-posterUrl: string--><!--Device-MediaInfo-posterUrl: string-End-->

**System capability:** SystemCapability.Web.Webview.Core

## preload

```TypeScript
preload: Preload
```

Whether preloading is required.

**Type:** [Preload](arkts-arkweb-webview-preload-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MediaInfo-preload: Preload--><!--Device-MediaInfo-preload: Preload-End-->

**System capability:** SystemCapability.Web.Webview.Core

## surfaceInfo

```TypeScript
surfaceInfo: NativeMediaPlayerSurfaceInfo
```

Surface information used for same-layer rendering.

**Type:** [NativeMediaPlayerSurfaceInfo](arkts-arkweb-webview-nativemediaplayersurfaceinfo-c.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-MediaInfo-surfaceInfo: NativeMediaPlayerSurfaceInfo--><!--Device-MediaInfo-surfaceInfo: NativeMediaPlayerSurfaceInfo-End-->

**System capability:** SystemCapability.Web.Webview.Core
