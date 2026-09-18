# Sampler

采样器接口，用于定义纹理贴图采样时的过滤方式。

@interface { Sampler }

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D

## addressModeU

```TypeScript
addressModeU?: SamplerAddressMode
```

纹理贴图U方向（水平）的采样方式，默认值为REPEAT。

**类型：** [SamplerAddressMode](arkts-arkgraphics3d-sceneresources-sampleraddressmode-e.md)

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D

## addressModeV

```TypeScript
addressModeV?: SamplerAddressMode
```

纹理贴图V方向（垂直）的采样方式，默认值为REPEAT。

**类型：** [SamplerAddressMode](arkts-arkgraphics3d-sceneresources-sampleraddressmode-e.md)

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D

## magFilter

```TypeScript
magFilter?: SamplerFilter
```

放大过滤模式，控制纹理贴图被放大时的采样方式，默认值为LINEAR。

**类型：** [SamplerFilter](arkts-arkgraphics3d-sceneresources-samplerfilter-e.md)

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D

## minFilter

```TypeScript
minFilter?: SamplerFilter
```

缩小过滤模式，控制纹理贴图被缩小时的采样方式，默认值为LINEAR。

**类型：** [SamplerFilter](arkts-arkgraphics3d-sceneresources-samplerfilter-e.md)

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D

## mipMapMode

```TypeScript
mipMapMode?: SamplerFilter
```

mipmap过滤模式，控制纹理贴图在多层不同分辨率之间的采样方式，默认值为LINEAR。

**类型：** [SamplerFilter](arkts-arkgraphics3d-sceneresources-samplerfilter-e.md)

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D
