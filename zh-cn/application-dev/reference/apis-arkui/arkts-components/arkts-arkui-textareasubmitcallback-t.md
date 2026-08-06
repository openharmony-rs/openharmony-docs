# TextAreaSubmitCallback

```TypeScript
declare type TextAreaSubmitCallback = (enterKeyType: EnterKeyType, event?: SubmitEvent) => void
```

软键盘按下回车键时的回调事件。

**起始版本：** 14

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为14。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type TextAreaSubmitCallback = (enterKeyType: EnterKeyType, event?: SubmitEvent) => void--><!--Device-unnamed-declare type TextAreaSubmitCallback = (enterKeyType: EnterKeyType, event?: SubmitEvent) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enterKeyType | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 软键盘输入法回车键类型。 \_\_\_HTML\_TAG\_USD\_0\_\_\_类型为EnterKeyType.NEW\_LINE时不触发onSubmit。  |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 提交事件。用于获取提交事件的详细信息。不传入此参数时，无法获取提交事件的详细信息。  |

