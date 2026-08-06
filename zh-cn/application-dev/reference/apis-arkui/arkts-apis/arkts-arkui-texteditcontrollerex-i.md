# TextEditControllerEx

文本扩展编辑控制器。 继承自[TextBaseController]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**继承/实现关系：** TextEditControllerEx extends [TextBaseController](arkts-arkui-component/textcommon-textbasecontroller-i.md)

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-unnamed-declare interface TextEditControllerEx extends TextBaseController--><!--Device-unnamed-declare interface TextEditControllerEx extends TextBaseController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getCaretOffset

```TypeScript
getCaretOffset(): number
```

返回当前光标所在位置。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextEditControllerEx-getCaretOffset(): number--><!--Device-TextEditControllerEx-getCaretOffset(): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 当前光标所在位置。 |

## getPreviewText

```TypeScript
getPreviewText?(): PreviewText
```

获取预上屏信息。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextEditControllerEx-getPreviewText?(): PreviewText--><!--Device-TextEditControllerEx-getPreviewText?(): PreviewText-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 预上屏信息，包含预上屏起始位置索引和预上屏文本内容。 |

## isEditing

```TypeScript
isEditing(): boolean
```

获取当前富文本的编辑状态。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextEditControllerEx-isEditing(): boolean--><!--Device-TextEditControllerEx-isEditing(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true为编辑态，false为非编辑态。 |

## setCaretOffset

```TypeScript
setCaretOffset(offset: number): boolean
```

设置光标偏移位置。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextEditControllerEx-setCaretOffset(offset: number): boolean--><!--Device-TextEditControllerEx-setCaretOffset(offset: number): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 是 | 光标偏移位置，取值范围[0, 文本长度]。超出所有内容范围时，设置失败。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 光标是否设置成功。 |

## stopEditing

```TypeScript
stopEditing(): void
```

退出编辑态。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextEditControllerEx-stopEditing(): void--><!--Device-TextEditControllerEx-stopEditing(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

