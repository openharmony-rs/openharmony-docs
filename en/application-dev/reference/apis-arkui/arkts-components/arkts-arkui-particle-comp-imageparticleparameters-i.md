# ImageParticleParameters

```TypeScript
interface ImageParticleParameters
```

Defines the parameters for an image-like particle. @interface ImageParticleParameters

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## objectFit

```TypeScript
objectFit?: ImageFit
```

Image display mode.

**Type:** [ImageFit](../arkts-apis/arkts-arkui-imagefit-e.md)

**Default:** ImageFit.Cover

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size: ParticleTuple<Dimension, Dimension>
```

Particle image size.

**Type:** [ParticleTuple](arkts-arkui-particle-comp-particletuple-t.md)&lt;[Dimension](../arkts-apis/arkts-arkui-dimension-t.md), [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## src

```TypeScript
src: ResourceStr
```

Path to the image. Local and online sources are supported. For details about how to reference an image, see [Loading Image Resources](../../../ui/arkts-graphics-display.md#loading-image-resources).

SVG images are not supported.

If the value of src does not change, the cached resource is preferentially used. As a result, resources cannot be dynamically switched. If you want to dynamically switch resources, you are advised to switch to different src values.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
