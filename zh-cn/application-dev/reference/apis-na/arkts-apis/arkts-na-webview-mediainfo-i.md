# MediaInfo

[CreateNativeMediaPlayerCallback](../../../reference/apis-arkweb/arkts-apis-webview-t.md#createnativemediaplayercallback) 回调函数的一个参数。包含了网页中媒体的信息。应用可以根据这些信息来创建接管网页媒体播放的播放器。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-webview-interface MediaInfo--><!--Device-webview-interface MediaInfo-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## attributes

```TypeScript
attributes: Record<string, string>
```

Attributes in **&lt;video&gt;** or **&lt;audio&gt;**.

**类型：** Record&lt;string, string&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-MediaInfo-attributes: Record<string, string>--><!--Device-MediaInfo-attributes: Record<string, string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## controlList

```TypeScript
controlList: string[]
```

Value of the **controlslist** attribute in **&lt;video&gt;** or **&lt;audio&gt;**.

**类型：** string[]

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-MediaInfo-controlList: string[]--><!--Device-MediaInfo-controlList: string[]-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## controlsShown

```TypeScript
controlsShown: boolean
```

Whether the **controls** attribute exists in **&lt;video&gt;** or **&lt;audio&gt;**. The value **true** means that the **controls** attribute exists in **&lt;video&gt;** or **&lt;audio&gt;**, and **false** means the opposite.

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-MediaInfo-controlsShown: boolean--><!--Device-MediaInfo-controlsShown: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## embedID

```TypeScript
embedID: string
```

ID of **&lt;video&gt;** or **&lt;audio&gt;** on the web page.

**类型：** string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-MediaInfo-embedID: string--><!--Device-MediaInfo-embedID: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## headers

```TypeScript
headers: Record<string, string>
```

HTTP headers that need to be included in the player's request for media resources.

**类型：** Record&lt;string, string&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-MediaInfo-headers: Record<string, string>--><!--Device-MediaInfo-headers: Record<string, string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## mediaSrcList

```TypeScript
mediaSrcList: MediaSourceInfo[]
```

Source of the media. There may be multiple sources. The application needs to select a supported source to play.

**类型：** [MediaSourceInfo](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-mediasourceinfo-c.md)[]

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-MediaInfo-mediaSrcList: MediaSourceInfo[]--><!--Device-MediaInfo-mediaSrcList: MediaSourceInfo[]-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## mediaType

```TypeScript
mediaType: MediaType
```

Type of the media.

**类型：** MediaType

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-MediaInfo-mediaType: MediaType--><!--Device-MediaInfo-mediaType: MediaType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## muted

```TypeScript
muted: boolean
```

Whether to mute the player. The value **true** means to mute the player, and **false** means the opposite.

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-MediaInfo-muted: boolean--><!--Device-MediaInfo-muted: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## posterUrl

```TypeScript
posterUrl: string
```

URL of a poster.

**类型：** string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-MediaInfo-posterUrl: string--><!--Device-MediaInfo-posterUrl: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## preload

```TypeScript
preload: Preload
```

Whether preloading is required.

**类型：** [Preload](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-preload-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-MediaInfo-preload: Preload--><!--Device-MediaInfo-preload: Preload-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## surfaceInfo

```TypeScript
surfaceInfo: NativeMediaPlayerSurfaceInfo
```

Surface information used for same-layer rendering.

**类型：** [NativeMediaPlayerSurfaceInfo](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-nativemediaplayersurfaceinfo-c.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-MediaInfo-surfaceInfo: NativeMediaPlayerSurfaceInfo--><!--Device-MediaInfo-surfaceInfo: NativeMediaPlayerSurfaceInfo-End-->

**系统能力：** SystemCapability.Web.Webview.Core

