# SceneResourceFactory

场景资源工厂.

**继承/实现关系：** SceneResourceFactory extends [RenderResourceFactory](arkts-arkgraphics3d-scene-renderresourcefactory-i.md)

**起始版本：** 12

<!--Device-unnamed-export interface SceneResourceFactory extends RenderResourceFactory--><!--Device-unnamed-export interface SceneResourceFactory extends RenderResourceFactory-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## createCamera

```TypeScript
createCamera(params: SceneNodeParameters): Promise<Camera>
```

Create a camera.

**起始版本：** 12

<!--Device-SceneResourceFactory-createCamera(params: SceneNodeParameters): Promise<Camera>--><!--Device-SceneResourceFactory-createCamera(params: SceneNodeParameters): Promise<Camera>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [SceneNodeParameters](arkts-arkgraphics3d-scene-scenenodeparameters-i.md) | 是 | 创建相机的参数 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Camera> | 返回创建的相机 |

## createCamera

```TypeScript
createCamera(params: SceneNodeParameters, cameraParams: CameraParameters): Promise<Camera>
```

Create a camera.

**起始版本：** 21

<!--Device-SceneResourceFactory-createCamera(params: SceneNodeParameters, cameraParams: CameraParameters): Promise<Camera>--><!--Device-SceneResourceFactory-createCamera(params: SceneNodeParameters, cameraParams: CameraParameters): Promise<Camera>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [SceneNodeParameters](arkts-arkgraphics3d-scene-scenenodeparameters-i.md) | 是 | 创建相机的参数 |
| cameraParams | [CameraParameters](arkts-arkgraphics3d-scene-cameraparameters-i.md) | 是 | 相机特定的额外参数 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Camera> | 返回创建的相机 |

## createEffect

```TypeScript
createEffect(params: EffectParameters): Promise<Effect>
```

创建特效.

**起始版本：** 21

<!--Device-SceneResourceFactory-createEffect(params: EffectParameters): Promise<Effect>--><!--Device-SceneResourceFactory-createEffect(params: EffectParameters): Promise<Effect>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [EffectParameters](arkts-arkgraphics3d-scene-effectparameters-i.md) | 是 | 创建特效的参数. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Effect> | 返回创建的特效. |

## createEnvironment

```TypeScript
createEnvironment(params: SceneResourceParameters): Promise<Environment>
```

Create an environment.

**起始版本：** 12

<!--Device-SceneResourceFactory-createEnvironment(params: SceneResourceParameters): Promise<Environment>--><!--Device-SceneResourceFactory-createEnvironment(params: SceneResourceParameters): Promise<Environment>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [SceneResourceParameters](arkts-arkgraphics3d-scene-sceneresourceparameters-i.md) | 是 | 创建环境对象的参数 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Environment> | 返回创建的环境 |

## createGeometry

```TypeScript
createGeometry(params: SceneNodeParameters, mesh:MeshResource): Promise<Geometry>
```

创建几何节点.

**起始版本：** 18

<!--Device-SceneResourceFactory-createGeometry(params: SceneNodeParameters, mesh:MeshResource): Promise<Geometry>--><!--Device-SceneResourceFactory-createGeometry(params: SceneNodeParameters, mesh:MeshResource): Promise<Geometry>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [SceneNodeParameters](arkts-arkgraphics3d-scene-scenenodeparameters-i.md) | 是 | 创建几何体的参数 |
| mesh | [MeshResource](arkts-arkgraphics3d-sceneresources-meshresource-i.md) | 是 | resource - 几何体的网格数据 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Geometry> | 返回创建的几何体 |

## createLight

```TypeScript
createLight(params: SceneNodeParameters, lightType: LightType): Promise<Light>
```

Create a light.

**起始版本：** 12

<!--Device-SceneResourceFactory-createLight(params: SceneNodeParameters, lightType: LightType): Promise<Light>--><!--Device-SceneResourceFactory-createLight(params: SceneNodeParameters, lightType: LightType): Promise<Light>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [SceneNodeParameters](arkts-arkgraphics3d-scene-scenenodeparameters-i.md) | 是 | the param of creating a light |
| lightType | [LightType](arkts-arkgraphics3d-scenenodes-lighttype-e.md) | 是 | 光源类型 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Light> | 返回创建的光源 |

## createMaterial

```TypeScript
createMaterial(params: SceneResourceParameters, materialType: MaterialType): Promise<Material>
```

Create a material.

**起始版本：** 12

<!--Device-SceneResourceFactory-createMaterial(params: SceneResourceParameters, materialType: MaterialType): Promise<Material>--><!--Device-SceneResourceFactory-createMaterial(params: SceneResourceParameters, materialType: MaterialType): Promise<Material>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [SceneResourceParameters](arkts-arkgraphics3d-scene-sceneresourceparameters-i.md) | 是 | the param of creating a material |
| materialType | [MaterialType](../../apis-arkui/arkts-apis/arkts-arkui-uimaterial-materialtype-e.md) | 是 | 材质类型 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Material> | 返回创建的材质 |

## createNode

```TypeScript
createNode(params: SceneNodeParameters): Promise<Node>
```

Create a node.

**起始版本：** 12

<!--Device-SceneResourceFactory-createNode(params: SceneNodeParameters): Promise<Node>--><!--Device-SceneResourceFactory-createNode(params: SceneNodeParameters): Promise<Node>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [SceneNodeParameters](arkts-arkgraphics3d-scene-scenenodeparameters-i.md) | 是 | 创建节点的参数 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Node> | 返回创建的节点 |

