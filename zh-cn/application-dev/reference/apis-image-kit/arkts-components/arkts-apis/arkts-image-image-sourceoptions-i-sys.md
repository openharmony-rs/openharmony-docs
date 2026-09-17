# SourceOptions

ImageSource的初始化选项。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Image.Core

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## svgResourceLimitLevel

```TypeScript
svgResourceLimitLevel?: SVGResourceLimitLevel
```

SVG图像解析和绘制时使用的资源限制。该限制于SVG元数据解析前生效，因此也应用于图像信息获取。该限制对非SVG图像无效。默认值：默认值为[NONE](arkts-image-image-svgresourcelimitlevel-e-sys.md#none)，它使用系统定义的默认资源限制，不会禁用SVG资源保护。

**类型：** [SVGResourceLimitLevel](arkts-image-image-svgresourcelimitlevel-e-sys.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**系统接口：** 此接口为系统接口。
