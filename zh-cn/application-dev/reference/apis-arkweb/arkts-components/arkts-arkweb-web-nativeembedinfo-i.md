# NativeEmbedInfo

提供同层标签的详细信息。

**起始版本：** 11

<!--Device-unnamed-declare interface NativeEmbedInfo--><!--Device-unnamed-declare interface NativeEmbedInfo-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## height

```TypeScript
height?: number
```

同层标签的高，单位为px。

**类型：** number

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NativeEmbedInfo-height?: number--><!--Device-NativeEmbedInfo-height?: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## id

```TypeScript
id?: string
```

同层标签的id信息。

**类型：** string

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NativeEmbedInfo-id?: string--><!--Device-NativeEmbedInfo-id?: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## params

```TypeScript
params?: Map<string, string>
```

object标签包含的param标签键值对列表，该map本质为Object类型，请使用Object提供的方法操作该对象，即`embed.info?.param?.["name"]`。

**类型：** Map<string, string>

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeEmbedInfo-params?: Map<string, string>--><!--Device-NativeEmbedInfo-params?: Map<string, string>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## position

```TypeScript
position?: Position
```

同层标签相对于Web组件左上角为坐标原点的位置信息，此处区别于标准Position，单位为px。

**类型：** Position

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeEmbedInfo-position?: Position--><!--Device-NativeEmbedInfo-position?: Position-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## src

```TypeScript
src?: string
```

同层标签的src信息。

**类型：** string

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NativeEmbedInfo-src?: string--><!--Device-NativeEmbedInfo-src?: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## tag

```TypeScript
tag?: string
```

标签名，统一为大写字符。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeEmbedInfo-tag?: string--><!--Device-NativeEmbedInfo-tag?: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## type

```TypeScript
type?: string
```

同层标签的type信息，统一为小写字符。

**类型：** string

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NativeEmbedInfo-type?: string--><!--Device-NativeEmbedInfo-type?: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## url

```TypeScript
url?: string
```

同层标签的url信息。

**类型：** string

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NativeEmbedInfo-url?: string--><!--Device-NativeEmbedInfo-url?: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## width

```TypeScript
width?: number
```

同层标签的宽，单位为px。

**类型：** number

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NativeEmbedInfo-width?: number--><!--Device-NativeEmbedInfo-width?: number-End-->

**系统能力：** SystemCapability.Web.Webview.Core

