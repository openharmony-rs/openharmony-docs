# CheckBoxGroupConfiguration

开发者必须自定义此类以实现ContentModifier接口，使用方法见[contentModifier](CheckboxGroupAttribute#contentModifier)。

**继承/实现关系：** CheckBoxGroupConfiguration extends [CommonConfiguration<CheckBoxGroupConfiguration>](CommonConfiguration<CheckBoxGroupConfiguration>)

**起始版本：** 21

<!--Device-unnamed-declare interface CheckBoxGroupConfiguration extends CommonConfiguration<CheckBoxGroupConfiguration>--><!--Device-unnamed-declare interface CheckBoxGroupConfiguration extends CommonConfiguration<CheckBoxGroupConfiguration>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name: string
```

当前多选框群组名称。

**类型：** string

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-CheckBoxGroupConfiguration-name: string--><!--Device-CheckBoxGroupConfiguration-name: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## status

```TypeScript
status: SelectStatus
```

表示多选框群组的选中状态。

**类型：** SelectStatus

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-CheckBoxGroupConfiguration-status: SelectStatus--><!--Device-CheckBoxGroupConfiguration-status: SelectStatus-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## triggerChange

```TypeScript
triggerChange: Callback<boolean>
```

触发多选框群组选中状态变化。true表示从部分选中或未选中变为全部选中，false表示从全部选中或部分选中变为全部未选中。

**类型：** Callback&lt;boolean&gt;

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-CheckBoxGroupConfiguration-triggerChange: Callback<boolean>--><!--Device-CheckBoxGroupConfiguration-triggerChange: Callback<boolean>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

