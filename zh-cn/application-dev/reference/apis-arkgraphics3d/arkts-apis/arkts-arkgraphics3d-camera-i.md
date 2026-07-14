# Camera

定义相机.

**继承/实现关系：** Camera extends [Node](arkts-arkgraphics3d-node-i.md)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## getProjectionMatrix

```TypeScript
getProjectionMatrix(): Mat4x4
```

获取相机的投影矩阵.

**起始版本：** 23

**系统能力：** SystemCapability.ArkUi.Graphics3D

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Mat4x4 | -- 相机的投影矩阵 |

## getViewMatrix

```TypeScript
getViewMatrix(): Mat4x4
```

获取相机的视图矩阵.

**起始版本：** 23

**系统能力：** SystemCapability.ArkUi.Graphics3D

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Mat4x4 | -- 相机的视图矩阵 |

## raycast

```TypeScript
raycast(viewPosition: Vec2, params: RaycastParameters): Promise<RaycastResult[]>
```

向屏幕上的位置投射射线并列出射线击中的对象.

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| viewPosition | Vec2 | 是 | 在归一化设备坐标中投射的位置. |
| params | RaycastParameters | 是 | 执行射线检测使用的选项. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;RaycastResult[]&gt; | - 返回命中结果数组的Promise，按从近到远排序. 数组可能为空. |

## clearColor

```TypeScript
clearColor: Color | null
```

背景清除颜色（环境背景会覆盖此颜色,
需要BACKGROUND_NONE才能实际生效).

**类型：** Color | null

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## effects

```TypeScript
readonly effects: Container<Effect>
```

应用于相机输出的特效.

**类型：** Container<Effect>

**起始版本：** 21

**系统能力：** SystemCapability.ArkUi.Graphics3D

## enabled

```TypeScript
enabled: boolean
```

相机是否启用.

**类型：** boolean

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## farPlane

```TypeScript
farPlane: number
```

相机远平面, 单位为世界坐标系下的场景单位（例如cm、m、km等）.

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## fov

```TypeScript
fov: number
```

相机视场, 单位为弧度.

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## msaa

```TypeScript
msaa?: boolean
```

控制是否启用MSAA.

**类型：** boolean

**默认值：** false

**起始版本：** 22

**系统能力：** SystemCapability.ArkUi.Graphics3D

## nearPlane

```TypeScript
nearPlane: number
```

相机近平面, 单位为世界坐标系下的场景单位（例如cm、m、km等）.

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## postProcess

```TypeScript
postProcess: PostProcessSettings | null
```

相机的后处理设置.

**类型：** PostProcessSettings | null

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## renderingPipeline

```TypeScript
renderingPipeline?: RenderingPipelineType
```

控制渲染管线.
请注意，如果选择了FORWARD_LIGHTWEIGHT管线，某些功能将不可用.

**类型：** RenderingPipelineType

**默认值：** RenderingPipelineType.FORWARD_LIGHTWEIGHT 前向轻量级渲染管线

**起始版本：** 21

**系统能力：** SystemCapability.ArkUi.Graphics3D

