# DrawableDescriptor

```TypeScript
export class DrawableDescriptor
```

父类对象提供可重写的方法，包含：获取[PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)实例，图片资源加载能力。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { DrawableDescriptor, LayeredDrawableDescriptor, PixelMapDrawableDescriptor, AnimationOptions, AnimatedDrawableDescriptor, AnimationController, DrawableDescriptorLoadedResult, AnimationStopMode, PictureDrawableDescriptor, HdrCompositionConfig } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor()
```

Creates a new DrawableDescriptor.

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## setSVGResourceLimitLevel

```TypeScript
setSVGResourceLimitLevel(limit: image.SVGResourceLimitLevel): void
```

设置svg资源限制级别。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| limit | [image.SVGResourceLimitLevel](../../apis-image-kit/arkts-apis/arkts-image-image-svgresourcelimitlevel-e-sys.md) | 是 | svg resource limit level. |
