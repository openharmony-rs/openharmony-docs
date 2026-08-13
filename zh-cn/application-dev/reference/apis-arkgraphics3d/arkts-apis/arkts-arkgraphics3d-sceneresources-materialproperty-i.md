# MaterialProperty

材质属性接口.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface MaterialProperty--><!--Device-unnamed-export interface MaterialProperty-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## factor

```TypeScript
factor: Vec4
```

纹理系数. 默认为{1,1,1,1}，表示无效果.

**类型：** [Vec4](arkts-arkgraphics3d-scenetypes-vec4-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-MaterialProperty-factor: Vec4--><!--Device-MaterialProperty-factor: Vec4-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## image

```TypeScript
image: Image | null
```

要使用的纹理. 如果未定义，factor定义漫反射颜色.

**类型：** [Image](arkts-arkgraphics3d-sceneresources-image-i.md) \| null

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-MaterialProperty-image: Image | null--><!--Device-MaterialProperty-image: Image | null-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## sampler

```TypeScript
sampler?: Sampler
```

纹理贴图采样器，默认使用放大、缩小和mipmap过滤模式为线性过滤（LINEAR），纹理贴图U、V、W方向的寻址模式为重复（REPEAT）。

**类型：** [Sampler](arkts-arkgraphics3d-sceneresources-sampler-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-MaterialProperty-sampler?: Sampler--><!--Device-MaterialProperty-sampler?: Sampler-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

