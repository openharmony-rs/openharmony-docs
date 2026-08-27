# SVGResourceLimitLevel（系统接口）

SVG资源限制等级枚举。更高等级允许解析和绘制SVG图像时使用更少的资源。 无论指定哪种等级，系统默认的资源限制都会实施。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Multimedia.Image.Core

**系统接口：** 此接口为系统接口。

## NONE

```TypeScript
NONE = 0
```

使用系统默认的SVG资源限制。该等级不会关闭SVG资源保护。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**系统接口：** 此接口为系统接口。

## LOW

```TypeScript
LOW = 1
```

使用低等级限制，允许使用更多SVG资源预算。此等级适用于复杂的SVG图片。系统默认的资源限制仍然使用。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**系统接口：** 此接口为系统接口。

## MEDIUM

```TypeScript
MEDIUM = 2
```

使用中等级限制，允许使用适中的SVG资源预算。该等级平衡SVG兼容性和资源消耗，适用于大多数SVG图像。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**系统接口：** 此接口为系统接口。

## HIGH

```TypeScript
HIGH = 3
```

使用高等级限制，允许使用更少SVG资源预算。该等级适用于简单SVG图像，如图标和基础的UI资源。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**系统接口：** 此接口为系统接口。
