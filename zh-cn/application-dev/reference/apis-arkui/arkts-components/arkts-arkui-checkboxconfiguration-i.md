# CheckBoxConfiguration

开发者需要自定义class实现ContentModifier接口。继承自[CommonConfiguration](arkts-arkui-commonconfiguration-i.md)。

**继承/实现关系：** CheckBoxConfiguration extends CommonConfiguration<CheckBoxConfiguration>

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## name

```TypeScript
name: string
```

当前多选框名称。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected: boolean
```

指示多选框是否被选中，值为true时，多选框被选中。值为false时，多选框未选中。&lt;/br&gt;如果select属性没有设置默认值是false。&lt;/br&gt;如果设置select属性，此值与设置select属性的值相同。

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## triggerChange

```TypeScript
triggerChange: Callback<boolean>
```

触发多选框选中状态变化的回调函数。调用时传入true，多选框被设置为选中状态；传入false，多选框被设置为未选中状态。

**类型：** Callback&lt;boolean&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
