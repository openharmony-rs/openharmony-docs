# PictureDrawableDescriptor

```TypeScript
export class PictureDrawableDescriptor extends DrawableDescriptor
```

支持通过传入Picture对象创建PictureDrawableDescriptor对象。继承自[DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptorloadedresult-i.md)。

**继承/实现关系：** PictureDrawableDescriptor extends [DrawableDescriptor](arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md)

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { DrawableDescriptor, LayeredDrawableDescriptor, PixelMapDrawableDescriptor, AnimationOptions, AnimatedDrawableDescriptor, AnimationController, DrawableDescriptorLoadedResult, AnimationStopMode, PictureDrawableDescriptor, HdrCompositionConfig } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(src: image.Picture)
```

PictureDrawableDescriptor的构造函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | [image.Picture](../../apis-image-kit/arkts-apis/arkts-image-image-picture-i.md) | 是 | 用于创建PictureDrawableDescriptor的Picture对象。 |

## setHdrComposition

```TypeScript
setHdrComposition(config: HdrCompositionConfig): void
```

设置HDR合成配置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [HdrCompositionConfig](arkts-arkui-arkui-drawabledescriptor-hdrcompositionconfig-i.md) | 是 | HDR合成配置。 |

**示例**
