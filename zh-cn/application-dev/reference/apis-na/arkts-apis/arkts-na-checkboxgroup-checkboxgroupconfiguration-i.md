# CheckBoxGroupConfiguration

CheckboxGroup的内容修饰器配置对象，用于配置CheckboxGroup的内容和样式。

**继承/实现关系：** CheckBoxGroupConfiguration extends CommonConfiguration<CheckBoxGroupConfiguration>

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface CheckBoxGroupConfiguration--><!--Device-unnamed-export declare interface CheckBoxGroupConfiguration-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## triggerChange

```TypeScript
triggerChange(isSelect: boolean): void
```

触发多选框群组选中状态变化。true表示从部分选中或未选中变为全部选中，false表示从全部选中或部分选中变为全部未选中。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CheckBoxGroupConfiguration-triggerChange(isSelect: boolean): void--><!--Device-CheckBoxGroupConfiguration-triggerChange(isSelect: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isSelect | boolean | 是 | Whether the checkbox group is selected. |

## name

```TypeScript
name: string
```

当前CheckboxGroup的群组名称。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CheckBoxGroupConfiguration-name: string--><!--Device-CheckBoxGroupConfiguration-name: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## status

```TypeScript
status: SelectStatus
```

CheckboxGroup的选中状态。

**类型：** [SelectStatus](arkts-na-checkboxgroup-selectstatus-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CheckBoxGroupConfiguration-status: SelectStatus--><!--Device-CheckBoxGroupConfiguration-status: SelectStatus-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

