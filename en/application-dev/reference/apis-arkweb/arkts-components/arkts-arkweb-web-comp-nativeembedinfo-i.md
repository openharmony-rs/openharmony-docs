# NativeEmbedInfo

```TypeScript
declare interface NativeEmbedInfo
```

Provides detailed information about the same-layer tag, including the ID, type, size, and location. It is suitable for scenarios where obtaining same-layer element attributes is required, improving same-layer rendering customization and user experience.

@interface NativeEmbedInfo [since 11 - 11]

**Since:** 11

**System capability:** SystemCapability.Web.Webview.Core

## height

```TypeScript
height?: number
```

Height of the same-layer tag, in px.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## id

```TypeScript
id?: string
```

ID of the same-layer tag.

**Type:** string

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## params

```TypeScript
params?: Map<string, string>
```

List of key-value pairs of the params tag in the object tag. Use the methods provided by Object to operate this object, for example, `embed.info?.params?.["name"]`.

**Type:** Map&lt;string, string&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## position

```TypeScript
position?: Position
```

Position of the same-layer tag relative to the upper left corner of the **Web** component as the coordinate origin, in pixels. This position is different from the standard position.

**Type:** Position

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## src

```TypeScript
src?: string
```

**src** information of the same-layer tag.

**Type:** string

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## tag

```TypeScript
tag?: string
```

Tag name, which is in uppercase.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## type

```TypeScript
type?: string
```

Type of the same-layer tag. The value is in lowercase.

**Type:** string

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## url

```TypeScript
url?: string
```

URL of the same-layer tag.

**Type:** string

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## width

```TypeScript
width?: number
```

Width of the same-layer tag, in px.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core
