# RenderResourceFactory

用于创建可在共享RenderContext的多个场景（[Scene](arkts-arkgraphics3d-scene-c.md)）中共享的渲染资源。

**起始版本：** 23

<!--Device-unnamed-export interface RenderResourceFactory--><!--Device-unnamed-export interface RenderResourceFactory-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## createImage

```TypeScript
createImage(params: SceneResourceParameters): Promise<Image>
```

根据指定场景资源参数创建一个图像资源，使用Promise异步回调。

**起始版本：** 23

<!--Device-RenderResourceFactory-createImage(params: SceneResourceParameters): Promise<Image>--><!--Device-RenderResourceFactory-createImage(params: SceneResourceParameters): Promise<Image>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [SceneResourceParameters](arkts-arkgraphics3d-scene-sceneresourceparameters-i.md) | 是 | 创建图像的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Image](arkts-arkgraphics3d-sceneresources-image-i.md)&gt; | Promise对象，返回创建的图像对象。 |

**示例**

```TypeScript
import { Image, SceneResourceParameters, Scene, RenderContext, RenderResourceFactory } from '@kit.ArkGraphics3D';

function createImageResource(): Promise<Image> {
  const renderContext: RenderContext | null = Scene.getDefaultRenderContext();
  if (!renderContext) {
    return Promise.reject(new Error("RenderContext is null"));
  }
  const renderResourceFactory: RenderResourceFactory = renderContext.getRenderResourceFactory();
  // 加载图片资源，路径和文件名可根据项目实际资源自定义
  let imageParams: SceneResourceParameters = {
    name: "sampleImage",
    uri: $rawfile("image/Cube_BaseColor.png")
  };
  return renderResourceFactory.createImage(imageParams);
}
```

## createImageStream

```TypeScript
createImageStream(params: SceneResourceParameters): Promise<ImageStream>
```

根据指定场景资源参数创建流图片，使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RenderResourceFactory-createImageStream(params: SceneResourceParameters): Promise<ImageStream>--><!--Device-RenderResourceFactory-createImageStream(params: SceneResourceParameters): Promise<ImageStream>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [SceneResourceParameters](arkts-arkgraphics3d-scene-sceneresourceparameters-i.md) | 是 | 创建流图片的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ImageStream](arkts-arkgraphics3d-sceneresources-imagestream-i.md)&gt; | Promise对象，返回创建的流图片。 |

**示例**

```TypeScript
import { ImageStream, SceneResourceParameters, Scene, RenderContext, RenderResourceFactory } from '@kit.ArkGraphics3D';

function createImageStreamResource(): Promise<ImageStream> {
  const renderContext: RenderContext | null = Scene.getDefaultRenderContext();
  if (!renderContext) {
    return Promise.reject(new Error("RenderContext is null"));
  }
  const renderResourceFactory: RenderResourceFactory = renderContext.getRenderResourceFactory();
  let imageStreamParams: SceneResourceParameters = {
    name: "sampleImageStream"
  };
  return renderResourceFactory.createImageStream(imageStreamParams);
}
```

## createMesh

```TypeScript
createMesh(params: SceneResourceParameters, geometry: GeometryDefinition): Promise<MeshResource>
```

根据指定场景资源参数和几何体定义（GeometryDefinition）创建一个网格资源（MeshResource），使用Promise异步回调。

**起始版本：** 23

<!--Device-RenderResourceFactory-createMesh(params: SceneResourceParameters, geometry: GeometryDefinition): Promise<MeshResource>--><!--Device-RenderResourceFactory-createMesh(params: SceneResourceParameters, geometry: GeometryDefinition): Promise<MeshResource>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [SceneResourceParameters](arkts-arkgraphics3d-scene-sceneresourceparameters-i.md) | 是 | 创建网格资源的参数。 |
| geometry | [GeometryDefinition](arkts-arkgraphics3d-scenetypes-geometrydefinition-c.md) | 是 | 几何形状定义，描述要创建的网格形状。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[MeshResource](arkts-arkgraphics3d-sceneresources-meshresource-i.md)&gt; | Promise对象，返回创建的网格资源对象。 |

