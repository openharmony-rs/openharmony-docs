# EllipsisMode

省略号类型枚举。

EllipsisMode.START和EllipsisMode.MIDDLE仅在单行超长文本生效。

**起始版本：** 12

<!--Device-text-enum EllipsisMode--><!--Device-text-enum EllipsisMode-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## START

```TypeScript
START = 0
```

开头省略号，该枚举值只在[ParagraphStyle](arkts-arkgraphics2d-text-paragraphstyle-i.md)中设置maxLines为1时生效。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-EllipsisMode-START = 0--><!--Device-EllipsisMode-START = 0-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## MIDDLE

```TypeScript
MIDDLE = 1
```

中间省略号，该枚举值只在[ParagraphStyle](arkts-arkgraphics2d-text-paragraphstyle-i.md)中设置maxLines为1时生效。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-EllipsisMode-MIDDLE = 1--><!--Device-EllipsisMode-MIDDLE = 1-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## END

```TypeScript
END = 2
```

末尾省略号，该枚举值在[ParagraphStyle](arkts-arkgraphics2d-text-paragraphstyle-i.md)中maxLines设置为任何值时均有效。

**起始版本：** 12

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-EllipsisMode-END = 2--><!--Device-EllipsisMode-END = 2-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## MULTILINE_START

```TypeScript
MULTILINE_START = 3
```

开头省略号，该枚举值在[ParagraphStyle](arkts-arkgraphics2d-text-paragraphstyle-i.md)中maxLines设置为任何值时均有效。

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-EllipsisMode-MULTILINE_START = 3--><!--Device-EllipsisMode-MULTILINE_START = 3-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## MULTILINE_MIDDLE

```TypeScript
MULTILINE_MIDDLE = 4
```

中间省略号，该枚举值在[ParagraphStyle](arkts-arkgraphics2d-text-paragraphstyle-i.md)中maxLines设置为任何值时均有效。

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-EllipsisMode-MULTILINE_MIDDLE = 4--><!--Device-EllipsisMode-MULTILINE_MIDDLE = 4-End-->

**系统能力：** SystemCapability.Graphics.Drawing

