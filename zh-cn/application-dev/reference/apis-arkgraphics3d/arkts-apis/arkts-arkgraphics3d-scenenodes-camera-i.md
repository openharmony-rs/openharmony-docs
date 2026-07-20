# Camera

定义相机.

**继承/实现关系：** Camera extends [Node](arkts-arkgraphics3d-scenenodes-node-i.md)

**起始版本：** 12

<!--Device-unnamed-export interface Camera extends Node--><!--Device-unnamed-export interface Camera extends Node-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

<a id="getprojectionmatrix"></a>
## getProjectionMatrix

```TypeScript
getProjectionMatrix(): Mat4x4
```

获取相机的投影矩阵.

**起始版本：** 23

<!--Device-Camera-getProjectionMatrix(): Mat4x4--><!--Device-Camera-getProjectionMatrix(): Mat4x4-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Mat4x4](arkts-arkgraphics3d-scenetypes-mat4x4-i.md) | -- 相机的投影矩阵 |

<a id="getviewmatrix"></a>
## getViewMatrix

```TypeScript
getViewMatrix(): Mat4x4
```

获取相机的视图矩阵.

**起始版本：** 23

<!--Device-Camera-getViewMatrix(): Mat4x4--><!--Device-Camera-getViewMatrix(): Mat4x4-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Mat4x4](arkts-arkgraphics3d-scenetypes-mat4x4-i.md) | -- 相机的视图矩阵 |

<a id="raycast"></a>
## raycast

```TypeScript
raycast(viewPosition: Vec2, params: RaycastParameters): Promise<RaycastResult[]>
```

向屏幕上的位置投射射线并列出射线击中的对象.

**起始版本：** 20

<!--Device-Camera-raycast(viewPosition: Vec2, params: RaycastParameters): Promise<RaycastResult[]>--><!--Device-Camera-raycast(viewPosition: Vec2, params: RaycastParameters): Promise<RaycastResult[]>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| viewPosition | [Vec2](arkts-arkgraphics3d-scenetypes-vec2-i.md) | 是 | 在归一化设备坐标中投射的位置. |
| params | [RaycastParameters](arkts-arkgraphics3d-scene-raycastparameters-i.md) | 是 | 执行射线检测使用的选项. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;RaycastResult[]&gt; | - 返回命中结果数组的Promise，按从近到远排序. 数组可能为空. |

## clearColor

```TypeScript
clearColor: Color | null
```

背景清除颜色（环境背景会覆盖此颜色,需要BACKGROUND_NONE才能实际生效).

**类型：** Color \| null

**起始版本：** 12

<!--Device-Camera-clearColor: Color | null--><!--Device-Camera-clearColor: Color | null-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## effects

```TypeScript
readonly effects: Container<Effect>
```

应用于相机输出的特效.

**类型：** Container&lt;Effect&gt;

**起始版本：** 21

<!--Device-Camera-readonly effects: Container<Effect>--><!--Device-Camera-readonly effects: Container<Effect>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## enabled

```TypeScript
enabled: boolean
```

相机是否启用.

**类型：** boolean

**起始版本：** 12

<!--Device-Camera-enabled: boolean--><!--Device-Camera-enabled: boolean-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## farPlane

```TypeScript
farPlane: number
```

相机远平面, 单位为世界坐标系下的场景单位（例如cm、m、km等）.

**类型：** number

**起始版本：** 12

<!--Device-Camera-farPlane: double--><!--Device-Camera-farPlane: double-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## fov

```TypeScript
fov: number
```

相机视场, 单位为弧度.

**类型：** number

**起始版本：** 12

<!--Device-Camera-fov: double--><!--Device-Camera-fov: double-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## msaa

```TypeScript
msaa?: boolean
```

控制是否启用MSAA.

**类型：** boolean

**默认值：** false

**起始版本：** 22

<!--Device-Camera-msaa?: boolean--><!--Device-Camera-msaa?: boolean-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## nearPlane

```TypeScript
nearPlane: number
```

相机近平面, 单位为世界坐标系下的场景单位（例如cm、m、km等）.

**类型：** number

**起始版本：** 12

<!--Device-Camera-nearPlane: double--><!--Device-Camera-nearPlane: double-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## postProcess

```TypeScript
postProcess: PostProcessSettings | null
```

相机的后处理设置.

**类型：** PostProcessSettings \| null

**起始版本：** 12

<!--Device-Camera-postProcess: PostProcessSettings | null--><!--Device-Camera-postProcess: PostProcessSettings | null-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## renderingPipeline

```TypeScript
renderingPipeline?: RenderingPipelineType
```

控制渲染管线.请注意，如果选择了FORWARD_LIGHTWEIGHT管线，某些功能将不可用.

**类型：** RenderingPipelineType

**默认值：** RenderingPipelineType.FORWARD_LIGHTWEIGHT 前向轻量级渲染管线

**起始版本：** 21

<!--Device-Camera-renderingPipeline?: RenderingPipelineType--><!--Device-Camera-renderingPipeline?: RenderingPipelineType-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

