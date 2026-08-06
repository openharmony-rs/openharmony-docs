# TargetInfo

指定组件绑定的目标节点。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface TargetInfo--><!--Device-unnamed-export interface TargetInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## componentId

```TypeScript
componentId?: int
```

目标节点所在的自定义组件的UniqueID。当上述id指定为string类型时，可通过此属性圈定范围。方便开发者在一定范围内保证id: string的唯一性。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TargetInfo-componentId?: int--><!--Device-TargetInfo-componentId?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## id

```TypeScript
id: string | int
```

指定popup或menu绑定的目标节点。 **说明：** 1. 当id是number时，对应组件实例的UniqueID，此id由系统保证唯一性。 2. 当id是string时，对应[通用属性id]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_所指定的组件，此id的唯一性需由开发者确保，但实际可能会有多个。

**类型：** string \| int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TargetInfo-id: string | int--><!--Device-TargetInfo-id: string | int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

