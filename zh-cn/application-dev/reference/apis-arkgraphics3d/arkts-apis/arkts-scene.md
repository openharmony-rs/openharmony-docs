# Scene

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [PCFConfig](arkts-arkgraphics3d-scene-pcfconfig-c.md) | PCF（Percentage Closer Filtering，百分比邻近过滤）软阴影配置类，继承自SoftShadowConfig。 |
| [Scene](arkts-arkgraphics3d-scene-c.md) | 用于设置场景。Scene采用树状层次结构组织场景节点，根节点（root）作为场景的入口。 |
| [SoftShadowConfig](arkts-arkgraphics3d-scene-softshadowconfig-c.md) | 软阴影配置抽象基类，用于控制阴影渲染的算法类型及其参数配置。 |

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Scene](arkts-arkgraphics3d-scene-c-sys.md) | 用于设置场景。Scene采用树状层次结构组织场景节点，根节点（root）作为场景的入口。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [CameraParameters](arkts-arkgraphics3d-scene-cameraparameters-i.md) | 相机创建参数配置，用于定义相机创建的额外选项。 |
| [EffectParameters](arkts-arkgraphics3d-scene-effectparameters-i.md) | 特效参数配置，用于指定创建特效时所需的特效ID，作为createEffect接口的入参来创建特效对象。 |
| [RaycastParameters](arkts-arkgraphics3d-scene-raycastparameters-i.md) | 射线检测参数配置，用于定义射线检测的行为。 |
| [RaycastResult](arkts-arkgraphics3d-scene-raycastresult-i.md) | 射线检测命中结果对象，包含被射线击中的3D物体详细信息。 |
| [RenderConfiguration](arkts-arkgraphics3d-scene-renderconfiguration-i.md) | 渲染配置接口。 |
| [RenderContext](arkts-arkgraphics3d-scene-rendercontext-i.md) | 定义了所有渲染资源的上下文。在同一渲染上下文中创建的多个场景之间，可以共享渲染资源。 |
| [RenderParameters](arkts-arkgraphics3d-scene-renderparameters-i.md) | 渲染参数接口。 |
| [RenderResourceFactory](arkts-arkgraphics3d-scene-renderresourcefactory-i.md) | 用于创建可在共享RenderContext的多个场景（[Scene](arkts-arkgraphics3d-scene-c.md)）中共享的渲染资源。 |
| [SceneComponent](arkts-arkgraphics3d-scene-scenecomponent-i.md) | 表示基础场景组件，用于描述场景节点的组件信息，包括组件名称及其对应的属性集合。 |
| [SceneNodeParameters](arkts-arkgraphics3d-scene-scenenodeparameters-i.md) | 场景节点参数对象，用于提供场景节点层次中的名称和路径。 |
| [SceneResourceFactory](arkts-arkgraphics3d-scene-sceneresourcefactory-i.md) | 用于创建3D场景中资源的接口，例如相机、光源等，继承自RenderResourceFactory。 |
| [SceneResourceParameters](arkts-arkgraphics3d-scene-sceneresourceparameters-i.md) | 场景资源参数对象，包含name和uri，用于提供场景资源的名称以及3D场景所需的资源文件路径。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [RenderResourceFactory](arkts-arkgraphics3d-scene-renderresourcefactory-i-sys.md) | 用于创建可在共享RenderContext的多个场景（[Scene](arkts-arkgraphics3d-scene-c.md)）中共享的渲染资源。 |
| [SceneLoadParams](arkts-arkgraphics3d-scene-sceneloadparams-i-sys.md) | 场景加载参数对象，用于指定加载3D模型资源时的额外配置选项。典型使用场景为从MP4容器文件中加载内嵌的glb模型。 |
<!--DelEnd-->