**示例**

```TypeScript
import { SceneResourceParameters, Scene, CustomGeometry, PrimitiveTopology, RenderContext, RenderResourceFactory,
  MeshResource }  from '@kit.ArkGraphics3D';

function createMeshResource(): Promise<MeshResource> {
  const renderContext: RenderContext | null = Scene.getDefaultRenderContext();
  if (!renderContext) {
    return Promise.reject(new Error("RenderContext is null"));
  }
  const renderResourceFactory: RenderResourceFactory = renderContext.getRenderResourceFactory();
  const geometry = new CustomGeometry();
  geometry.vertices = [
    { x: 0, y: 0, z: 0 },
    { x: 1, y: 0, z: 0 },
    { x: 1, y: 1, z: 0 },
    { x: 0, y: 1, z: 0 },
    { x: 0, y: 0, z: 1 },
    { x: 1, y: 0, z: 1 },
    { x: 1, y: 1, z: 1 },
    { x: 0, y: 1, z: 1 }
  ];
  geometry.indices = [
    0, 1, 2, 2, 3, 0, // front
    4, 5, 6, 6, 7, 4, // back
    0, 4, 5, 5, 1, 0, // bottom
    1, 5, 6, 6, 2, 1, // right
    3, 2, 6, 6, 7, 3, // top
    3, 7, 4, 4, 0, 3  // left
  ];
  geometry.topology = PrimitiveTopology.TRIANGLE_LIST;
  geometry.normals = [
    { x: 0, y: 0, z: 1 },
    { x: 0, y: 0, z: 1 },
    { x: 0, y: 0, z: 1 },
    { x: 0, y: 0, z: 1 },
    { x: 0, y: 0, z: 1 },
    { x: 0, y: 0, z: 1 },
    { x: 0, y: 0, z: 1 },
    { x: 0, y: 0, z: 1 }
  ];
  geometry.uvs = [
    { x: 0, y: 0 },
    { x: 1, y: 0 },
    { x: 1, y: 1 },
    { x: 0, y: 1 },
    { x: 0, y: 0 },
    { x: 1, y: 0 },
    { x: 1, y: 1 },
    { x: 0, y: 1 }
  ];
  geometry.colors = [
    { r: 1, g: 0, b: 0, a: 1 },
    { r: 0, g: 1, b: 0, a: 1 },
    { r: 0, g: 0, b: 1, a: 1 },
    { r: 1, g: 1, b: 0, a: 1 },
    { r: 1, g: 0, b: 1, a: 1 },
    { r: 0, g: 1, b: 1, a: 1 },
    { r: 1, g: 1, b: 1, a: 1 },
    { r: 0, g: 0, b: 0, a: 1 }
  ];
  // 创建网格资源，路径和文件名可根据项目实际资源自定义
  let sceneResourceParameter: SceneResourceParameters = {
    name: "cubeMesh",
    uri: $rawfile("image/Cube_BaseColor.png")
  };
  return renderResourceFactory.createMesh(sceneResourceParameter, geometry);
}
```

## createSampler

```TypeScript
createSampler(params:SceneResourceParameters): Promise<Sampler>
```

根据指定场景资源参数创建一个采样器资源，使用Promise异步回调。

**起始版本：** 23

<!--Device-RenderResourceFactory-createSampler(params:SceneResourceParameters): Promise<Sampler>--><!--Device-RenderResourceFactory-createSampler(params:SceneResourceParameters): Promise<Sampler>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [SceneResourceParameters](arkts-arkgraphics3d-scene-sceneresourceparameters-i.md) | 是 | 创建采样器的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Sampler](arkts-arkgraphics3d-sceneresources-sampler-i.md)&gt; | Promise对象，返回创建的采样器对象。 |

