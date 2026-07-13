# TextUndefinedGlyphDisplay

文本未定义字形时的显示方式枚举。

**起始版本：** 20

**系统能力：** SystemCapability.Graphics.Drawing

## USE_DEFAULT

```TypeScript
USE_DEFAULT = 0
```

使用字体的内部.notdef字形。遵循字体的内部.notdef字形设计，可以是空框、空格或自定义符号。

**起始版本：** 20

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

## USE_TOFU

```TypeScript
USE_TOFU = 1
```

总是用显式的豆腐块替换未定义的字形，覆盖字体的默认行为。用于调试缺失字符或强制一致的缺失符号显示。

**起始版本：** 20

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

