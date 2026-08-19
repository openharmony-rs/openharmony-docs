# Light

光源，继承自Node。

**继承/实现关系：** Light extends [Node](arkts-arkgraphics3d-scenenodes-node-i.md)

**起始版本：** 23

<!--Device-unnamed-export interface Light--><!--Device-unnamed-export interface Light-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## color

```TypeScript
color: Color
```

颜色。

**类型：** [Color](arkts-arkgraphics3d-scenetypes-color-i.md)

**起始版本：** 23

<!--Device-Light-color: Color--><!--Device-Light-color: Color-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## enabled

```TypeScript
enabled: boolean
```

是否使能光源。true表示使用光源，false表示不使用。

**类型：** boolean

**起始版本：** 23

<!--Device-Light-enabled: boolean--><!--Device-Light-enabled: boolean-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## intensity

```TypeScript
intensity: double
```

光照强度，单位为坎德拉（cd），取值范围是大于0的实数。

**类型：** double

**起始版本：** 23

<!--Device-Light-intensity: double--><!--Device-Light-intensity: double-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## lightType

```TypeScript
readonly lightType: LightType
```

光源类型。

**类型：** [LightType](arkts-arkgraphics3d-scenenodes-lighttype-e.md)

**起始版本：** 23

<!--Device-Light-readonly lightType: LightType--><!--Device-Light-readonly lightType: LightType-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## shadowEnabled

```TypeScript
shadowEnabled: boolean
```

是否使能阴影。true表示添加阴影，false表示没有阴影效果。

**类型：** boolean

**起始版本：** 23

<!--Device-Light-shadowEnabled: boolean--><!--Device-Light-shadowEnabled: boolean-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

