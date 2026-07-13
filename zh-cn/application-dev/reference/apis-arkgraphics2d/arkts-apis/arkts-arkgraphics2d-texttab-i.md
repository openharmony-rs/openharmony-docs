# TextTab

段落风格的文本制表符，储存了对齐方式和位置。

**起始版本：** 18

**系统能力：** SystemCapability.Graphics.Drawing

## alignment

```TypeScript
alignment: TextAlign
```

段落中制表符之后的文本对齐方式，支持设置[TextAlign](arkts-arkgraphics2d-textalign-e.md)的LEFT左对齐、RIGHT右对齐和CENTER居中对齐方式，未列出的枚举值将视为左对齐，默认为左对齐。

**类型：** TextAlign

**起始版本：** 18

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

## location

```TypeScript
location: number
```

制表符之后的文本对齐位置，浮点数，单位为物理像素px，最小值为1.0，当该值小于1.0时，该制表符会被替换为一个空格。

**类型：** number

**起始版本：** 18

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

