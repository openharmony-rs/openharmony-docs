# DimensionNoPercentage

```TypeScript
declare type DimensionNoPercentage = PX | VP | FP | LPX | Resource
```

不支持百分比类型的长度联合类型。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型 | 说明 |
| --- | --- |
| PX | Length Length Length 长度类型，用于描述以px为单位的长度。 |
| VP | Length Length Length 长度类型，用于描述以vp为单位的长度。 |
| FP | Length Length Length 长度类型，用于描述以fp为单位的长度。 |
| LPX | Length Length Length 长度类型，用于描述以lpx为单位的长度。 |
| Resource | Resource Resource Resource 资源引用类型，用于设置组件属性的值。 |

