# RadioConfiguration

开发者需要自定义class实现ContentModifier接口。继承自CommonConfiguration。

**继承/实现关系：** RadioConfiguration extends CommonConfiguration<RadioConfiguration>

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface RadioConfiguration--><!--Device-unnamed-export declare interface RadioConfiguration-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## checked

```TypeScript
checked: boolean
```

设置单选框的选中状态。 默认值：false 值为true时，单选框被选中。值为false时，单选框不被选中。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RadioConfiguration-checked: boolean--><!--Device-RadioConfiguration-checked: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## triggerChange

```TypeScript
triggerChange: Callback<boolean>
```

触发单选框选中状态变化。 值为true时，表示从未选中变为选中。值为false时，表示从选中变为未选中。

**类型：** [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;boolean&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RadioConfiguration-triggerChange: Callback<boolean>--><!--Device-RadioConfiguration-triggerChange: Callback<boolean>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: string
```

当前单选框的值。 **卡片能力（仅ArkTS-Dyn）：** 从API version 9开始，该接口支持在ArkTS卡片中使用。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RadioConfiguration-value: string--><!--Device-RadioConfiguration-value: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

