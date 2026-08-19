# 常量

## MAX_RECORD_NUM

```TypeScript
const MAX_RECORD_NUM: int
```

API version 10之前，此常量值为512，表示单个PasteData中所能包含的最大条目数为512。当剪贴板内容中添加的条目达到数量上限512后，后续的添加操作无效。 从API version 10开始，不再限制单个PasteData中所能包含的最大条目数。 单位: Numbers，该值必须是 [512, 512] 范围内的整数。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-pasteboard-const MAX_RECORD_NUM: int--><!--Device-pasteboard-const MAX_RECORD_NUM: int-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

## MIMETYPE_PIXELMAP

```TypeScript
const MIMETYPE_PIXELMAP: string
```

PixelMap内容的MIME类型，值为'pixelMap'。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-pasteboard-const MIMETYPE_PIXELMAP: string--><!--Device-pasteboard-const MIMETYPE_PIXELMAP: string-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

## MIMETYPE_TEXT_HTML

```TypeScript
const MIMETYPE_TEXT_HTML: string
```

HTML内容的MIME类型，值为'text/html'。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-pasteboard-const MIMETYPE_TEXT_HTML: string--><!--Device-pasteboard-const MIMETYPE_TEXT_HTML: string-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

## MIMETYPE_TEXT_PLAIN

```TypeScript
const MIMETYPE_TEXT_PLAIN: string
```

纯文本内容的MIME类型，值为'text/plain'。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-pasteboard-const MIMETYPE_TEXT_PLAIN: string--><!--Device-pasteboard-const MIMETYPE_TEXT_PLAIN: string-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

## MIMETYPE_TEXT_URI

```TypeScript
const MIMETYPE_TEXT_URI: string
```

URI内容的MIME类型，值为'text/uri'。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-pasteboard-const MIMETYPE_TEXT_URI: string--><!--Device-pasteboard-const MIMETYPE_TEXT_URI: string-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

## MIMETYPE_TEXT_WANT

```TypeScript
const MIMETYPE_TEXT_WANT: string
```

Want内容的MIME类型，值为'text/want'。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-pasteboard-const MIMETYPE_TEXT_WANT: string--><!--Device-pasteboard-const MIMETYPE_TEXT_WANT: string-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

