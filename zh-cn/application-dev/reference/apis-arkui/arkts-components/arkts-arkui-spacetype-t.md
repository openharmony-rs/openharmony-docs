# SpaceType

```TypeScript
declare type SpaceType = string | number | Resource
```

Column组件构造函数中space支持的数据类型，取值类型为下表类型中的并集。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-unnamed-declare type SpaceType = string | number | Resource--><!--Device-unnamed-declare type SpaceType = string | number | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型 | 说明 |
| --- | --- |
| string | 表示值类型为字符串，可取任意值。 |
| number | 表示类型为数字，可取任意值。 |
| Resource | 表示值为资源引用类型，取值为从系统资源或者应用资源中引入的数据值。 |

