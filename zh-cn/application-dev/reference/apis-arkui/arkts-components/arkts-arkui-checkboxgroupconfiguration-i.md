# CheckBoxGroupConfiguration

开发者必须自定义此类以实现ContentModifier接口，使用方法见[contentModifier](arkts-arkui-checkboxgroup-attribute.md#contentmodifier)。

**继承/实现关系：** CheckBoxGroupConfiguration extends CommonConfiguration<CheckBoxGroupConfiguration>

**起始版本：** 21

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## name

```TypeScript
name: string
```

当前多选框群组名称，用于标识和关联Checkbox与CheckboxGroup，与Checkbox的group属性值相同时属于同一群组。

**类型：** string

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## status

```TypeScript
status: SelectStatus
```

表示多选框群组的选中状态。

**类型：** [SelectStatus](arkts-arkui-selectstatus-e.md)

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

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

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
