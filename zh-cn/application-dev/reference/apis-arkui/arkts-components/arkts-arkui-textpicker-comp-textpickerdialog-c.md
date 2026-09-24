# TextPickerDialog

```TypeScript
declare class TextPickerDialog
```

根据指定的选择范围创建文本滑动选择器，展示在弹窗上。该组件适用于设置页面、表单录入、数据筛选等需要用户从预设选项中选择文本的场景。

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## show

```TypeScript
static show(options?: TextPickerDialogOptions)
```

定义文本滑动选择器弹窗并弹出。

> **说明：** 
> 
> 从API version 10开始，可以通过使用[UIContext](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md)中的
> [showTextPickerDialog](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#showtextpickerdialog)来明确UI的执行上下文。

**起始版本：** 8

**废弃版本：** 18

**替代接口：** [showTextPickerDialog](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#showtextpickerdialog)

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TextPickerDialogOptions](arkts-arkui-textpicker-comp-textpickerdialogoptions-i.md) | 否 | 配置文本选择器弹窗的参数，缺省时无法弹出弹窗。至少需要提供range参数才能正常弹出弹窗，其他参数均为可选配置。 |
