# RadioConfiguration

开发者需要自定义class实现ContentModifier接口。继承自[CommonConfiguration](arkts-arkui-commonconfiguration-i.md)。

**继承/实现关系：** RadioConfiguration extends [CommonConfiguration<RadioConfiguration>]

**起始版本：** 12

<!--Device-unnamed-declare interface RadioConfiguration extends CommonConfiguration<RadioConfiguration>--><!--Device-unnamed-declare interface RadioConfiguration extends CommonConfiguration<RadioConfiguration>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## checked

```TypeScript
checked: boolean
```

设置单选框的选中状态。

默认值：false

值为true时，单选框被选中。值为false时，单选框不被选中。

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RadioConfiguration-checked: boolean--><!--Device-RadioConfiguration-checked: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## triggerChange

```TypeScript
triggerChange: Callback<boolean>
```

触发单选框选中状态变化。

值为true时，表示从未选中变为选中。值为false时，表示从选中变为未选中。

**类型：** Callback&lt;boolean&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RadioConfiguration-triggerChange: Callback<boolean>--><!--Device-RadioConfiguration-triggerChange: Callback<boolean>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: string
```

当前单选框的值。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RadioConfiguration-value: string--><!--Device-RadioConfiguration-value: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

