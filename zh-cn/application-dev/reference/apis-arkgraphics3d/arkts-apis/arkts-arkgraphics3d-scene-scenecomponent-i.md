# SceneComponent

表示基础场景组件，用于描述场景节点的组件信息，包括组件名称及其对应的属性集合。@interface SceneComponent

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D

## name

```TypeScript
name: string
```

要创建场景组件的名称，可由开发者自定义填写，用于标识场景组件。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D

## property

```TypeScript
readonly property: Record<string, string | number | Vec2 | Vec3 | Vec4 | SceneResource | boolean | number[] |
  string[] | SceneResource[] | Vec2[] | Vec3[] | Vec4[] | null | undefined>
```

组件的属性集合，以键值对形式存储。支持多种基础类型和复杂类型，用于描述场景组件的各种属性，单位及取值范围取决于具体场景组件。

**类型：** Record&lt;string, string \| number \| [Vec2](arkts-arkgraphics3d-scenetypes-vec2-i.md) \| [Vec3](arkts-arkgraphics3d-scenetypes-vec3-i.md) \| [Vec4](arkts-arkgraphics3d-scenetypes-vec4-i.md) \| [SceneResource](arkts-arkgraphics3d-sceneresources-sceneresource-i.md) \| boolean \| number[] \| string[] \| [SceneResource](arkts-arkgraphics3d-sceneresources-sceneresource-i.md)[] \| [Vec2](arkts-arkgraphics3d-scenetypes-vec2-i.md)[] \| [Vec3](arkts-arkgraphics3d-scenetypes-vec3-i.md)[] \| [Vec4](arkts-arkgraphics3d-scenetypes-vec4-i.md)[] \| null \| undefined&gt;

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D