**示例**

```TypeScript
import { SceneResourceParameters, Scene, RenderContext, RenderResourceFactory, Sampler } from '@kit.ArkGraphics3D';

function createSamplerResource(): Promise<Sampler> {
  const renderContext: RenderContext | null = Scene.getDefaultRenderContext();
  if (!renderContext) {
    return Promise.reject(new Error("RenderContext is null"));
  }
  const renderResourceFactory: RenderResourceFactory = renderContext.getRenderResourceFactory();
  // 创建采样器资源，路径和文件名可根据项目实际资源自定义
  let samplerParams: SceneResourceParameters = {
    name: "sampler1",
    uri: $rawfile("image/Cube_BaseColor.png")
  };
  return renderResourceFactory.createSampler(samplerParams);
}
```

## createScene

```TypeScript
createScene(uri?: ResourceStr): Promise<Scene>
```

从指定的资源URI创建一个新的场景。如果不指定URI，则创建一个空场景，使用Promise异步回调。

**起始版本：** 23

<!--Device-RenderResourceFactory-createScene(uri?: ResourceStr): Promise<Scene>--><!--Device-RenderResourceFactory-createScene(uri?: ResourceStr): Promise<Scene>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | ResourceStr | 否 | 创建场景使用的资源路径，如果未传入资源路径，则默认创建一个空场景。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Scene](arkts-arkgraphics3d-scene-c.md)&gt; | Promise对象，返回创建的场景对象。 |

**示例**

```TypeScript
import { Scene, RenderContext, RenderResourceFactory } from '@kit.ArkGraphics3D';

// fromFile=true：从指定glb文件加载场景，fromFile=false：创建一个空场景，此参数是为了示例展示两种常见场景创建方式
function createScenePromise(fromFile: boolean = false): Promise<Scene> {
  const renderContext: RenderContext | null = Scene.getDefaultRenderContext();
  if (!renderContext) {
    return Promise.reject(new Error("RenderContext is null"));
  }

  const renderResourceFactory: RenderResourceFactory = renderContext.getRenderResourceFactory();
  if (fromFile) {
    // 创建场景并加载.gltf或.glb文件作为初始内容，路径和名称可根据项目实际资源自定义
    return renderResourceFactory.createScene($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  } else {
    // 创建空场景
    return renderResourceFactory.createScene();
  }
}
```

## createShader

```TypeScript
createShader(params: SceneResourceParameters): Promise<Shader>
```

根据指定场景资源参数创建一个着色器，使用Promise异步回调。

**起始版本：** 23

<!--Device-RenderResourceFactory-createShader(params: SceneResourceParameters): Promise<Shader>--><!--Device-RenderResourceFactory-createShader(params: SceneResourceParameters): Promise<Shader>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [SceneResourceParameters](arkts-arkgraphics3d-scene-sceneresourceparameters-i.md) | 是 | 创建着色器的参数。详细.shader文件格式请参考.shader资源文件格式要求。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Shader](arkts-arkgraphics3d-sceneresources-shader-i.md)&gt; | Promise对象，返回创建的着色器对象。 |

**示例**

```TypeScript
import { Shader, SceneResourceParameters, Scene, RenderContext, RenderResourceFactory } from '@kit.ArkGraphics3D';

function createShaderResource(): Promise<Shader> {
  const renderContext: RenderContext | null = Scene.getDefaultRenderContext();
  if (!renderContext) {
    return Promise.reject(new Error("RenderContext is null"));
  }
  const renderResourceFactory: RenderResourceFactory = renderContext.getRenderResourceFactory();
  // 创建shader资源，路径和文件名可根据项目实际资源自定义
  let shaderParams: SceneResourceParameters = {
    name: "custom_shader",
    uri: $rawfile("shaders/custom_shader/custom_material_sample.shader")
  };
  return renderResourceFactory.createShader(shaderParams);
}
```

