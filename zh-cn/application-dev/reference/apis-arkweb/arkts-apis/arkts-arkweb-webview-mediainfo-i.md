# MediaInfo

[CreateNativeMediaPlayerCallback](arkts-arkweb-webview-createnativemediaplayercallback-t.md)回调函数的一个参数。包含了网页中媒体的信息。应用可以根据这些信息来创建 接管网页媒体播放的播放器。

**起始版本：** 12

<!--Device-webview-interface MediaInfo--><!--Device-webview-interface MediaInfo-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## attributes

```TypeScript
attributes: Record<string, string>
```

`&lt;video&gt;` 或 `&lt;audio&gt;` 标签中的属性。

**类型：** Record&lt;string, string&gt;

**起始版本：** 12

<!--Device-MediaInfo-attributes: Record<string, string>--><!--Device-MediaInfo-attributes: Record<string, string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## controlList

```TypeScript
controlList: string[]
```

`&lt;video&gt;` 或 `&lt;audio&gt;` 中的 `controlslist` 属性的值。

**类型：** string[]

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaInfo-controlList: string[]--><!--Device-MediaInfo-controlList: string[]-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## controlsShown

```TypeScript
controlsShown: boolean
```

`&lt;video&gt;` 或 `&lt;audio&gt;` 中是否有 `controls` 属性。 true 表示有，false 表示没有。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaInfo-controlsShown: boolean--><!--Device-MediaInfo-controlsShown: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## embedID

```TypeScript
embedID: string
```

网页中的 `&lt;video&gt;` 或 `&lt;audio&gt;` 的 ID。

**类型：** string

**起始版本：** 12

<!--Device-MediaInfo-embedID: string--><!--Device-MediaInfo-embedID: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## headers

```TypeScript
headers: Record<string, string>
```

播放器请求媒体资源时，需要携带的 HTTP 头。

**类型：** Record&lt;string, string&gt;

**起始版本：** 12

<!--Device-MediaInfo-headers: Record<string, string>--><!--Device-MediaInfo-headers: Record<string, string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## mediaSrcList

```TypeScript
mediaSrcList: MediaSourceInfo[]
```

媒体的源。可能有多个源，应用需要选择一个支持的源来播放。

**类型：** [MediaSourceInfo](arkts-arkweb-webview-mediasourceinfo-c.md)[]

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaInfo-mediaSrcList: MediaSourceInfo[]--><!--Device-MediaInfo-mediaSrcList: MediaSourceInfo[]-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## mediaType

```TypeScript
mediaType: MediaType
```

媒体的类型。

**类型：** MediaType

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaInfo-mediaType: MediaType--><!--Device-MediaInfo-mediaType: MediaType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## muted

```TypeScript
muted: boolean
```

是否要求静音播放。 true 表示静音播放，false 表示未静音播放。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaInfo-muted: boolean--><!--Device-MediaInfo-muted: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## posterUrl

```TypeScript
posterUrl: string
```

海报的地址。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaInfo-posterUrl: string--><!--Device-MediaInfo-posterUrl: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## preload

```TypeScript
preload: Preload
```

是否需要预加载。

**类型：** [Preload](arkts-arkweb-webview-preload-e.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaInfo-preload: Preload--><!--Device-MediaInfo-preload: Preload-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## surfaceInfo

```TypeScript
surfaceInfo: NativeMediaPlayerSurfaceInfo
```

用于同层渲染的 surface 信息。

**类型：** [NativeMediaPlayerSurfaceInfo](arkts-arkweb-webview-nativemediaplayersurfaceinfo-c.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MediaInfo-surfaceInfo: NativeMediaPlayerSurfaceInfo--><!--Device-MediaInfo-surfaceInfo: NativeMediaPlayerSurfaceInfo-End-->

**系统能力：** SystemCapability.Web.Webview.Core

