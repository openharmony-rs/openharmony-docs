# MaterialProperty

材质属性接口.

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D

## factor

```TypeScript
factor: Vec4
```

纹理系数. 默认为{1,1,1,1}，表示无效果.

**类型：** Vec4

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D

## image

```TypeScript
image: Image | null
```

要使用的纹理. 如果未定义，factor定义漫反射颜色.

**类型：** Image | null

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D

## sampler

```TypeScript
sampler?: Sampler
```

纹理采样器.

**类型：** Sampler

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D

