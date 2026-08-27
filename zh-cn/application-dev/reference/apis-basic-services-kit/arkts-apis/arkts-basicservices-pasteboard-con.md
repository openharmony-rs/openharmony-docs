# 常量

## MAX_RECORD_NUM

```TypeScript
const MAX_RECORD_NUM = 512
```

API version 10之前，此常量值为512，表示单个PasteData中所能包含的最大条目数为512。当剪贴板内容中添加的条目达到数量上限512后，后续的添加操作无效。从API version 10开始，不再限制单个PasteData中所能包含的最大条目数。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.MiscServices.Pasteboard

## MIMETYPE_PIXELMAP

```TypeScript
const MIMETYPE_PIXELMAP = 'pixelMap'
```

PixelMap内容的MIME类型定义。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.MiscServices.Pasteboard

## MIMETYPE_TEXT_HTML

```TypeScript
const MIMETYPE_TEXT_HTML = 'text/html'
```

HTML内容的MIME类型定义。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.MiscServices.Pasteboard

## MIMETYPE_TEXT_PLAIN

```TypeScript
const MIMETYPE_TEXT_PLAIN = 'text/plain'
```

纯文本内容的MIME类型定义。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.MiscServices.Pasteboard

## MIMETYPE_TEXT_URI

```TypeScript
const MIMETYPE_TEXT_URI = 'text/uri'
```

URI内容的MIME类型定义。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.MiscServices.Pasteboard

## MIMETYPE_TEXT_WANT

```TypeScript
const MIMETYPE_TEXT_WANT = 'text/want'
```

Want内容的MIME类型定义。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.MiscServices.Pasteboard
