# MaterialProperty

材质属性接口，用于定义材质所使用的纹理、属性因子及纹理采样器信息。@interface MaterialProperty

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D

## factor

```TypeScript
factor: Vec4
```

基于物理渲染（PBR）属性因子，不同属性不同含义。

**类型：** [Vec4](arkts-arkgraphics3d-scenetypes-vec4-i.md)

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D

## image

```TypeScript
image: Image | null
```

基于物理渲染（PBR）属性纹理贴图，用于表达材质的纹理信息。

**类型：** [Image](arkts-arkgraphics3d-sceneresources-image-i.md) \| null

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D

## sampler

```TypeScript
sampler?: Sampler
```

纹理贴图采样器，默认使用放大、缩小和mipmap过滤模式为线性过滤（LINEAR），纹理贴图U、V、W方向的寻址模式为重复（REPEAT）。

**类型：** [Sampler](arkts-arkgraphics3d-sceneresources-sampler-i.md)

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D
