# CheckBoxConfiguration

开发者需要自定义class实现ContentModifier接口。继承自CommonConfiguration。

**继承/实现关系：** CheckBoxConfiguration extends CommonConfiguration<CheckBoxConfiguration>

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface CheckBoxConfiguration--><!--Device-unnamed-export declare interface CheckBoxConfiguration-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name: string
```

当前多选框名称。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CheckBoxConfiguration-name: string--><!--Device-CheckBoxConfiguration-name: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected: boolean
```

指示多选框是否被选中，值为true时，多选框被选中。值为false时，多选框未选中。 如果select属性没有设置默认值是false。 如果设置select属性，此值与设置select属性的值相同。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CheckBoxConfiguration-selected: boolean--><!--Device-CheckBoxConfiguration-selected: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## triggerChange

```TypeScript
triggerChange: Callback<boolean>
```

触发多选框选中状态变化。true表示从未选中变为选中，false表示从选中变为未选中。

**类型：** [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;boolean&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CheckBoxConfiguration-triggerChange: Callback<boolean>--><!--Device-CheckBoxConfiguration-triggerChange: Callback<boolean>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

