# CommandDataType（系统接口）

```TypeScript
type CommandDataType = number | string | boolean
```

表示私有数据命令中值的数据类型。接口参数具体类型根据其功能而定，key为命令名称（string类型），value为命令数据值（支持number、string或boolean类型）。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-inputMethodSystemPanelManager-type CommandDataType = int | string | boolean--><!--Device-inputMethodSystemPanelManager-type CommandDataType = int | string | boolean-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

| 类型 | 说明 |
| --- | --- |
| int | 数字类型，用于表示数值类命令数据，如开关状态码、配置参数值等。 |
| string | 字符串类型，用于表示文本类命令数据，如命令标识、文本内容、路径信息等。 |
| boolean | 布尔类型，用于表示开关类命令数据，如功能启用/禁用状态等。 |
