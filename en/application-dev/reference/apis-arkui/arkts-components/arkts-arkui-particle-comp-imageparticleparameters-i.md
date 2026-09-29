# ImageParticleParameters

```TypeScript
interface ImageParticleParameters
```

Sets the image options.

**Since:** 10

<!--Device-unnamed-interface ImageParticleParameters--><!--Device-unnamed-interface ImageParticleParameters-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## objectFit

```TypeScript
objectFit?: ImageFit
```

Image display mode.

Default value: **ImageFit.Cover**

**Type:** [ImageFit](../arkts-apis/arkts-arkui-imagefit-e.md)

**Default:** ImageFit.Cover

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ImageParticleParameters-objectFit?: ImageFit--><!--Device-ImageParticleParameters-objectFit?: ImageFit-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size: ParticleTuple<Dimension, Dimension>
```

Image size. The first parameter is the image width, and the second parameter is the image height.

Default value: [0, 0]

**Type:** [ParticleTuple](arkts-arkui-particle-comp-particletuple-t.md)&lt;[Dimension](../arkts-apis/arkts-arkui-dimension-t.md), [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ImageParticleParameters-size: ParticleTuple<Dimension, Dimension>--><!--Device-ImageParticleParameters-size: ParticleTuple<Dimension, Dimension>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## src

```TypeScript
src: ResourceStr
```

Image path. Both local images and network images are supported. For details about how to reference images, see [Loading Image Resources](../../../ui/arkts-graphics-display.md#loading-image-resources).

The SVG image type is not supported yet.

When src remains unchanged, cached resources are used preferentially, and resources cannot be switched dynamically. To switch resources dynamically, you are advised to switch to a different src.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ImageParticleParameters-src: ResourceStr--><!--Device-ImageParticleParameters-src: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
