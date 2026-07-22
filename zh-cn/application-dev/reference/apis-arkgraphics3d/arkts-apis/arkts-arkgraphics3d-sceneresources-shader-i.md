# Shader

着色器资源.

**继承/实现关系：** Shader extends [SceneResource](arkts-arkgraphics3d-sceneresources-sceneresource-i.md)

**起始版本：** 12

<!--Device-unnamed-export interface Shader extends SceneResource--><!--Device-unnamed-export interface Shader extends SceneResource-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## setShaderInputs

```TypeScript
setShaderInputs(inputs: Record<string, number | Vec2 | Vec3 | Vec4 | Image>): void
```

设置着色器输入。与属性版本功能相同，但性能更优。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Shader-setShaderInputs(inputs: Record<string, double | Vec2 | Vec3 | Vec4 | Image>): void--><!--Device-Shader-setShaderInputs(inputs: Record<string, double | Vec2 | Vec3 | Vec4 | Image>): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inputs | Record&lt;string, number \| Vec2 \| Vec3 \| Vec4 \| Image&gt; | 是 | 着色器的输入 |

## inputs

```TypeScript
readonly inputs: Record<string, number | Vec2 | Vec3 | Vec4 | Image>
```

着色器输入.

**类型：** Record&lt;string, number \| Vec2 \| Vec3 \| Vec4 \| Image&gt;

**起始版本：** 12

<!--Device-Shader-readonly inputs: Record<string, double | Vec2 | Vec3 | Vec4 | Image>--><!--Device-Shader-readonly inputs: Record<string, double | Vec2 | Vec3 | Vec4 | Image>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

