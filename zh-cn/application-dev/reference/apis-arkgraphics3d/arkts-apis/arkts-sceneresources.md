# SceneResources

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [Animation](arkts-arkgraphics3d-sceneresources-animation-i.md) | 动画类型，继承自SceneResource。 |
| [Blend](arkts-arkgraphics3d-sceneresources-blend-i.md) | 用于控制材质的透明效果。 |
| [Effect](arkts-arkgraphics3d-sceneresources-effect-i.md) | 特效类型，继承自SceneResource。由createEffect接口获得。 |
| [Environment](arkts-arkgraphics3d-sceneresources-environment-i.md) | 环境类型，继承自SceneResource。 |
| [Image](arkts-arkgraphics3d-sceneresources-image-i.md) | 图片类型，继承自SceneResource。 |
| [ImageStream](arkts-arkgraphics3d-sceneresources-imagestream-i.md) | 流图片类型，继承自Image。 |
| [Material](arkts-arkgraphics3d-sceneresources-material-i.md) | 材质类型，继承自SceneResource。 |
| [MaterialProperty](arkts-arkgraphics3d-sceneresources-materialproperty-i.md) | 材质属性接口，用于定义材质所使用的纹理、属性因子及纹理采样器信息。 |
| [Mesh](arkts-arkgraphics3d-sceneresources-mesh-i.md) | 网格类型，继承自SceneResource。 |
| [MeshResource](arkts-arkgraphics3d-sceneresources-meshresource-i.md) | 网格资源，继承自SceneResource。 |
| [MetallicRoughnessMaterial](arkts-arkgraphics3d-sceneresources-metallicroughnessmaterial-i.md) | 用于实现真实感外观的材质资源。 采用基于物理渲染（PBR）的金属-粗糙度模型，通过调节金属度和粗糙度参数，可模拟金属、塑料等不同材质的表面光照与反射效果，继承自Material。 |
| [Morpher](arkts-arkgraphics3d-sceneresources-morpher-i.md) | 用于控制3D模型的形变，通过调整不同形变目标的权重，实现模型的动态变形效果。 |
| [OcclusionMaterial](arkts-arkgraphics3d-sceneresources-occlusionmaterial-i.md) | 遮挡材质，能够遮挡场景中的其他物体但不会遮挡环境，继承自Material。 |
| [RenderSort](arkts-arkgraphics3d-sceneresources-rendersort-i.md) | 定义材质物体的渲染顺序，控制不同物体在渲染管线中的绘制先后。 |
| [Sampler](arkts-arkgraphics3d-sceneresources-sampler-i.md) | 采样器接口，用于定义纹理贴图采样时的过滤方式。 |
| [SceneResource](arkts-arkgraphics3d-sceneresources-sceneresource-i.md) | 用于表示场景中的资源。 |
| [Shader](arkts-arkgraphics3d-sceneresources-shader-i.md) | 着色器，继承自SceneResource。 |
| [ShaderMaterial](arkts-arkgraphics3d-sceneresources-shadermaterial-i.md) | 着色器材质，继承自Material。 |
| [SubMesh](arkts-arkgraphics3d-sceneresources-submesh-i.md) | 子网格类型。 |
| [UnlitMaterial](arkts-arkgraphics3d-sceneresources-unlitmaterial-i.md) | 不受光照影响的材质，其着色值只与设置的基础颜色有关，与光照条件无关，继承自Material。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [UnlitShadowAlphaMaterial](arkts-arkgraphics3d-sceneresources-unlitshadowalphamaterial-i-sys.md) | 此材质继承自Material，仅绘制材质表面阴影。材质启用Blend属性时，可与背景融合模拟透明效果。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CullMode](arkts-arkgraphics3d-sceneresources-cullmode-e.md) | 用于设置基于物理渲染（PBR）材质的剔除模式枚举。通过控制剔除物体的正面或背面几何面片，提升渲染性能和视觉效果。 |
| [EnvironmentBackgroundType](arkts-arkgraphics3d-sceneresources-environmentbackgroundtype-e.md) | 环境背景类型枚举，用于定义场景的背景呈现方式。 |
| [MaterialType](arkts-arkgraphics3d-sceneresources-materialtype-e.md) | 场景中物体材质类型枚举，定义材质的渲染方式。 |
| [PolygonMode](arkts-arkgraphics3d-sceneresources-polygonmode-e.md) | 控制多边形绘制模式的枚举。 |
| [SamplerAddressMode](arkts-arkgraphics3d-sceneresources-sampleraddressmode-e.md) | 采样器寻址模式枚举，用于控制纹理坐标超出[0, 1]范围时的处理方式。 |
| [SamplerFilter](arkts-arkgraphics3d-sceneresources-samplerfilter-e.md) | 采样器过滤模式枚举，定义纹理采样时的插值方法，用于控制纹理在缩放或变形时如何计算最终像素的颜色值。 |
| [SceneResourceType](arkts-arkgraphics3d-sceneresources-sceneresourcetype-e.md) | 场景资源类型枚举，对场景中的资源进行分类。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [MaterialType](arkts-arkgraphics3d-sceneresources-materialtype-e-sys.md) | 场景中物体材质类型枚举，定义材质的渲染方式。 |
<!--DelEnd-->

