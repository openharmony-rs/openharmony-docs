# RenderResourceFactory

渲染资源工厂，用于创建可在共享RenderContext的场景间共享的资源。

**起始版本：** 20

<!--Device-unnamed-export interface RenderResourceFactory--><!--Device-unnamed-export interface RenderResourceFactory-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## createImage

```TypeScript
createImage(params: SceneResourceParameters): Promise<Image>
```

创建图像.

**起始版本：** 20

<!--Device-RenderResourceFactory-createImage(params: SceneResourceParameters): Promise<Image>--><!--Device-RenderResourceFactory-createImage(params: SceneResourceParameters): Promise<Image>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [SceneResourceParameters](arkts-arkgraphics3d-scene-sceneresourceparameters-i.md) | 是 | 创建图像的参数 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Image> | 返回创建的图像 |

## createImageStream

```TypeScript
createImageStream(params: SceneResourceParameters): Promise<ImageStream>
```

创建图像流.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RenderResourceFactory-createImageStream(params: SceneResourceParameters): Promise<ImageStream>--><!--Device-RenderResourceFactory-createImageStream(params: SceneResourceParameters): Promise<ImageStream>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [SceneResourceParameters](arkts-arkgraphics3d-scene-sceneresourceparameters-i.md) | 是 | 创建图像流的参数 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ImageStream> | 返回创建的图像流 |

## createMesh

```TypeScript
createMesh(params: SceneResourceParameters, geometry: GeometryDefinition): Promise<MeshResource>
```

从顶点数组创建网格.

**起始版本：** 20

<!--Device-RenderResourceFactory-createMesh(params: SceneResourceParameters, geometry: GeometryDefinition): Promise<MeshResource>--><!--Device-RenderResourceFactory-createMesh(params: SceneResourceParameters, geometry: GeometryDefinition): Promise<MeshResource>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [SceneResourceParameters](arkts-arkgraphics3d-scene-sceneresourceparameters-i.md) | 是 | 创建网格对象的参数 |
| geometry | [GeometryDefinition](arkts-arkgraphics3d-scenetypes-geometrydefinition-c.md) | 是 | 要创建的几何形状类型 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<MeshResource> | 返回创建的网格 |

## createSampler

```TypeScript
createSampler(params:SceneResourceParameters): Promise<Sampler>
```

创建采样器.

**起始版本：** 20

<!--Device-RenderResourceFactory-createSampler(params:SceneResourceParameters): Promise<Sampler>--><!--Device-RenderResourceFactory-createSampler(params:SceneResourceParameters): Promise<Sampler>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [SceneResourceParameters](arkts-arkgraphics3d-scene-sceneresourceparameters-i.md) | 是 | 创建采样器的参数 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Sampler> | - 返回创建的采样器 |

## createScene

```TypeScript
createScene(uri?: ResourceStr): Promise<Scene>
```

从资源创建新场景.如果未提供uri，将返回空场景.

**起始版本：** 20

<!--Device-RenderResourceFactory-createScene(uri?: ResourceStr): Promise<Scene>--><!--Device-RenderResourceFactory-createScene(uri?: ResourceStr): Promise<Scene>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md) | 否 | 创建场景的资源 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Scene> | 返回创建的场景 |

## createShader

```TypeScript
createShader(params: SceneResourceParameters): Promise<Shader>
```

创建着色器.

**起始版本：** 20

<!--Device-RenderResourceFactory-createShader(params: SceneResourceParameters): Promise<Shader>--><!--Device-RenderResourceFactory-createShader(params: SceneResourceParameters): Promise<Shader>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [SceneResourceParameters](arkts-arkgraphics3d-scene-sceneresourceparameters-i.md) | 是 | 创建着色器的参数 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Shader> | 返回创建的着色器 |

