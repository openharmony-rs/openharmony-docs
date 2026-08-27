# SpaceType

```TypeScript
declare type SpaceType = string | number | Resource
```

Column组件构造函数中space支持的数据类型，取值类型为下表类型中的并集。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型 | 说明 |
| --- | --- |
| string | 表示值类型为字符串，取值为可以转换为非负数字的字符串。取负数或不可转换的字符串时，按默认值0处理。 |
| number | 表示类型为数字，取值为大于等于0的数字。取负数或非法值时，按默认值0处理。 |
| Resource | 表示值为资源引用类型，取值为从系统资源或者应用资源中引入的数据值。 |
