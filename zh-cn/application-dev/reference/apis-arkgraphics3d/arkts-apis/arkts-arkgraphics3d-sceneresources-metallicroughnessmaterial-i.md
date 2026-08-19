# MetallicRoughnessMaterial

用于实现真实感外观的材质资源。 采用基于物理渲染（PBR）的金属-粗糙度模型，通过调节金属度和粗糙度参数，可模拟金属、塑料等不同材质的表面光照与反射效果，继承自Material。

**继承/实现关系：** MetallicRoughnessMaterial extends [Material](arkts-arkgraphics3d-sceneresources-material-i.md)

**起始版本：** 23

<!--Device-unnamed-export interface MetallicRoughnessMaterial--><!--Device-unnamed-export interface MetallicRoughnessMaterial-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## ambientOcclusion

```TypeScript
ambientOcclusion: MaterialProperty
```

环境光遮蔽贴图，用于模拟环境光在物体凹陷或细节部分的遮挡效果，增强局部阴影表现，提高细节真实感。

**类型：** [MaterialProperty](arkts-arkgraphics3d-sceneresources-materialproperty-i.md)

**起始版本：** 23

<!--Device-MetallicRoughnessMaterial-ambientOcclusion: MaterialProperty--><!--Device-MetallicRoughnessMaterial-ambientOcclusion: MaterialProperty-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## baseColor

```TypeScript
baseColor: MaterialProperty
```

基础颜色贴图，用于表达材质在没有光照情况下所表达的颜色信息。

**类型：** [MaterialProperty](arkts-arkgraphics3d-sceneresources-materialproperty-i.md)

**起始版本：** 23

<!--Device-MetallicRoughnessMaterial-baseColor: MaterialProperty--><!--Device-MetallicRoughnessMaterial-baseColor: MaterialProperty-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## clearCoat

```TypeScript
clearCoat: MaterialProperty
```

透明图层，用于在材质表面叠加一层具有反光特性的透明图层，可模拟车漆、碳纤、被水打湿的表面等材质的光泽表现。

**类型：** [MaterialProperty](arkts-arkgraphics3d-sceneresources-materialproperty-i.md)

**起始版本：** 23

<!--Device-MetallicRoughnessMaterial-clearCoat: MaterialProperty--><!--Device-MetallicRoughnessMaterial-clearCoat: MaterialProperty-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## clearCoatNormal

```TypeScript
clearCoatNormal: MaterialProperty
```

透明图层法线贴图。

**类型：** [MaterialProperty](arkts-arkgraphics3d-sceneresources-materialproperty-i.md)

**起始版本：** 23

<!--Device-MetallicRoughnessMaterial-clearCoatNormal: MaterialProperty--><!--Device-MetallicRoughnessMaterial-clearCoatNormal: MaterialProperty-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## clearCoatRoughness

```TypeScript
clearCoatRoughness: MaterialProperty
```

透明图层粗糙度。

**类型：** [MaterialProperty](arkts-arkgraphics3d-sceneresources-materialproperty-i.md)

**起始版本：** 23

<!--Device-MetallicRoughnessMaterial-clearCoatRoughness: MaterialProperty--><!--Device-MetallicRoughnessMaterial-clearCoatRoughness: MaterialProperty-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## emissive

```TypeScript
emissive: MaterialProperty
```

自发光颜色，表达材质自身作为光源向外发光的颜色信息。

**类型：** [MaterialProperty](arkts-arkgraphics3d-sceneresources-materialproperty-i.md)

**起始版本：** 23

<!--Device-MetallicRoughnessMaterial-emissive: MaterialProperty--><!--Device-MetallicRoughnessMaterial-emissive: MaterialProperty-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## material

```TypeScript
material: MaterialProperty
```

金属材质参数。 粗糙度（Roughness）：表达材质因其表面细微的结构细节所导致的反光强弱程度。 金属度（Metallic）：表达材质的金属属性。 反射度（Reflectance）：材质的光反射率。

**类型：** [MaterialProperty](arkts-arkgraphics3d-sceneresources-materialproperty-i.md)

**起始版本：** 23

<!--Device-MetallicRoughnessMaterial-material: MaterialProperty--><!--Device-MetallicRoughnessMaterial-material: MaterialProperty-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## normal

```TypeScript
normal: MaterialProperty
```

法线贴图，表达物体表面结构细节，使光照效果更真实，不改变几何结构。

**类型：** [MaterialProperty](arkts-arkgraphics3d-sceneresources-materialproperty-i.md)

**起始版本：** 23

<!--Device-MetallicRoughnessMaterial-normal: MaterialProperty--><!--Device-MetallicRoughnessMaterial-normal: MaterialProperty-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## sheen

```TypeScript
sheen: MaterialProperty
```

微纤维漫反射材质光泽，可用于表示布料和织物材料。

**类型：** [MaterialProperty](arkts-arkgraphics3d-sceneresources-materialproperty-i.md)

**起始版本：** 23

<!--Device-MetallicRoughnessMaterial-sheen: MaterialProperty--><!--Device-MetallicRoughnessMaterial-sheen: MaterialProperty-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## specular

```TypeScript
specular: MaterialProperty
```

非金属材质的高光反射，表示传统镜面反射强度。

**类型：** [MaterialProperty](arkts-arkgraphics3d-sceneresources-materialproperty-i.md)

**起始版本：** 23

<!--Device-MetallicRoughnessMaterial-specular: MaterialProperty--><!--Device-MetallicRoughnessMaterial-specular: MaterialProperty-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

