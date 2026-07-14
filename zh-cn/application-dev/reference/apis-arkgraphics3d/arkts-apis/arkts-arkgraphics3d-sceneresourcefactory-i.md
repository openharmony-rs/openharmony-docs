# SceneResourceFactory

场景资源工厂.

**继承/实现关系：** SceneResourceFactory extends [RenderResourceFactory](arkts-arkgraphics3d-renderresourcefactory-i.md)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## createCamera

```TypeScript
createCamera(params: SceneNodeParameters): Promise<Camera>
```

Create a camera.

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | SceneNodeParameters | 是 | 创建相机的参数 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Camera&gt; | 返回创建的相机 |

## createCamera

```TypeScript
createCamera(params: SceneNodeParameters, cameraParams: CameraParameters): Promise<Camera>
```

Create a camera.

**起始版本：** 21

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | SceneNodeParameters | 是 | 创建相机的参数 |
| cameraParams | CameraParameters | 是 | 相机特定的额外参数 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Camera&gt; | 返回创建的相机 |

## createEffect

```TypeScript
createEffect(params: EffectParameters): Promise<Effect>
```

创建特效.

**起始版本：** 21

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | EffectParameters | 是 | 创建特效的参数. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Effect&gt; | 返回创建的特效. |

## createEnvironment

```TypeScript
createEnvironment(params: SceneResourceParameters): Promise<Environment>
```

Create an environment.

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | SceneResourceParameters | 是 | 创建环境对象的参数 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Environment&gt; | 返回创建的环境 |

## createGeometry

```TypeScript
createGeometry(params: SceneNodeParameters, mesh:MeshResource): Promise<Geometry>
```

创建几何节点.

**起始版本：** 18

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | SceneNodeParameters | 是 | 创建几何体的参数 |
| mesh | MeshResource | 是 | resource - 几何体的网格数据 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Geometry&gt; | 返回创建的几何体 |

## createLight

```TypeScript
createLight(params: SceneNodeParameters, lightType: LightType): Promise<Light>
```

Create a light.

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | SceneNodeParameters | 是 | the param of creating a light |
| lightType | LightType | 是 | 光源类型 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Light&gt; | 返回创建的光源 |

## createMaterial

```TypeScript
createMaterial(params: SceneResourceParameters, materialType: MaterialType): Promise<Material>
```

Create a material.

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | SceneResourceParameters | 是 | the param of creating a material |
| materialType | MaterialType | 是 | 材质类型 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Material&gt; | 返回创建的材质 |

## createNode

```TypeScript
createNode(params: SceneNodeParameters): Promise<Node>
```

Create a node.

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | SceneNodeParameters | 是 | 创建节点的参数 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Node&gt; | 返回创建的节点 |

