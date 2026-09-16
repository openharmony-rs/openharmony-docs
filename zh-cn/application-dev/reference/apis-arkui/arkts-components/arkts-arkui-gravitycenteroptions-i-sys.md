# GravityCenterOptions（系统接口）

定义引力中心参数。

> **说明：** 
> 
> 此参数必须与[unionMode](arkts-arkui-unioneffectcontainer-comp-attribute.md#unionmode)一起使用，且unionMode须为UnionMode.GRAVITY_UNION，
> 同时useUnionEffect的value须为true时才生效，单独设置不生效。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## gravityCenter

```TypeScript
gravityCenter?: boolean
```

指定当前组件是否为引力中心。

设置为true表示当前组件是引力中心；设置为false表示当前组件不是引力中心。

默认值：false

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## gravityIntensity

```TypeScript
gravityIntensity?: number
```

定义引力中心处吸引力或排斥力的强度。

仅在gravityCenter为true时生效。

默认值：0

负数表示排斥力，正数表示吸引力。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
