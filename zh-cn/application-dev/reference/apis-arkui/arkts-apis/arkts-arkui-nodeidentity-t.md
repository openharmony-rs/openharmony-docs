# NodeIdentity

```TypeScript
export declare type NodeIdentity = string | number
```

定义节点标识类型。对于string类型，代表指定组件id，该id通过通用属性[id](../arkts-components/arkts-arkui-commonmethod-c.md#id-1)设置。对于number类型，
代表系统分配的唯一标识的节点UniqueID，可通过[getUniqueId](arkts-arkui-framenode-c.md#getuniqueid-1)获取。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型 | 说明 |
| --- | --- |
| string |  |
| number |  |

