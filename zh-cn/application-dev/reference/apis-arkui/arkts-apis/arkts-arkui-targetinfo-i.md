# TargetInfo

指定组件绑定的目标节点。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## componentId

```TypeScript
componentId?: number
```

目标节点所在的自定义组件的UniqueID。当上述id指定为string类型时，可通过此属性圈定范围。
方便开发者在一定范围内保证id: string的唯一性。

**类型：** number

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id: string | number
```

指定popup或menu绑定的目标节点。<br/>**说明：** <br/>
1. 当id是number时，对应组件实例的UniqueID，此id由系统保证唯一性。<br/>
2. 当id是string时，对应[通用属性id](arkts-arkui-commonmethod-c.md#id-1)所指定的组件
此id的唯一性需由开发者确保，但实际可能会有多个。

**类型：** string | number

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

