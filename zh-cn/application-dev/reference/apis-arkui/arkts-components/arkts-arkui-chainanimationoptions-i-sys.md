# ChainAnimationOptions（系统接口）

链式联动动效属性集合，用于设置List最大间距、最小间距、动效强度、传导系数和边缘效果。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## conductivity

```TypeScript
conductivity?: number
```

设置链式联动动效传导系数。取值范围[0,1]，数值越大，动效传导范围越远。

**类型：** number

**默认值：** 0.7

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## damping

```TypeScript
damping?: number
```

设置链式联动动效效果阻尼。<br/>取值范围[0, +∞)

**类型：** number

**默认值：** 30

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## edgeEffect

```TypeScript
edgeEffect?: ChainEdgeEffect
```

设置链式联动动效边缘效果。

**类型：** ChainEdgeEffect

**默认值：** ChainEdgeEffect.DEFAULT

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## intensity

```TypeScript
intensity?: number
```

设置链式联动动效效果强度。取值范围[0,1]，数值越大，动效效果越明显。

**类型：** number

**默认值：** 0.3

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## maxSpace

```TypeScript
maxSpace: Length
```

设置链式联动动效最大间距。<br/>单位：与Length一致。

**类型：** Length

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## minSpace

```TypeScript
minSpace: Length
```

设置链式联动动效最小间距。<br/>单位：与Length一致。

**类型：** Length

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## stiffness

```TypeScript
stiffness?: number
```

设置链式联动动效效果刚度。<br/>取值范围[0, +∞)

**类型：** number

**默认值：** 228

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

