# CheckBoxConfiguration

开发者需要自定义class实现ContentModifier接口。继承自[CommonConfiguration]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**继承/实现关系：** CheckBoxConfiguration extends [CommonConfiguration<CheckBoxConfiguration>](CommonConfiguration<CheckBoxConfiguration>)

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-unnamed-declare interface CheckBoxConfiguration extends CommonConfiguration<CheckBoxConfiguration>--><!--Device-unnamed-declare interface CheckBoxConfiguration extends CommonConfiguration<CheckBoxConfiguration>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name: string
```

当前多选框名称。

**类型：** string

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CheckBoxConfiguration-name: string--><!--Device-CheckBoxConfiguration-name: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected: boolean
```

指示多选框是否被选中，值为true时，多选框被选中。值为false时，多选框未选中。\_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_如果select属性没有设置默认值是false。\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_如果设置select属性，此值与设置select属性的值相同。

**类型：** boolean

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CheckBoxConfiguration-selected: boolean--><!--Device-CheckBoxConfiguration-selected: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## triggerChange

```TypeScript
triggerChange: Callback<boolean>
```

触发多选框选中状态变化的回调函数。调用时传入true，多选框被设置为选中状态；传入false，多选框被设置为未选中状态。

**类型：** Callback&lt;boolean&gt;

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CheckBoxConfiguration-triggerChange: Callback<boolean>--><!--Device-CheckBoxConfiguration-triggerChange: Callback<boolean>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

