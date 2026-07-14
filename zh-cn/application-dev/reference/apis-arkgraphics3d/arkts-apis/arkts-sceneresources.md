# SceneResources

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [Animation](arkts-arkgraphics3d-animation-i.md) | 动画资源. |
| [Blend](arkts-arkgraphics3d-blend-i.md) | 混合接口. |
| [Effect](arkts-arkgraphics3d-effect-i.md) | 特效资源. |
| [Environment](arkts-arkgraphics3d-environment-i.md) | 环境资源. |
| [Image](arkts-arkgraphics3d-image-i.md) | 图像资源. |
| [ImageStream](arkts-arkgraphics3d-imagestream-i.md) | 图像流资源. |
| [Material](arkts-arkgraphics3d-material-i.md) | 材质资源. |
| [MaterialProperty](arkts-arkgraphics3d-materialproperty-i.md) | 材质属性接口. |
| [Mesh](arkts-arkgraphics3d-mesh-i.md) | 网格节点拥有的网格实例 |
| [MeshResource](arkts-arkgraphics3d-meshresource-i.md) | 几何节点的网络数据描述资源 |
| [MetallicRoughnessMaterial](arkts-arkgraphics3d-metallicroughnessmaterial-i.md) | 基于物理的金属粗糙度材质资源. |
| [Morpher](arkts-arkgraphics3d-morpher-i.md) | 定义用于指定节点几何体形变目标的Morpher接口. |
| [OcclusionMaterial](arkts-arkgraphics3d-occlusionmaterial-i.md) | 遮挡材质资源 |
| [RenderSort](arkts-arkgraphics3d-rendersort-i.md) | 渲染排序层。在渲染槽中，层可以定义排序层顺序。可用值为0-63（0最先，63最后）。默认id值为32。典型用法：1. 将渲染排序层设置为对使用深度测试但未写入深度的对象进行渲染。2. 始终首先渲染角色和/或相机对象以剔除大部分视图。3. 对平面层进行排序。 |
| [Sampler](arkts-arkgraphics3d-sampler-i.md) | 采样器接口 |
| [SceneResource](arkts-arkgraphics3d-sceneresource-i.md) | 定义被其他3D资源扩展的场景资源. |
| [Shader](arkts-arkgraphics3d-shader-i.md) | 着色器资源. |
| [ShaderMaterial](arkts-arkgraphics3d-shadermaterial-i.md) | 着色器材质资源. |
| [SubMesh](arkts-arkgraphics3d-submesh-i.md) | 子网格资源. |
| [UnlitMaterial](arkts-arkgraphics3d-unlitmaterial-i.md) | 无光照材质资源 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [UnlitShadowAlphaMaterial](arkts-arkgraphics3d-unlitshadowalphamaterial-i-sys.md) | 无光照阴影透明度材质资源 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CullMode](arkts-arkgraphics3d-cullmode-e.md) | PBR材质剔除模式枚举. |
| [EnvironmentBackgroundType](arkts-arkgraphics3d-environmentbackgroundtype-e.md) | 环境背景类型枚举. |
| [MaterialType](arkts-arkgraphics3d-materialtype-e.md) | 材质类型枚举. |
| [PolygonMode](arkts-arkgraphics3d-polygonmode-e.md) | 多边形模式枚举. |
| [SamplerAddressMode](arkts-arkgraphics3d-sampleraddressmode-e.md) | 采样器的寻址模式 |
| [SamplerFilter](arkts-arkgraphics3d-samplerfilter-e.md) | 采样器过滤模式 |
| [SceneResourceType](arkts-arkgraphics3d-sceneresourcetype-e.md) | 场景资源类型枚举. |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [MaterialType](arkts-arkgraphics3d-materialtype-e-sys.md) | 材质类型枚举. |
<!--DelEnd-->

