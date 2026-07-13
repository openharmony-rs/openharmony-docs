# LineHeightStyle

行高缩放基数枚举。

**起始版本：** 21

**系统能力：** SystemCapability.Graphics.Drawing

## FONT_SIZE

```TypeScript
FONT_SIZE = 0
```

以字号大小作为缩放基数。最终行高为[TextStyle](arkts-arkgraphics2d-textstyle-i.md).fontSize * [TextStyle](arkts-arkgraphics2d-textstyle-i.md).heightScale。

**起始版本：** 21

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

## FONT_HEIGHT

```TypeScript
FONT_HEIGHT = 1
```

以字形高度作为缩放基数。最终行高为塑形后字形高度 * [TextStyle](arkts-arkgraphics2d-textstyle-i.md).heightScale。

**起始版本：** 21

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

