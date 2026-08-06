# graphics3d/SceneResources

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [Animation](sceneresources-animation-i.md) | 动画资源. |
| [Blend](sceneresources-blend-i.md) | 混合接口. |
| [Effect](sceneresources-effect-i.md) | 特效资源. |
| [Environment](sceneresources-environment-i.md) | 环境资源. |
| [Image](sceneresources-image-i.md) | 图像资源. |
| [ImageStream](sceneresources-imagestream-i.md) | 图像流资源. |
| [Material](sceneresources-material-i.md) | 材质资源. |
| [MaterialProperty](sceneresources-materialproperty-i.md) | 材质属性接口. |
| [Mesh](sceneresources-mesh-i.md) | 网格节点拥有的网格实例 |
| [MeshResource](sceneresources-meshresource-i.md) | 几何节点的网络数据描述资源 |
| [MetallicRoughnessMaterial](sceneresources-metallicroughnessmaterial-i.md) | 基于物理的金属粗糙度材质资源. |
| [Morpher](sceneresources-morpher-i.md) | 定义用于指定节点几何体形变目标的Morpher接口. |
| [OcclusionMaterial](sceneresources-occlusionmaterial-i.md) | 遮挡材质资源 |
| [RenderSort](sceneresources-rendersort-i.md) | 渲染排序层。在渲染槽中，层可以定义排序层顺序。 可用值为0-63（0最先，63最后）。默认id值为32。 典型用法：1. 将渲染排序层设置为对使用深度测试但未写入深度的对象进行渲染。 2. 始终首先渲染角色和/或相机对象以剔除大部分视图。 3. 对平面层进行排序。 |
| [Sampler](sceneresources-sampler-i.md) | 采样器接口 |
| [SceneResource](sceneresources-sceneresource-i.md) | 定义被其他3D资源扩展的场景资源. |
| [Shader](sceneresources-shader-i.md) | 着色器资源. |
| [ShaderMaterial](sceneresources-shadermaterial-i.md) | 着色器材质资源. |
| [SubMesh](sceneresources-submesh-i.md) | 子网格资源. |
| [UnlitMaterial](sceneresources-unlitmaterial-i.md) | 无光照材质资源 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [UnlitShadowAlphaMaterial](sceneresources-unlitshadowalphamaterial-i-sys.md) | 无光照阴影透明度材质资源 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CullMode](sceneresources-cullmode-e.md) | PBR材质剔除模式枚举. |
| [EnvironmentBackgroundType](sceneresources-environmentbackgroundtype-e.md) | 环境背景类型枚举. |
| [MaterialType](sceneresources-materialtype-e.md) | 材质类型枚举. |
| [PolygonMode](sceneresources-polygonmode-e.md) | 多边形模式枚举. |
| [SamplerAddressMode](sceneresources-sampleraddressmode-e.md) | 采样器的寻址模式 |
| [SamplerFilter](sceneresources-samplerfilter-e.md) | 采样器过滤模式 |
| [SceneResourceType](sceneresources-sceneresourcetype-e.md) | 场景资源类型枚举. |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [MaterialType](sceneresources-materialtype-e-sys.md) | 材质类型枚举. |
<!--DelEnd-->

