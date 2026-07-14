# EllipsisMode

省略号类型枚举。

EllipsisMode.START和EllipsisMode.MIDDLE仅在单行超长文本生效。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

## START

```TypeScript
START = 0
```

开头省略号，该枚举值只在[ParagraphStyle](arkts-arkgraphics2d-paragraphstyle-i.md)中设置maxLines为1时生效。

**起始版本：** 12

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

## MIDDLE

```TypeScript
MIDDLE = 1
```

中间省略号，该枚举值只在[ParagraphStyle](arkts-arkgraphics2d-paragraphstyle-i.md)中设置maxLines为1时生效。

**起始版本：** 12

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

## END

```TypeScript
END = 2
```

末尾省略号，该枚举值在[ParagraphStyle](arkts-arkgraphics2d-paragraphstyle-i.md)中maxLines设置为任何值时均有效。

**起始版本：** 12

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

## MULTILINE_START

```TypeScript
MULTILINE_START = 3
```

开头省略号，该枚举值在[ParagraphStyle](arkts-arkgraphics2d-paragraphstyle-i.md)中maxLines设置为任何值时均有效。

**起始版本：** 24

**元服务API：** 从API版本24开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

## MULTILINE_MIDDLE

```TypeScript
MULTILINE_MIDDLE = 4
```

中间省略号，该枚举值在[ParagraphStyle](arkts-arkgraphics2d-paragraphstyle-i.md)中maxLines设置为任何值时均有效。

**起始版本：** 24

**元服务API：** 从API版本24开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

