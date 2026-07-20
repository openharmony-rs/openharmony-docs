# ImageParticleParameters

设置图片选项。

**起始版本：** 10

<!--Device-unnamed-interface ImageParticleParameters--><!--Device-unnamed-interface ImageParticleParameters-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## objectFit

```TypeScript
objectFit?: ImageFit
```

图片显示模式。

**类型：** ImageFit

**默认值：** ImageFit.Cover

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ImageParticleParameters-objectFit?: ImageFit--><!--Device-ImageParticleParameters-objectFit?: ImageFit-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size: ParticleTuple<Dimension, Dimension>
```

图像尺寸。

默认值：[0, 0]

**类型：** ParticleTuple&lt;Dimension, Dimension&gt;

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ImageParticleParameters-size: ParticleTuple<Dimension, Dimension>--><!--Device-ImageParticleParameters-size: ParticleTuple<Dimension, Dimension>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## src

```TypeScript
src: ResourceStr
```

图片路径，支持本地图片和网络图片，引用方式请参考[加载图片资源](docroot://ui/arkts-graphics-display.md#加载图片资源)。

暂不支持svg图片类型。

src未发生变化时，会优先使用缓存的资源，无法动态切换资源。如需动态切换资源建议切换为不同的src。

**类型：** ResourceStr

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ImageParticleParameters-src: ResourceStr--><!--Device-ImageParticleParameters-src: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

