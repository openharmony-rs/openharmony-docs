# AlertDialog

```TypeScript
declare class AlertDialog
```

**起始版本：** 7

**废弃版本：** 26.0.0

**替代接口：** [showAlertDialog](arkts-arkui-arkui-uicontext-uicontext-c.md#showalertdialog)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## show

```TypeScript
static show(value: AlertDialogParamWithConfirm | AlertDialogParamWithButtons | AlertDialogParamWithOptions)
```

定义警告弹窗并弹出。

> **说明：** 

showAlertDialog需先获取[UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)实例后再进行调用。

> 从API version 10开始，可以通过使用[UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)中的
> [showAlertDialog](arkts-arkui-arkui-uicontext-uicontext-c.md#showalertdialog)来明确UI的执行上下文。

**起始版本：** 7

**废弃版本：** 18

**替代接口：** [showAlertDialog](arkts-arkui-arkui-uicontext-uicontext-c.md#showalertdialog)

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [AlertDialogParamWithConfirm](arkts-arkui-alertdialogparamwithconfirm-i.md) &#124; [AlertDialogParamWithButtons](arkts-arkui-alertdialogparamwithbuttons-i.md) &#124; [AlertDialogParamWithOptions](arkts-arkui-alertdialogparamwithoptions-i.md) | 是 | 定义并显示AlertDialog组件。<br>**适用版本：** 10 |
