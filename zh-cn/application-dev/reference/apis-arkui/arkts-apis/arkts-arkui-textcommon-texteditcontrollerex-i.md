# TextEditControllerEx

文本扩展编辑控制器。 继承自[TextBaseController](arkts-arkui-textcommon-textbasecontroller-i.md)。

**继承/实现关系：** TextEditControllerEx extends [TextBaseController](arkts-arkui-textcommon-textbasecontroller-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface TextEditControllerEx--><!--Device-unnamed-export declare interface TextEditControllerEx-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getCaretOffset

```TypeScript
getCaretOffset(): int | undefined
```

返回当前光标所在位置。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextEditControllerEx-getCaretOffset(): int | undefined--><!--Device-TextEditControllerEx-getCaretOffset(): int | undefined-End-->

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 当前光标所在位置。 |

## getPreviewText

```TypeScript
getPreviewText(): PreviewText | undefined
```

获取预上屏信息。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextEditControllerEx-getPreviewText(): PreviewText | undefined--><!--Device-TextEditControllerEx-getPreviewText(): PreviewText | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PreviewText](arkts-arkui-textcommon-previewtext-i.md) | 预上屏信息。 |

## isEditing

```TypeScript
isEditing(): boolean | undefined
```

获取当前富文本的编辑状态。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextEditControllerEx-isEditing(): boolean | undefined--><!--Device-TextEditControllerEx-isEditing(): boolean | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true为编辑态，false为非编辑态。 |

## setCaretOffset

```TypeScript
setCaretOffset(offset: int): boolean | undefined
```

设置光标偏移位置。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextEditControllerEx-setCaretOffset(offset: int): boolean | undefined--><!--Device-TextEditControllerEx-setCaretOffset(offset: int): boolean | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | int | 是 | 光标偏移位置。超出所有内容范围时，设置失败。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 光标是否设置成功。<br/>true表示光标设置成功，false表示设置失败。 |

## stopEditing

```TypeScript
stopEditing(): void
```

退出编辑态。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextEditControllerEx-stopEditing(): void--><!--Device-TextEditControllerEx-stopEditing(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

