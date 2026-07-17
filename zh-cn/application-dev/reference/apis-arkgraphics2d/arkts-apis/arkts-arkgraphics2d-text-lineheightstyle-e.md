# LineHeightStyle

行高缩放基数枚举。

**起始版本：** 21

<!--Device-text-enum LineHeightStyle--><!--Device-text-enum LineHeightStyle-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## FONT_SIZE

```TypeScript
FONT_SIZE = 0
```

以字号大小作为缩放基数。最终行高为[TextStyle](arkts-arkgraphics2d-text-textstyle-i.md).fontSize * [TextStyle](arkts-arkgraphics2d-text-textstyle-i.md).heightScale。

**起始版本：** 21

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-LineHeightStyle-FONT_SIZE = 0--><!--Device-LineHeightStyle-FONT_SIZE = 0-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## FONT_HEIGHT

```TypeScript
FONT_HEIGHT = 1
```

以字形高度作为缩放基数。最终行高为塑形后字形高度 * [TextStyle](arkts-arkgraphics2d-text-textstyle-i.md).heightScale。

**起始版本：** 21

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-LineHeightStyle-FONT_HEIGHT = 1--><!--Device-LineHeightStyle-FONT_HEIGHT = 1-End-->

**系统能力：** SystemCapability.Graphics.Drawing

