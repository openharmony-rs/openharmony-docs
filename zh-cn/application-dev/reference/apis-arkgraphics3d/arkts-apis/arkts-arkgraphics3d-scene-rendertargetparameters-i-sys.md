# RenderTargetParameters（系统接口）

```TypeScript
export interface RenderTargetParameters extends SceneResourceParameters
```

渲染目标参数对象，继承自[SceneResourceParameters](arkts-arkgraphics3d-scene-sceneresourceparameters-i.md)，用于描述渲染目标。

**继承/实现关系：** RenderTargetParameters extends [SceneResourceParameters](arkts-arkgraphics3d-scene-sceneresourceparameters-i.md)

**起始版本：** 26.1.0

<!--Device-unnamed-export interface RenderTargetParameters extends SceneResourceParameters--><!--Device-unnamed-export interface RenderTargetParameters extends SceneResourceParameters-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

## size

```TypeScript
size: Vec2
```

渲染目标的尺寸，x表示宽度，y表示高度，单位为像素（px），取值必须大于0，当取值为浮点数时向下取整。

**类型：** [Vec2](arkts-arkgraphics3d-scenetypes-vec2-i.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RenderTargetParameters-size: Vec2--><!--Device-RenderTargetParameters-size: Vec2-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。
