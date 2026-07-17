# MetallicRoughnessMaterial

基于物理的金属粗糙度材质资源.

**继承/实现关系：** MetallicRoughnessMaterial extends [Material](arkts-arkgraphics3d-sceneresources-material-i.md)

**起始版本：** 20

<!--Device-unnamed-export interface MetallicRoughnessMaterial extends Material--><!--Device-unnamed-export interface MetallicRoughnessMaterial extends Material-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## ambientOcclusion

```TypeScript
ambientOcclusion: MaterialProperty
```

PBR材质的环境光遮蔽.factor.x定义环境光遮蔽因子.

**类型：** MaterialProperty

**起始版本：** 20

<!--Device-MetallicRoughnessMaterial-ambientOcclusion: MaterialProperty--><!--Device-MetallicRoughnessMaterial-ambientOcclusion: MaterialProperty-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## baseColor

```TypeScript
baseColor: MaterialProperty
```

PBR材质的基础颜色因子.factor.xyzw的值定义rgba颜色.

**类型：** MaterialProperty

**起始版本：** 20

<!--Device-MetallicRoughnessMaterial-baseColor: MaterialProperty--><!--Device-MetallicRoughnessMaterial-baseColor: MaterialProperty-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## clearCoat

```TypeScript
clearCoat: MaterialProperty
```

清漆强度.factor.x定义清漆层强度.

**类型：** MaterialProperty

**起始版本：** 20

<!--Device-MetallicRoughnessMaterial-clearCoat: MaterialProperty--><!--Device-MetallicRoughnessMaterial-clearCoat: MaterialProperty-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## clearCoatNormal

```TypeScript
clearCoatNormal: MaterialProperty
```

清漆法线.factor.xyz定义RGB清漆法线缩放.

**类型：** MaterialProperty

**起始版本：** 20

<!--Device-MetallicRoughnessMaterial-clearCoatNormal: MaterialProperty--><!--Device-MetallicRoughnessMaterial-clearCoatNormal: MaterialProperty-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## clearCoatRoughness

```TypeScript
clearCoatRoughness: MaterialProperty
```

清漆粗糙度.factor.y定义清漆层粗糙度.

**类型：** MaterialProperty

**起始版本：** 20

<!--Device-MetallicRoughnessMaterial-clearCoatRoughness: MaterialProperty--><!--Device-MetallicRoughnessMaterial-clearCoatRoughness: MaterialProperty-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## emissive

```TypeScript
emissive: MaterialProperty
```

PBR材质的自发光属性.

**类型：** MaterialProperty

**起始版本：** 20

<!--Device-MetallicRoughnessMaterial-emissive: MaterialProperty--><!--Device-MetallicRoughnessMaterial-emissive: MaterialProperty-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## material

```TypeScript
material: MaterialProperty
```

金属粗糙度材质参数.factor.y定义粗糙度，factor.z定义金属度，factor.a定义反射率.

**类型：** MaterialProperty

**起始版本：** 20

<!--Device-MetallicRoughnessMaterial-material: MaterialProperty--><!--Device-MetallicRoughnessMaterial-material: MaterialProperty-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## normal

```TypeScript
normal: MaterialProperty
```

PBR材质的法线因子.factor.x的值定义法线缩放.

**类型：** MaterialProperty

**起始版本：** 20

<!--Device-MetallicRoughnessMaterial-normal: MaterialProperty--><!--Device-MetallicRoughnessMaterial-normal: MaterialProperty-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## sheen

```TypeScript
sheen: MaterialProperty
```

PBR材质的光泽颜色.Value of factor.xyz defines RGB sheen color,Value of factor.w defines sheen roughness.

**类型：** MaterialProperty

**起始版本：** 20

<!--Device-MetallicRoughnessMaterial-sheen: MaterialProperty--><!--Device-MetallicRoughnessMaterial-sheen: MaterialProperty-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## specular

```TypeScript
specular: MaterialProperty
```

PBR材质的镜面反射颜色.Value of factor.xyz defines RGB specular color,Value of factor.w defines specular intensity.

**类型：** MaterialProperty

**起始版本：** 20

<!--Device-MetallicRoughnessMaterial-specular: MaterialProperty--><!--Device-MetallicRoughnessMaterial-specular: MaterialProperty-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

