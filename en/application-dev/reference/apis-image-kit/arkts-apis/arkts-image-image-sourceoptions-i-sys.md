# SourceOptions

```TypeScript
interface SourceOptions
```

Defines image source initialization options.

**Since:** 9

<!--Device-image-interface SourceOptions--><!--Device-image-interface SourceOptions-End-->

**System capability:** SystemCapability.Multimedia.Image.Core

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## svgResourceLimitLevel

```TypeScript
svgResourceLimitLevel?: SVGResourceLimitLevel
```

SVG resource limit level used when parsing and rendering an SVG image. The limit takes effect before SVG metadata is parsed. Therefore, it is also applied when image information is obtained. This property has no effect on non-SVG images. Default value: The default value is [NONE](arkts-image-image-svgresourcelimitlevel-e-sys.md#none), which uses the system-defined default resource limits and does not disable SVG resource protection.

**Type:** [SVGResourceLimitLevel](arkts-image-image-svgresourcelimitlevel-e-sys.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-SourceOptions-svgResourceLimitLevel?: SVGResourceLimitLevel--><!--Device-SourceOptions-svgResourceLimitLevel?: SVGResourceLimitLevel-End-->

**System capability:** SystemCapability.Multimedia.Image.Core

**System API:** This is a system API.
