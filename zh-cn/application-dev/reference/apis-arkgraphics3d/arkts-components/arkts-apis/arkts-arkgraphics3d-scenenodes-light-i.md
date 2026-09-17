# Light

光源，继承自Node。

@extends Node @interface Light

**继承/实现关系：** Light extends [Node](arkts-arkgraphics3d-scenenodes-node-i.md)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## color

```TypeScript
color: Color
```

颜色。

**类型：** [Color](arkts-arkgraphics3d-scenetypes-color-i.md)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## enabled

```TypeScript
enabled: boolean
```

是否使能光源。true表示使用光源，false表示不使用。

**类型：** boolean

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## intensity

```TypeScript
intensity: number
```

光照强度，单位为坎德拉（cd），取值范围是大于0的实数。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## lightType

```TypeScript
readonly lightType: LightType
```

光源类型。

**类型：** [LightType](arkts-arkgraphics3d-scenenodes-lighttype-e.md)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## shadowEnabled

```TypeScript
shadowEnabled: boolean
```

是否使能阴影。true表示添加阴影，false表示没有阴影效果。

**类型：** boolean

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D
